---
title: "[SOLVED] Need Help new Mobo - ubuntu wont install"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by daimaru on 2007-06-25
ok i just got a new motherboard (see sig) cause my old one broke. i never had problems using ubuntu with my old motherboard, but now i get weird errors. first i tried installing ubuntu to one of my sata hds (sata1) and everything worked (got to my desktop after install and everything) but as soon as i installed the updates (tried normal update manager and sudo apt-get upgrade) the errors start. the updates download, but when they are supposed to be installed i get errors like e:/var/chache or something - dpkg package corrupt. after that i get the message software index is broken try apt-get -f  , which does not resolve the problem. so all i can do is reinstall ubuntu. 
this was using i386 (live and alternate) version of ubuntu. im going to try amd64 next.

second installation i tried using my ide hardisk, cause i thought well maybe somethings not working with the sata one, but same result. i really have no idea what to do and i want my ubuntu back. sucks being stuck in windows. 

if anyone has had similar problems before please post. thx in advance.

---

### Post by analoog on 2007-06-25
you have an intel and you want to try the amd64 version?
that's not an good idea.

---

### Post by daimaru on 2007-06-25
core 2 duo is 64 bit right? the core duo is i386 so i thought that should work. ;)

---

### Post by Shazaam on 2007-06-25
Hmm. I went to the Abit forums and there seems to be a few people unhappy with that board. Here is the link; you might try searching there for your answer.

[http://forum.uabit.com/](http://forum.uabit.com/)

---

### Post by daimaru on 2007-06-25
well my problem seems to be resolved. installed 64bit version and everything works. it still is kind of weird because normally installing a 32bit version on a 64bit system worked fine for me, but somehow with this intel chip and the motherboard it didn't. 

steps i had to take to resolve it:
install amd64 version of ubuntu
login in recovery mode - install all updates
edit /boot/grub/menu.lst
delete the "splash" lines (cause it made my comp freeze right after grub menu)
reboot 
select new kernel and ---> all good

---

