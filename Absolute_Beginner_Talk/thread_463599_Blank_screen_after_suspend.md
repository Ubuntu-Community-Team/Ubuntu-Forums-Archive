---
title: "Blank screen after suspend"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by cross157 on 2007-06-03
For starters: I'm running Feisty 7.04 on a HP pavilion zv5000 with an ATI mobility radeon 9000 card, which uses the "ati" open source driver because the fglxr driver doesn't support it. I'm also running Beryl, but this problem exists even if I switch back to gnome and close Beryl.

I have seen a number of posts on this subject and followed a number of suggestions without success.

I tried adding ec_intr=0 to /boot/grub/menu.lst like this tread suggested: [http://ubuntuforums.org/showthread.php?t=434718](http://ubuntuforums.org/showthread.php?t=434718)
I tried installing suspend2, but apparently you need to compile the kernel or something like that I just don't know what I'm doing enough to attempt that.
I tired µswsusp as suggeted here: [http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)
Lastly, I've tried many different configurations of the acpi-support file without finding a successful config.

Here's what happens: When I go to the log out screen and click suspend the screen briefly goes to the screensaver, then suspends as it should. The screen turns off and the fan stops spinning. When I hit the power button to resume, the hard drive spins up the fan starts spinning, but the screen stays off (not just black but actually off) No combination of keyboard buttons revives it. I have to force the power off by hold down the power button, then reboot in order to get the screen back. This also occurs when Power Management puts the computer to sleep after being idle.

I can post the results of any commands suggested, being a newbie I don't know what would help diagnose this problem. Thanks in advance

---

### Post by jonward0690 on 2007-06-04
Well I am sorry to have to tell you this but that is how hibernation and suspend kind of stand they eather work or they don't sometimes you can fix them and other times you can't.

---

### Post by Inxsible on 2007-06-04
My dv9000t suspends and hibernates correctly but does not resume...just like you. 

I shall try adding the ec_intr=0 thingy and try that. I have uswsusp installed already.

---

### Post by charles.g.moore on 2007-06-04
> **Inxsible said:**
> My dv9000t suspends and hibernates correctly but does not resume...just like you. 

I shall try adding the ec_intr=0 thingy and try that. I have uswsusp installed already.

Did you ever run 6.06?
I too have a dv9000t but am running 6.06, were you able to get the suspend/hibernate running correctly?

---

### Post by jvictor on 2007-06-04
I dont have an HP, but am a Toshiba user. I used to get stuff like this when my bios was old version.. I flashed the bios with the latest version and things cleared up instantly.. my two cents

---

### Post by pappapump on 2007-06-04
iggy this I fell asleep in the middle of typing.

---

### Post by cross157 on 2007-06-04
> **jvictor said:**
> I dont have an HP, but am a Toshiba user. I used to get stuff like this when my bios was old version.. I flashed the bios with the latest version and things cleared up instantly.. my two cents

My BIOS verison is the newest one HP offers. I'd be willing to switch to an open source BIOS, but how do I find the correct open BIOS for my hardware?

---

### Post by pospam on 2007-06-07
Hi all:
I hope someone can help and explain why this happens.
I have a hp zx5000 pavilion laptop with a Ati radeon 9600 video card.
After doing a clean install of feisty I was able to either use desktop effects
and also use beryl out of the box (without the restricted drivers turned on).
I was happy but then I tried to suspend and I could not. I read multiple post and it seems
that it is a common problem. The pc does suspend but then the screen stays off and I have to do a hard reboot (press power button for 5 seconds).

Then I decided to turn on the restricted ATI drivers and well, everything turned around.
I was able to suspend and this time the screen turned on, but I was not able to
either use desktop effects or use beryl.

Is there any way to have everything in working order at the same time?

Thanks for your help

P.

---

### Post by Sweet Mercury on 2007-06-09
> **pospam said:**
> Hi all:
I hope someone can help and explain why this happens.
I have a hp zx5000 pavilion laptop with a Ati radeon 9600 video card.
After doing a clean install of feisty I was able to either use desktop effects
and also use beryl out of the box (without the restricted drivers turned on).
I was happy but then I tried to suspend and I could not. I read multiple post and it seems
that it is a common problem. The pc does suspend but then the screen stays off and I have to do a hard reboot (press power button for 5 seconds).

Then I decided to turn on the restricted ATI drivers and well, everything turned around.
I was able to suspend and this time the screen turned on, but I was not able to
either use desktop effects or use beryl.

Is there any way to have everything in working order at the same time?

Thanks for your help

P.

How does one turn on the restricted ATI drivers? I don't use Beryl or Compiz effects, but I would like to be able to suspend my laptop.

---

