---
title: "Wierd problem preventing installation"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by FlamingGooch on 2007-10-19
Ok so I downloaded the Ubuntu 7.10 iso, burned it to a disk, and booted from it. After I click install it goes on all well and good. 

I get to this point where my screen flickers a lot and the installation just stops and I have to manually shut my computer down. I'm trying to run a dual boot Vista and 7.10 on a dell inspiron 9400 notebook. My graphics card is the ATI X1400.

EDIT: SOLVED: Thanks everyone for their input. I sued Norman's advice to get Ubuntu to install and it worked. I then had to use the server-agl driver on my X1400 ATI card to get compiz working. Thanks again!

---

### Post by norman_ on 2007-10-19
Sorry I can't add much to this, and please guys don't transform this into a "me too" thread that's 10 pages long, but over here: same card, same exact problem. So it's not isolated.

I'll come back if I find a solution.

---

### Post by jdong on 2007-10-19
As a workaround, have you guys tried the alternate CD install?

---

### Post by norman_ on 2007-10-19
Nope, haven't tried the alternate cd, but I'm currently writing from the live cd. I applied a similar technique to what I used to do in feisty with the black screen on install. 

So, I'm really not a Linux whiz, so my steps are probably very inaccurate, but anyhow, here they are. Also, the steps in this post didn't work for me but they might for you and they're shorter: [http://ubuntuforums.org/showthread.php?t=580327&highlight=something+bad+x1400](http://ubuntuforums.org/showthread.php?t=580327&highlight=something+bad+x1400)

Also, all these steps require active internet connection. My wifi card didn't work so I had to plug in.
After you get the "Something bad is happening" error message (they really have to do something about that by the way, sounds real unprofessional and is not informative at all) press ok


1- Alt+Ctrl+F1 to get to a console
2- Use vim or nano to edit your sources list and uncomment universe and multiverse repositories
sudo nano /etc/apt/sources.list
3- sudo apt-get update
4- sudo apt-get instal xorg-driver-fglrx
5- sudo aticonfig --initial

And select ati and then your prefered resolution.

That'll throw you back to console. Just type startx to log in the live cd

Remember, you only installed the driver in the live cd. If you install ubuntu, you'll need to redo the routine after you reboot in the new installation, or even the next time you boot the live cd.

Hope it works for you

Norman

EDIT: cleaned up instructions. I am having partitioning problems, but once that is solved i'll try to install it and i'll come back here

---

### Post by FlamingGooch on 2007-10-19
Thanks for the replies guys. Norman, I will try what you suggested tonight and let you know how it worked.

EDIT: Norman, I tried your solution but it didn't work. I can find no way to get to a terminal. I press ctrl+alt+f1 and my screen just still flickers. Also, the few times I managed to get a command prompt, this error message that I've been getting because of my broadcom wireless card just keeps appearing where im typing so I have to type the command again. Is there a way I can get a prompt without interruptions?

NEW EDIT: Ok, with your steps, Ubuntu is now installed on my computer! However, just as you had said, I need to put the drivers on my computer. This is not working for me. I typed the same commands edited the same lines and it doesnt work. It says it failed to find the files. Help?

---

### Post by norman_ on 2007-10-21
I'm really not sure. I have not been able to boot in the installed system. Bulletproofx seems to be locking me in and is not letting me get back to command prompt. Maybe an alternative would be to chroot in the target system while still in the live-cd right after the install, and then apply the configuration (install the driver and issue the aticonfig --initial). 

I bet that would work. Maybe i'll try later. 

Good luck

---

