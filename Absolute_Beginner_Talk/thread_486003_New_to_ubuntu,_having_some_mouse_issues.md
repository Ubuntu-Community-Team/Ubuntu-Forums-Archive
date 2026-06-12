---
title: "New to ubuntu, having some mouse issues"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by kungfugecko on 2007-06-27
First of all I'd like to say howdy to the Ubuntu/Linux community!

This is my first venture into the land of Linux, and it's getting a touch rocky.

A few days ago I installed Ubuntu for the first time, and haven't had any problems with it since then.  Everything is working great on that machine.  Yesterday, I decided to throw it on another machine, which was running Windows 2000, to see how it would work with the slightly-more outdated hardware.  The install went perfect, however the PS/2 mouse doesn't seem to be working.  It loads up to the login screen, I can see the cursor in the middle, but it isn't moving at all, and I can't click either.  The mouse works fine, I just used it on a different computer to test it, and the PS/2 port on the computer works fine too.  I've google'd for a couple hours now, looking for a solution, and have tried several things but nothing worked.

I tried the solutions mentioned here [http://ubuntuforums.org/showthread.php?t=326225&highlight=bodzasfanta](http://ubuntuforums.org/showthread.php?t=326225&highlight=bodzasfanta)
to no avail.

I also tried someone's suggestion of

apt-get install mdetect
mdetect

which didn't do anything either.

If anyone has any suggestions on how to fix this problem, I would greatly appreciate it!

Thanks!

---

### Post by kungfugecko on 2007-06-27
I forgot to mention, the Ubuntu I installed was 7.04 for i386, if that helps.  Thanks!

---

### Post by nvteighen on 2007-06-27
> **kungfugecko said:**
> 
I also tried someone's suggestion of

apt-get install mdetect
mdetect


apt-get needs root permission, so the command should be:

```

sudo apt-get install mdetect
mdetect

```

---

### Post by kungfugecko on 2007-06-27
ok, after trying that, it appears to have downloaded mdetect.

I run it, and it doesnt show anything though.

I do this:

ben@ubuntu:~$ mdetect

and get this

ben@ubuntu:~$

(it just goes back to the command prompt)


Also, I just tried to run Ubuntu as a live CD, and the mouse didn't work then either.


One more question, After pressing ctrl+alt+f1 to get to the prompt from the login screen, how do I get back? I tried startx, and it says 

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock and start again

Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
giving up
xinit: unable to connect to X server
xinit: No such process (errno 3): Server error.
ben@ubuntu:~$

Any help would be appreciated!

---

### Post by reckless2k2 on 2007-06-27
is this a non-standard mouse? have you tried plugging in any other mouse? have you rebooted more than once to see if the problem continues to exist?

---

### Post by kungfugecko on 2007-06-27
@reckless2k2

I have tried 2 different mice, both are standard PS/2 mice (one optical / one ball) and neither are working.  I have also rebooted several times, and it still doesn't seem to want to work.  Any ideas for me?

---

### Post by kungfugecko on 2007-06-27
I've found a relevant post which may help this problem, hopefully someone can tell me what it means >_<

from [https://bugs.launchpad.net/baltix/+s...20/+bug/108221](https://bugs.launchpad.net/baltix/+s...20/+bug/108221)

"I have put a test kernel in [http://people.ubuntu.com/~pkl/ps2](http://people.ubuntu.com/~pkl/ps2). This kernel has a number of patches which may fix this problem. There is currently a kernel for i386, a x86_64 kernel will be available as soon as it builds.

Please test and let me know if this test kernel fixes the ps/2 mouse/keyboard problem.

If anyone needs to know, the package can be installed by sudo dpkg --install linux-image-2.6.20-16-generic_2.6.20-16.28_i386.deb and removed by sudo dpkg --purge linux-image-2.6.20-16-generic (for the i386 version).

Thanks"

another person says:

"This bug fix is now available as an official Ubuntu update.

Thanks to everyone who tried the test kernel, and reported their experiences. I'm marking this bug as fixed."


I tried the "sudo dpkg --install linux-image-2.6.20-16-generic_2.6.20-16.28_i386.deb" that he suggests, but it says the package cannot be found. There is a link to download it here [http://people.ubuntu.com/~pkl/ps2/](http://people.ubuntu.com/~pkl/ps2/)
however I don't have any idea how to download/install it from a command line in linux. If someone could post some advice I would appreciate it.

Thanks!

---

### Post by resander on 2007-07-11
I also had this problem about 4 weeks ago and I was using a brand new PS2 compatible mouse. I asked this forum and someone said there are some problems with the mouse driver and that those were being put to the developers at that time. Gave up at that point.

The PC is a Pentium III running at 700MHz with 256MB RAM.
It is a dual-boot with Windows XP and Ubuntu 7.04.

1.  The mouse works for Windows XP.

2.  I have also tried Linux Puppy and the mouse also works for that.

3.  Today I downloaded Ubuntu 6.06 KTS and the mouse worked.

I checked the Mouse from the Window XP Control Panel and the mouse was described as a 'PS2 compatible mouse'.

I think there is a SIS 'chip/chipset' on the motherboard, but have lost the motherboard manual so cannot say for sure.

I don't want to be left behind having to stay with Ubuntu 6.06, so would be grateful for instruction how to patch/fix this bug under 7.04

---

