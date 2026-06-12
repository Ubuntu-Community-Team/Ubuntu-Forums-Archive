---
title: "black screen of death"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by mykalreborn on 2006-08-26
well it's not really the microsoft counterpart as it doesn't say anything.
after installing ubuntu ,updating it and using it i had to restart the system to enter the xp. when ubuntu closed all the aplications just at the end i saw an error, but it was to short for me to read. the only thing i was able to read was nautilus, wich i think it's some kind of file manager, right?
then i restarted the system to check if it's okay and it worked. but this morning it loaded everything as it normaly does, but it stopped just before the welcome screen. everything else stopped:the keyboard the alt+ctrl+del command.
what to do?

---

### Post by Paul133 on 2006-08-26
What exactly has happened? Are you stuck at the command line or is the screen completely black?

---

### Post by mykalreborn on 2006-08-26
the screen is complelty black. there's nothing happening.
it's the second time this has happened to me.the last time i formated the hard disk.
if i start ubuntu in recovery mode, the terminal opens with the root user.and when i stop it i see a "[failed]" sign, but again it's way too fast and i can't see what that's about.

---

### Post by Paul133 on 2006-08-26
So, you can't just reboot the computer? It'll shut off as soon as you get into Ubuntu? Do you still have the grub menu? Do you have an alternate OS?

---

### Post by mykalreborn on 2006-08-26
i'm sorry, but i don't really know what a grub menu is.
the computer shuts off after loading all the devices and drivers and that stuff. right after the boot screen it turns black and it stays that way. i have the xp installed on my computer. and i would like to stop using it, but my father uses the computer too and for him even windows is too advanced :).

---

### Post by zappafrank on 2006-08-26
Your computer probably doesn't halt when this happens, try pressing alt+F1 and a text login should appear. 

I suspect you have this problem: [http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

There was a broken package which is fixed by now, so login to the text screen I mentioned earlier and do "sudo apt-get update" and after that "sudo apt-get upgrade" and reboot.

---

### Post by Dixie on 2006-08-26
Try reinstalling ubuntu again. it happened in a round about sort of way to me so i just reinstalled it. Hope this helps.

---

### Post by mykalreborn on 2006-08-26
> **zappafrank said:**
> Your computer probably doesn't halt when this happens, try pressing alt+F1 and a text login should appear. 

I suspect you have this problem: [http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

There was a broken package which is fixed by now, so login to the text screen I mentioned earlier and do "sudo apt-get update" and after that "sudo apt-get upgrade" and reboot.

i did that already. first i checked to see what verison i had, because i new that 10.3 had problems. i saw that i had 10.2, wich is quite weird given i had just updated ubuntu. still to be sure i typed the command to install 10.2, beacuse 10.4 wasn't in the repository. after doing that it gave me a message saying that it will downgrade the xserver-xorg-core. so it's really weird since i'm sure i saw it say that i already had 10.2 installed. anyhow...
the install finished, i rebooted the computer, and on closure of the programs, i could still see the "[failed]" message, but still could not see what failed, because it was so damn fast.
i started the normal ubuntu(not the recovery mode) and the same thing again.

there's gotta be something i can do without reinstalling ubuntu. i did that yesterday when the same thing apeared. and i'm pretty sure i downloaded the right version for my hardware.

what a predicament... :)

---

### Post by zappafrank on 2006-08-26
What kind of graphics card are you using? maybe using a different driver would help.

---

### Post by mykalreborn on 2006-08-26
i have an asus 9250 runing on an ati radeon platform (i think).

---

### Post by mikebeare on 2006-08-26
Just as a quick reply, since these problems with Ubuntu, I have got a similar problem. I manage to put in my password and userid, then after the initial windows loading the cursor freezes and that's it. I cannot do anything else. I have now reinstalled twice. I will not be applying the XSERVER updates this time!

---

### Post by confused57 on 2006-08-26
> **mykalreborn said:**
> i have an asus 9250 runing on an ati radeon platform (i think).

This may be a similar problem:

[http://www.ubuntuforums.org/showthread.php?t=244210](http://www.ubuntuforums.org/showthread.php?t=244210)

---

### Post by mykalreborn on 2006-08-26
i've started ubuntu in recovery mode yet again and tried this:[http://www.ubuntuforums.org/showthread.php?t=244210](http://www.ubuntuforums.org/showthread.php?t=244210), but it didn't fix anything. on reboot i was finally able to see what the "[failed]" sign was all about:the system periodic task manager. but i'm not absolutely sure.

---

### Post by kotti on 2006-08-28
I have the same (or similar?) problem. Here's a detailed description:

**Sometimes the screen goes black just before the login screen should come up.** The monitor then either stays black but with the monitor light green (as in it's getting a signal) or the monitor light goes yellow (as in it's not getting a signal). The former happens with Radeon 9600xt and the latter with my old Gefore4 420mx. The screen is just black, no mouse cursor or anything to be seen.

**Sometimes it boots fine for ten times in a row and then fails to do so another ten times in a row.** It doesn't seem to make any sense. This has been happening for weeks now so it can't be the recent Xserver bug.

**Ctrl+alt+backspace doesn't do anything, neither does ctrl+alt+f1, alt+f1 or any other combination**, the only thing I can do is to press reset and hope I'll get lucky next time.

**I've tried fresh installs for both Ubuntu (Gnome) and KUbuntu (KDE), it happens with both.** I've tried reinstalling the whole system a couple of times using both the live-cd and the alternative installer. No help.

**I've tried both Radeon 9600xt and Geforce4 420mx with both the default drivers and the proper 3d drivers** (using [this](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) guide for ATI and Automatix for NVIDIA). Happens in all combinations. **I've also tried setting the display driver to both vga and vesa** using [this](http://www.ubuntuforums.org/showthread.php?t=187177) guide. No help.

The monitor and both graphics cards work fine in Windows. I'm still pretty much a newbie when it comes to Linux so I'm pretty lost here. Any help would be appreciated.

---

### Post by kotti on 2006-08-28
Some more info about my case:

The screen has never gone black when I've tried using the live-cd (5 or 6 times) with the same screen resolution. It has never gone black the first time I've started the machine after a fresh install (which I've done 10 times or so already). I've always done a "apt-get update" and "apt-get upgrade" after the fresh install and sometimes it's failed on the next reboot.

- It can't be the graphics card as I've tried two and it happens with both.

- It can't be KDE or Gnome as it happens with both.

- It shouldn't be my monitor either as sometimes it works just fine.

I love Ubuntu but this is extremely annoying, I don't have the time or the energy to spend the first fifteen minutes every time I start the computer just trying to get to the login screen.

---

### Post by mykalreborn on 2006-08-28
i've downloaded mandriva linux from the internet, in the hope that this works. i thought it could some kind of ubuntu compatibity problem. but it seems that i have the same problem with mandriva. so i started to search the web for detailed information about my hardware, and i've checked and double checked and came to the conclusion that it's the compatible. 
it's frustating, because nobody seems to be able to help me and because i just want to get that darn linux running.

---

### Post by confused57 on 2006-08-28
> **kotti said:**
> Some more info about my case:

The screen has never gone black when I've tried using the live-cd (5 or 6 times) with the same screen resolution. It has never gone black the first time I've started the machine after a fresh install (which I've done 10 times or so already). I've always done a "apt-get update" and "apt-get upgrade" after the fresh install and sometimes it's failed on the next reboot.

- It can't be the graphics card as I've tried two and it happens with both.

- It can't be KDE or Gnome as it happens with both.

- It shouldn't be my monitor either as sometimes it works just fine.

I love Ubuntu but this is extremely annoying, I don't have the time or the energy to spend the first fifteen minutes every time I start the computer just trying to get to the login screen.
Might be a kernel updated version causing your problems...when your computer is first booting up, press "esc" to enter the grub menu, then arrow down to an older kernel and try booting into that.  If that works, you can comment out the newer kernel that doesn't boot in your menu.lst.

---

### Post by Aualin on 2006-08-29
This happened to me ones...
But then i used suse (i think...)
And same happend when i boted to windows, and after fifth rebott into windows everything worked fine (not linux).
When my dad got home, i said i got the black screen of death (i hadnt read this:P Got the same idea!)
When my dad was sitting there for some time, and all got fixed, i asked him what the hell he did!? He said hi bouted into erro free mode (directly translated from swedish, it mayb be recovery mode).
And run SaX2 i think... But he was looking into xorg.conf and edited something... I'll ask him when i gets home, it's tommorow i think (swedish time).

---

