---
title: "help with qemu pls"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by mad chey on 2007-03-20
Hi

i am currently running ubuntu dapper and have qemu installed so that i can use ventrillo, the installation of qemu went fine as did the installation of xp onto qemu, and then the subsequent installation of ventrillo

but now i would like to use qemu to run another windows only program, its the software that the Open University have sent me as part of my course, and no matter what ive tried i cannot get it to run in ubuntu

now my snag is that when in qemu-windows, if i try to open the cd drive it tells me to insert a disk into d:

well the disk is in the cd drive but it just doesnt see it

ive tried to google the solution but only get reference to installation of windows onto qemu

hoping someone can help

thanks

---

### Post by AtrejuT on 2007-03-20
well, not really an elegant solution, but maybe you could make an image of the cd in ubuntu which you subsequently mount in windows (isobuster or so)

atreju

---

### Post by mad chey on 2007-03-20
ok how would i do that, sorry im pretty dam newb at this

---

### Post by mad chey on 2007-03-22
you know what that is uber annoying

someone answers with a crap reply that dont help for XXXX and its no longer a zero reply post and therefore everyone else thinks ive had an answer

well i found the solution myself if anyone is reading this cos they also need to know

add

-cdrom /dev/cdrom

to the end of your qemu boot up command line.

ie:

qemu -hda c.img -m 256 -soundhw all -cdrom /dev/cdrom


oh and one other thing the cd you wanna run has to be in the drive ready before you boot it up, if you change the cd after the boot up it does that annoying windows donk noise and says its corrupt.

---

### Post by justleen on 2007-03-22
> **mad chey said:**
> you know what that is uber annoying

someone answers with a crap reply that dont help for XXXX and its no longer a zero reply post and therefore everyone else thinks ive had an answer

well i found the solution myself if anyone is reading this cos they also need to know

add

-cdrom /dev/cdrom

to the end of your qemu boot up command line.

ie:

qemu -hda c.img -m 256 -soundhw all -cdrom /dev/cdrom


oh and one other thing the cd you wanna run has to be in the drive ready before you boot it up, if you change the cd after the boot up it does that annoying windows donk noise and says its corrupt.


The enivitable RTFM attitude off the linux-community..

Glad to hear you've figured it out, sorry we didnt help (enough..).


"Give a man a fish, and feed him for a day. Teach a man to fish, and feed him for a lifetime"

---

### Post by mad chey on 2007-03-22
what does RTFM mean???


sorry if i sounded abrupt earlier just i was feeling very frustrated, oh and i do know that google is my friend but unfortunately google did not help at all with this one, a very nice programmer dude in southern uk that plays the same online game as me did

---

### Post by ridgeland on 2007-03-28
RTFM - - - Read The F***ing Manual
I wondered here trying to get some hints.
Guess I better spend some time with the manual.
Thanks for posting your answer.

---

