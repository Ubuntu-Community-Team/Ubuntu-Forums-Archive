---
title: "In a bit of a pickle"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2007-01-09
I have had problems with my computer recently e.g. applications just closing themselves and basically, it has just been unstable.

Just a moment ago, I was doing several things e.g. FTP manager was open, Browser was open and a few other things such as Email client etc..

I tried to load Quanta Web development studio and it was as if I was logged out of gnome, I was back at the login screen. I tried to log in and it was just blank, nothing at all.

Then I restarted and when I did, I got the following error message:

Busybox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
/bin/sh: can't access tty: job control turned off
(initramfs)

This is really worying and confusing, I have suspected hardware problems before this but cant put my finger on exactly what it is. I originally thought memory, but have dismissed that since they are crucial branded. I now suspect my PSU, does this sound familiar to anything anybody else has had?

Another problem which has been plaguing me for a while is that whenever I go to turn on my computer after some time of being off. It resets itself around 7 times before booting up properly, and the power supply emits a loud noise much like a fan being stressed.

If anybody is around on any of the popular means to offer real time support I would be greatful e.g. ICQ, Skype messenger, etc..

I am in a right pickle :-s

Appreciate the help, 
a very worried and disconcerted tom!

---

### Post by Shatrat on 2007-01-09
Well, to test your memory you can use memtest86 which should already be installed and have its own grub entry.  Even name brand memory can sometimes have problems, although usually if memory is working well when you get it it will continue working for the life of the PC.  The power supply does seem like it might be a problem.
Depending on your BIOS you might be able to see the actual voltages by going into the BIOS menu.  Make sure theyre all very close to spec, for example the +12 is at 11.98 and not 10.52 or something.  You could also try running a live CD and test driving a bunch of programs and seeing if that is stable, if so then it might be a problem with your installation and not hardware.

---

### Post by smoker on 2007-01-09
> Another problem which has been plaguing me for a while is that whenever I go to turn on my computer after some time of being off. It resets itself around 7 times before booting up properly, and the power supply emits a loud noise much like a fan being stressed.

definately sounds like your power supply is struggling, have you another handy you can maybe swap to try. failing that, what have you got in the way of power hungry hardware you can disconnect for a while to see if things improve, eg, cd drives, extra hard drives. if things improve, then go bad again when everything reconnected, then i think you are looking at a new power supply.

---

### Post by tommy1987 on 2007-01-09
Have now after several hours located and resolved the problem, which turned out to be a faulty module of RAM. It is replaced and there are now no errors from memtest86. 

Now to solve the problem stated above, the error im getting on trying to boot ubuntu. Is there any thoughts on how I can avoid a total reformat of the partition containing ubuntu?

It gives me the error on recovery mode also, and doesnt let me do anything at all!

---

