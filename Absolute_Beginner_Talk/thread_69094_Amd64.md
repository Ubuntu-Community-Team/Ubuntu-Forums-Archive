---
title: "Amd64"
date: 2005-09-25
forum: Absolute Beginner Talk
---

### Post by quixote8 on 2005-09-25
Having trouble with install ubuntu all variants (and all other distro's too).
i386 installs without problems on my 733 Pentium 3. but niether AMD64 or i386 versions of ubuntu are functional on AMD (asus A8N [skt939], gigabyte 6200 vid card, compaq V720 monitor)
the install appaers to go well untill the username password login, then only brown/grey "pincussion" screen with a functional mouse pointeer.
My suspicion is that the Xfree86 is malconfigured somehow but i do not have the skills to find and change necessary things with the command line.
any assistance appreciated   :-?

---

### Post by mlomker on 2005-09-25
>  then only brown/grey "pincussion" screen with a functional mouse pointeer.
My suspicion is that the Xfree86 is malconfigured somehow but i do not have the skills to find 

Good guess.  It probably doesn't like the videocard.

**dpkg-reconfigure xserver-xorg**

---

### Post by quixote8 on 2005-09-25
Thnx mlomker  :)

---

### Post by noerter on 2005-09-25
[QUOTE=mlomker]Good guess.  It probably doesn't like the videocard.

**dpkg-reconfigure xserver-xorg**[/QUOTE]

i have the same problem (yellow-brown screen with functional mouse and nothing more) but with liveCD. Is there any command line to add in order to boot live and overcome this?

---

### Post by mlomker on 2005-09-25
[QUOTE=noerter]i have the same problem (yellow-brown screen with functional mouse and nothing more) but with liveCD. Is there any command line to add in order to boot live and overcome this?[/QUOTE]

I don't know for sure since I don't use the liveCD.  Have you posted a message in their forum?

Generic advice:

1) Press Ctrl-Alt-F2
2) login
3) type **killall gdm**
4) run the command in the last post and select a different video card (VESA being the most compatible)
5) type **gdm**

---

### Post by noerter on 2005-09-25
[QUOTE=mlomker]I don't know for sure since I don't use the liveCD.  Have you posted a message in their forum?

Generic advice:

1) Press Ctrl-Alt-F2
2) login
3) type **killall gdm**
4) run the command in the last post and select a different video card (VESA being the most compatible)
5) type **gdm**[/QUOTE]
 yes ( [http://ubuntuforums.org/showpost.php?p=368416&postcount=13](http://ubuntuforums.org/showpost.php?p=368416&postcount=13) ) but it seems to be a problem noone can solve.

---

### Post by mlomker on 2005-09-25
What I told you works from a hard disk install.  You'll have to login as **root** and I assume that the password is blank.

You'd need to do that on every boot because it's a CD.  If you intend to actually get work done using a liveCD then I strongly recommend Knoppix over Ubuntu.  They provide a means of saving your configuration to a floppy or USB drive.

---

### Post by noerter on 2005-09-25
[QUOTE=mlomker]What I told you works from a hard disk install.  You'll have to login as **root** and I assume that the password is blank.

You'd need to do that on every boot because it's a CD.  If you intend to actually get work done using a liveCD then I strongly recommend Knoppix over Ubuntu.  They provide a means of saving your configuration to a floppy or USB drive.[/QUOTE]
 thank you for your fast reply and advice. Nothing works. The PC just freezes. Ctr-Alt-F2 yields no result. CDROM stops. I get a sound, a yellow screen and a otherwise fully functional mouse cursor. I sure hope Ubuntu is more than that.

---

### Post by mlomker on 2005-09-25
>  Ubuntu is more than that.

Hard freezes are always hardware problems.  The general advice there is to pull out/disconnect anything that isn't necessary for the machine to boot....assuming you have your heart set on Ubuntu.  Otherwise I'd just try a few other distros.

---

### Post by quixote8 on 2005-09-26
[QUOTE=quixote8]Having trouble with install ubuntu all variants (and all other distro's too).
i386 installs without problems on my 733 Pentium 3. but niether AMD64 or i386 versions of ubuntu are functional on AMD (asus A8N [skt939], gigabyte 6200 vid card, compaq V720 monitor)
the install appaers to go well untill the username password login, then only brown/grey "pincussion" screen with a functional mouse pointeer.
My suspicion is that the Xfree86 is malconfigured somehow but i do not have the skills to find and change necessary things with the command line.
any assistance appreciated   :-?[/QUOTE]

still no joy.
just got deeper in a tangle  
my own ignorance (of command line and the general structure of linux / ubuntu)  and the nvidia linux driver problem starting to seem like an insuperable barrier

---

### Post by brentoboy on 2005-09-27
I had the exact same problem, and my PC works now, here's the fix.

Go get the latest bios for the motherboard, and flash your motherboard.
Trust me, you have to - I have the same motherboard you listed, and nothing - not even winxp could get running once the vidio card kicked into gear - and that is an "officially supproted" os for the motherboard.

anyway once you flash your bios, ubuntu still wont work.  Boot in recovery mode, and edit your xorg.conf file to use the vesa driver instead of the nv driver.

nano /etc/X11/xorg.conf

find the spot where it tells it to use the "nv" driver and switch it to "vesa"

now you can boot to desktop and use whatever, what a relief.  You just arent getting the best out of your graphics card yet...

---

Chapter 2

get the latset nvidia drivers from nvidia.  - there are lots of posts on the forums to help you there, so I wont go into it.

---

### Post by brt on 2005-09-27
i also had some problems with my A8N ...

i had to deactivate onboard sound in the BIOS!

now it works great :D

i also installed the "nvidia-glx" package and replaced "nv" with "nvidia" in my xorg.conf file

---

### Post by noerter on 2005-09-28
is there anyway to do this in LiveCD?

---

### Post by brentoboy on 2005-09-28
not that I know of, but you can use grub to boot to recovery mode.  From here, you can disable the "nv" driver switch it to vesa. 

from command prompt as root:
nano /etc/X11.xorg.conf

go find the place where it lists your card, and the driver - which is probably listed as "nv" change it to "vesa"

save, exit, reboot

your system should boot to desktop now.  only problem is it wont use any of the acceleratd features of you gx card.  But, if your motherboard is the same as the one I got (which is sounds like it is) your PC will freeze up when any gpu gets initialized.  Go check out the manufautures website for the mboard and look at the bios flash rom documentation, and see if it looks like you are experienceing a fixed bug.  If so, you've got to take the plunge or life wont get better. (that's the excitment when you buy "bleeding edge" hardware)

after that is all in order, go ahead and try out the instructions for downloading the official nvidia driver 7667 (dont get 7676 - it has issues)

---

### Post by noerter on 2005-09-29
knoppix (liveCD) uses vesa and it works. However it looks a bit strange probably because the graphics card acc features are not in use. Is there anything one can do about that.

---

