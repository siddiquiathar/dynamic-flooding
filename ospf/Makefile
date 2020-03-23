
YANG_MODPATH=..

SRCS := ietf-dynamic-flooding-ospf@2019-09-01.yang
OBJS := $(SRCS:.yang=.tree)

all: $(OBJS)

reformat: $(SRCS)
	pyang -f yang --keep-comments --yang-line-length 69 $< >tmp.$$$$; \
	mv tmp.$$$$ $<

%.tree: %.yang
	pyang --lint --ietf --max-line-length=69 $<
	pyang --tree-line-length 69 -f tree $< >$@
	yanglint --verbose -p ../ietf -i $<

clean:
	rm -f $(OBJS)
