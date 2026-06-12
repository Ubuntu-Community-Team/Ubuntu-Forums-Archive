---
title: "2 computers"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by tomos on 2006-06-04
This is a big can of worms.                                                                                                                                                                                                                                        I have a laptop                                                                                                                                                                                        and a desktop, both macs and both with dapper.                                                                                                                                                               I want them to have the same software.                                      
I wonder how can I use synaptic                                                                                     just once and then do 2 installations.                                                                                                                                  For instance,                                                                                                                                                                                             I want the tex packages, tetex-base, bin and docs.
I    would   key:                                                                                                                                                                                              sudo apt-get tetex-base                                                                                                                                                                                                                                                                  
and then what?


TIA
tomos

---

### Post by aysiu on 2006-06-04
What are you asking exactly?

Do you want the two computers to be synced somehow so that if you install new software on one, it'll automatically be installed for the second computer as well?

Do you have a slow internet connection (dial-up) and not want to have to download the same package twice, so you want to reuse the .deb file on the other computer?

Do you have a list of packages you want installed but not have to mark each one individually in Synaptic all over again?

---

### Post by r3st on 2006-06-04
lol
someone found a use for macs
put linux on them

---

### Post by joshrobinson on 2006-06-04
[QUOTE=r3st]lol
someone found a use for macs
put linux on them[/QUOTE]

haha thats hitting below the belt for mac users :D

---

### Post by tomos on 2006-06-04
I do have a slow                                                                                                                                                     dial-up connection and                                                                                                                                                             I would like to avoid downloading the same package twice.
I would like to know what options I have.

Thanks
tomos

---

### Post by aysiu on 2006-06-04
You could create a [local repository](http://www.ubuntuforums.org/showthread.php?t=188158) on one computer and then use that to install the programs on the other computer.

---

### Post by NiceGuy on 2006-06-04
Or if you don't do much updating etc. You can find all your recently downloaded .debs in /var/cache/apt/archives - just get a pendrive (or whatever) copy them across and install them.

---

### Post by tomos on 2006-06-05
Thanks folks for the good ideas.  But my powerbook will not reboot - X server failed to start.  I have yet to resolve this, so now I only have one functioning Ubuntu computer.


tomos

---

