---
title: "No networking after kernel update......"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-05-29
hello.
ok the problem is i updated the kernel like alot of other people, and like alot of other people the system doesnt work properly, well not the whole system, just a bit of it.
for me its networking, by that i mean pc to pc networking, i had the home network set up perfectly, sharing files between my ubuntu system and the 2 other windows systems was fine no problems, i even found and installed a driver that will run the lexmark x1270 all in one printer thats installed on one of the windows pc's (was very pleased about the printer)
but now nothing :( i can still use the internet ok, we have a cable modem hooked up to a router and then 3 pc's connected to the router, but thats as far as it goes, if i go back to the previous kernel all is well, so im at a bit of  loss trying to figure out what the kernel update actually did to the networking setup.
all the stuff needed for networking is there, samba and such like, it just doesnt work, i have tried removing the lot of it and re-installing and basically starting from scratch but no dice im afraid.
so if anybody has any ideas i would appreciate the input.
cheers

it would seem that going into synaptic and removing the linux restricted modules for the previous kernel version has at least allowed me to see the other pc's on the network.
i had one file left in synaptic - linux-restricted-modules-2.6.20- 15-386 once i removed this one the pc's showed up on the network again (after rebooting)
im still having a small problem with access, eg - i cant create/delete file on the networked pc's, so i may need to set up the network again.
cheers to Borzo for the help.

---

