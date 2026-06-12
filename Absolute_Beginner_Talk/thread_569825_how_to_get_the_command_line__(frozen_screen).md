---
title: "how to get the command line ? (frozen screen)"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by doron387 on 2007-10-07
kubuntu 7.04 freezes right after the first "moving" bar,
how can i get to the terminal ? (no keyboard combinations function)

---

### Post by cmnorton on 2007-10-07
Do you mean after the first moving bar has completed or the first segment of the moving bar? You could try CONTROL+ALT+F4 which would take you to a virtual console, if you are far enough along in the boot. This sounds like a video problem. Is this in a laptop?

---

### Post by raja on 2007-10-07
I assume you are saying that the progress bar freezes up while kubuntu is booting up and that you are not able to get to a terminal with Ctrl-Alt-F1. 
In that case what you can so is reboot and when the grub screen comes up, just hit 'e'. This allows you to edit the grub menu. In the kernel line, add 'splash' at the end. What this does is have text messages come up during the booting process - can help find out where during booting you get stuck.

---

### Post by doron387 on 2007-10-07
i booted and pressed e 
in the grab menu, in the kernel line end was already written : **ro quiet splash**
what to write ?

---

### Post by Aesir09 on 2007-10-07
ctrl+alt+F1(or 2 or 3 or 4 or 5 i think) will bring you into a terminal

---

### Post by kirios on 2007-10-07
> **doron387 said:**
> i booted and pressed e 
in the grab menu, in the kernel line end was already written : **ro quiet splash**
what to write ? 
[COLOR="DarkRed"]Remove 'splash' and press Enter.[/COLOR]

---

### Post by doron387 on 2007-10-07
i  removed the splash and went back to the main menu, chose kubuntu and everything went the same : process bar untill the middle of it and then nothing !


more details for your help :

when i ran live cd sessions a few times before the installation, i discoverd that if i just pressed start/install kubuntu (the first menu option) the bar showed, then blank, then another bar, then blank screen and from here it didn't comtinue...(same screen like now, after the installation)

but

if i pressed F4, changed the resolution settings to 1024x768x32 it showed the bar, then blank, then bar, sounded beep when the second bar reached almost its end, then blank, then x appeared, then blue kubuntu screen etc... everything worked well.

so what should i do ?

---

### Post by kirios on 2007-10-07
> **doron387 said:**
> i  removed the splash and went back to the main menu, chose kubuntu and everything went the same : process bar untill the middle of it and then nothing !
.... so what should i do ? 
[COLOR="DarkRed"]Did you get any text below the progress bar? Is this a notebook PC? Do you have an ATI graphics card? [/COLOR]

---

### Post by doron387 on 2007-10-07
i did not have any message below the process bar,

my machine is : laptop hp pavilion dv 6102 ea
+mobile amd sempron 3400
i386 family, 1.8 MHz
nvidia geforce 6150 go, driver : nv4_mini.sys
resolution 1280x800x32
512 ram
hd sata 70 Gb

the istallation steps were :
1. totally recovering of the computer (after bad installation) - the comuter worked fine afterwards w/wnxp.
1.5 defraged the windows hd.
2. resized the win NTFS partition (made it small in 10 Gb) by GParted.
3. ran the live cd session, everything was as usual (i did press F4->chose 1024x768x32->everything worked well)
4. installed kubuntu using the option : "guided - use largest free consistent space in the disk"
5. installation passed perfect untill the shut aown sequence which never in the previous sessions reached the end perfectly - i mean that after ejecting the cd, closing the cd tray and pressing enter it always freezed, and this time again so i had to forced shutdown.

---

### Post by raja on 2007-10-07
I am sorry about my mistake.
What I mean to say was that you should remove the 'quiet' so that you get the status during booting.

---

### Post by kirios on 2007-10-07
Remove 'quiet splash' and try adding 'noacpi nolapic' instead.

---

### Post by doron387 on 2007-10-07
removing "quiet"didn't change, b4 i am booting again, what about the "ro", leave it too ?
(i personally don't have aclue what it does)

---

### Post by doron387 on 2007-10-07
i left the "ro", removed the "quiet splash, added "noacpi nolapic" and the only difference is that now in the obscure screen i can see in left upper corner a blinking  "_"   
please notice what i wrote few messages ago about the experiences that i had during live cd sessions, it must give you experts a clue about what i (the noob)nthink is a resolution setting problem.
waiting 4 reply, thnx 4 the help.
:)

---

### Post by kirios on 2007-10-07
Try adding the number 3 to the end of the grub command line to get to a login prompt, cd to /var/log and check your log files for an error message (using cat and less).

---

### Post by doron387 on 2007-10-07
done, please read the previous message
thnx

---

### Post by kirios on 2007-10-07
Try adding the number 3 to the end of the grub command line to get to a login prompt, then cd to /var/log and check your log files for an error message (using cat and less). 

It's surprising that Kubuntu worked as a live CD for you but not as a hard disk install. Hope someone can help you sort this out.

---

