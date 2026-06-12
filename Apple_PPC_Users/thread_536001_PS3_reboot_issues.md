---
title: "PS3 reboot issues"
date: 2007-08-27
forum: Apple PPC Users
---

### Post by jasonfweb on 2007-08-27
ok, i'm not sure if this is the right place but i tought it wsa the better as the ps3 havea ppc architechture
when i try to reboot to switch to the game os( the shell command doesn't work, i have the custom kernel) it freezes when the screen goes black and the intermittent line appears. i can read in the phrases that appear before that taht the CPU somewhat didn't work and it shut down normally, but it don't shut down neither, it freezes... what can i do? sometimes it worked a few days ago, may i delete some files in the file system? even if i try to shut down it freezes when it say will now halt

my only solution for now is switch off the button on the back, but it's not good for the PS3, any help???s

---

### Post by ditsch on 2007-08-27
Which custom kernel do you mean? Your own? There is a known issue with the Ubuntu PS3 kernel not to shut down properly. Maybe this link can shed some light: [http://psubuntu.com/forum/viewtopic.php?t=471](http://psubuntu.com/forum/viewtopic.php?t=471)

---

### Post by jasonfweb on 2007-08-29
yeah, i have the psubuntu forum's custom kernel
i find there may be a solution: add a XMB (the ps3 os) boot command to boot the option (kboot.conf) so i can just type XMB in the kboot prompt
but to get to the kboot prompt doon't i need to reboot?( isn't it the first black screen where you press enter and it loads the kernel  and the other stuff? or can i get the kboot prompt by the shell?)
other problem: i'm a noobv and i don't know how  to do that can someone gently post the exact command? ps the shell command to boot to the ps3 is boot-game-os, but it doesn't work, i need to reboot and instad of pressingf enter at the begginning i type boot-game-os, but the problem is that i can'ty reboot!!!

---

