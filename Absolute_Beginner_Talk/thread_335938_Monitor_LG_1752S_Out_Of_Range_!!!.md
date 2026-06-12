---
title: "Monitor LG 1752S Out Of Range !!!"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by widjaja31 on 2007-01-10
hai....
could someone help me ?
i use monitor LG 1752 S with ubuntu Edgy version. i found no problem when first installing. But when i try to boot for the first time, it's always said

"out of range
46.3 khz / 43 hz"

that message replaces ubuntu progression bar. I already try 
sudo dpkg-reconfigure xserver-xorg 
and set horizsync 30-85 and vertsync 40-70 but it still show that message.

is there anyone could help me solve my problem ?

Thanx A Lot !!:

---

### Post by Russty of Oz on 2007-01-11
When I have had that problem is was always that the resolutions was wrong.   I assume it is an LCD screen.  Do the reconfigure xserver thing again and when it gets to the resolution bit, use the down arrow to scroll down to whatever your screen can handle.  Mine is 1280X1024 then hit the space bar to select it then continue through.  I always let it use the horisync and vertsync that automatically shows up.

From what I have read before, this is a common problem with LCD monitors.

Russty

---

