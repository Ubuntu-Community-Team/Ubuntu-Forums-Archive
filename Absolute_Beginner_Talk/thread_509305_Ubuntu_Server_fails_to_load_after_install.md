---
title: "Ubuntu Server fails to load after install"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by pointyblue on 2007-07-25
I've just finished installing Ubuntu 7.04 Server edition. The Ubuntu server is the only OS on the machine.

Problem: When I start the computer Grub loads and tells me that it's starting the OS. Then the screen turns off and the computer is rebooted. This will continue until the end of time unless I hit the computer's off switch.

Do any of you know what causes this strange behaviour and how to fix it?

---

### Post by tcpip4lyfe on 2007-07-25
EDIT:  Scratch my idea. kvonb is the man.

---

### Post by kvonb on 2007-07-25
[FONT=monospace]You're using an older computer aren't you?

Have a read of my thread here, especially from post #3

[http://ubuntuforums.org/showthread.php?t=455884](http://ubuntuforums.org/showthread.php?t=455884)[/FONT]

---

### Post by pointyblue on 2007-07-27
You are right, it's an OLD computer. Only 150 mhz and 190 mb ram.

Tried your idea and it worked. I wanted to install Xubuntu by first installing the server and then sudo aptitude install xubuntu-desktop. At first it all appeared to be going as it should but the installation froze at 99% - guess it was just too much for the poor old thing.

Tried the alternate Xubuntu iso next and now the installation finishes but it doesn't recognize my mouse - hmmm! ](*,)

Anyway, thanks for helping me out with the kernel issue!

O:)

---

