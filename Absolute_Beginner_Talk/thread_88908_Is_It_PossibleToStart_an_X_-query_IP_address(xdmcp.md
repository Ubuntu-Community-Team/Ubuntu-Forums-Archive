---
title: "Is It PossibleToStart an X -query IP address(xdmcp)in a window onto MySessionOfLinux?"
date: 2005-11-11
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-11-11
Is It PossibleToStart an X -query IP address(xdmcp)in a window onto MySessionOfLinux?

---

### Post by apjone on 2005-11-11
[QUOTE=patrick295767]Is It PossibleToStart an X -query IP address(xdmcp)in a window onto MySessionOfLinux?[/QUOTE]
ssh -X ip address
export DISPLAY=yourip:display#
xterm / or what ever you want to run

AJ

---

