---
title: "Evolution on xfce 4"
date: 2005-07-04
forum: Absolute Beginner Talk
---

### Post by Error_Msg on 2005-07-04
I used an old machine, but when I switched to xfce 4, performance improved exponentially. I learned this in this forum.
Evolution doesn't show in any of the menus, so I started it from the terminal.
It runs, but I get all these errors:
:~$ evolution
es menu class init
adding hook target 'source'
(evolution:6609): camel-WARNING **: Invalid root: '/home/jorge/.evolution/mail/l ocal/Drafts.ibex.index'
(evolution:6609): camel-WARNING **: version: TEXT.000 (TEXT.000)
(evolution:6609): camel-WARNING **: block size: 1024 (1024) OK
(evolution:6609): camel-WARNING **: free: 0 (0 add size < 1024) OK
(evolution:6609): camel-WARNING **: last: 6144 (6144 and size: 1024) BAD
(evolution:6609): camel-WARNING **: flags: unSYNC
update flow align
update flow align
update flow align
update flow align
update flow align

Normally I just keep on trucking, but the "BAD" warning at the end of line eight 
stirred my curiosity. What's going on here? And what's camel anyway--I quit smoking years ago!

E_M

---

### Post by nocturn on 2005-07-04
[QUOTE=Error_Msg]I used an old machine, but when I switched to xfce 4, performance improved exponentially. I learned this in this forum.
Evolution doesn't show in any of the menus, so I started it from the terminal.
It runs, but I get all these errors:
:~$ evolution
es menu class init
adding hook target 'source'
(evolution:6609): camel-WARNING **: Invalid root: '/home/jorge/.evolution/mail/l ocal/Drafts.ibex.index'
(evolution:6609): camel-WARNING **: version: TEXT.000 (TEXT.000)
(evolution:6609): camel-WARNING **: block size: 1024 (1024) OK
(evolution:6609): camel-WARNING **: free: 0 (0 add size < 1024) OK
(evolution:6609): camel-WARNING **: last: 6144 (6144 and size: 1024) BAD
(evolution:6609): camel-WARNING **: flags: unSYNC
update flow align
update flow align
update flow align
update flow align
update flow align

Normally I just keep on trucking, but the "BAD" warning at the end of line eight 
stirred my curiosity. What's going on here? And what's camel anyway--I quit smoking years ago!

E_M[/QUOTE]


I think one of your files is corrupt.  You can try to move it somewhere and start evo.
BTW, Evo should run find in XFCE (I have it on an old laptop).

---

