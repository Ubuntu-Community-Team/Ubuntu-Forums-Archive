---
title: "Toshiba A30 - ubuntu 7.4 boot problems"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by cloneofme on 2007-04-24
Right i just finished installing Ubuntu 7.4 onto my Toshiba A30 laptop, before i start ill give you the specs

P4 2.66
512 memory
32 meg integrated graphics

Now ive successfully installed the system from a live cd. but when it came to the reboot i encountered a problem, just before the login screen it seems to get stuck, what i mean by this is the screen goes from the os into the command prompt and then back again, so i assume that the problem is that something is conflicting with the kernel.

does anyone have any ideas on what i should do? 
if anyone need more info tell me what to get for you if it makes life easier.
thanks

* im a total linux noobie, so bear with me :D *

---

### Post by cloneofme on 2007-04-24
ill list the message im getting whilst pressing ctrl+alt+f1

'ata1.00:exception emask 0x0 sact 0x0 serr 0x0 action 0x0
 ata1:oo: (bmdma stat 0.25)
 ata1.00: smd c8/00:08:1f:70:50/00:00:00:000:000:/e0 tag sdb 0x0 data 4096 in

---

### Post by cloneofme on 2007-04-25
Ive noticed that a few other people are having problems with Toshiba's and the Ubuntu 7.04. but ive come up with a (time consuming ) resolution, if you install 6.06 then update from there it seems to get rid of the over heating and booting problems . 

Hope this helps , it worked for me.

---

