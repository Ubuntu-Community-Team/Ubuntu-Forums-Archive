---
title: "uninstall ubuntu"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by matchstich on 2007-01-09
i have been searching for a while, found lots on installing this os.
how do get rid of it?
thanks

i tried putting a xp install disk , cept it won't run.

---

### Post by sardion on 2007-01-09
Is ubuntu the only OS on the machine or did you install it for dual booting with windows?

If it is the only OS, boot from the live CD and when it loads up run the installer.  Go thru to the part where it partitions the hard drives and then just tell it to format your entire hard drive to NTFS.  Then windows should install fine.  *BEWARE* the above will erase *all* data on your hard drive.

If you have dual boot set up then you should be able to use the existing windows to reformat the ubuntu piece to NTFS.

What exactly do you mean by "won't run" for the windows cd?

---

### Post by matchstich on 2007-01-09
well, i put in the xp disk and nothing happens, won't run
thanks

---

### Post by sardion on 2007-01-09
Try putting in the Windows XP CD and then booting from it.  Putting it in while Ubuntu is running will not work.  If booting from the Windows disc doesn't work, try what I said above.

Good luck.  Sorry to hear you didn't like Ubuntu but its all about what you prefer.

---

### Post by matchstich on 2007-01-09
i tried that, rebooting and still nada
 but i will try your suggestion,
 thanks

---

### Post by vf514 on 2007-01-09
Try adjusting your BIOS boot order so that your CD-ROM drive is your first priority boot device. On many PCs, you can change your BIOS settings by pressing <delete> the moment your system begins booting. Then, search through menus for an option to change the order of the devices on your computer.

You do not "uninstall" Ubuntu in the usual sense. If there is another operating system on your computer, formatting the partitions that Ubuntu resides on and rewriting the master boot record will suffice. In fact, simply rewriting the master boot record will make it appear as though your other operating system (Windows, for instance) is the only one installed on your computer, as Ubuntu would be inaccessible in such a situation.

If Ubuntu is the only operating system installed, you can overwrite it with Windows by deleting the partitions it resides on (which will most likely be marked as "unknown" by the installer). Reinstalling Windows will overwrite the master boot record automatically.

---

### Post by maino on 2007-01-09
Is the CD drive checked for booting before the hard disk drive?

There is usually some message that comes up first thing when you power on the PC, like
F12 - Choose boot device
or something, and from there you can check the order of the booting devices.

---

### Post by ajmorris on 2007-01-09
what didn't you like about ubuntu?

---

### Post by matchstich on 2007-01-09
i have to have a working scanner, both of my scanners work in windows and i can't get them working in ubuntu. 
thanks

---

### Post by wildkarde on 2007-01-09
> **matchstich said:**
> i have to have a working scanner, both of my scanners work in windows and i can't get them working in ubuntu. 
thanks

have you tried xsane?

---

### Post by kj1h234lkj1234 on 2007-01-09
Just a note: you don't *uninstall* operating systems. You simply overwrite them with a new one.

Basically, you need help installing Windows XP, not uninstalling Ubuntu. :)

---

### Post by Quillz on 2007-01-09
> **matchstich said:**
> i have to have a working scanner, both of my scanners work in windows and i can't get them working in ubuntu. 
thanks
I would recommend you try Xsane. I've found that Ubuntu is very good with auto-detecting hardware. My wireless card just worked, for example, whereas in Windows, I had to install a driver.

---

### Post by ucsdrake on 2007-01-09
hey, question about uninstallation/overwriting Ubuntu, if my Grub is located on hd0 (internal hard drive thats designated dev/hda) with only Windows on it and linux is on hd1 (external designated dev/sda by linux) 

if i were to overwrite Ubuntu on my external hard drive would the Grub have a problem?

as a note i have a Error 21 on boot-up that means my bios cant find my external on the first boot up (i press ctrl+alt+delete and then Grub loads properly) 

and how do i get rid of Grub if i cant just overwrite the external hard drive as described above?

thanks in advance

---

### Post by mdsmedia on 2007-01-09
> **ucsdrake said:**
> hey, question about uninstallation/overwriting Ubuntu, if my Grub is located on hd0 (internal hard drive thats designated dev/hda) with only Windows on it and linux is on hd1 (external designated dev/sda by linux) 

if i were to overwrite Ubuntu on my external hard drive would the Grub have a problem?

as a note i have a Error 21 on boot-up that means my bios cant find my external on the first boot up (i press ctrl+alt+delete and then Grub loads properly) 

and how do i get rid of Grub if i cant just overwrite the external hard drive as described above?

thanks in advanceThis is kind of what I was going to ask. If you just erase/format Ubuntu, will Grub still run and boot into Windows. How would you go about removing Grub from the MBR and having Windows boot itself as it would have prior to installing Ubuntu.

Having said that, if I was going to remove anything, I'd remove Windows and find a way to get the scanners working in Ubuntu. Until you do get them working in Ubuntu, dual-boot XP and Ubuntu and use Windows for scanning. That's just my choice though.

---

### Post by ucsdrake on 2007-01-10
help anybody?

atm i need to get ubuntu off my computer, but ill be putting it on a slave internal HDD at a later date.

i just need to know if that will interefere as stated in my last post

---

### Post by stoer on 2007-01-10
I did some experimenting with installing various linux distros before settling on Ubuntu.
Each one i did't like, i just installed the next one over it.
Before finding ubuntu i decided to get rid of my last linux dist and reinstall windows xp pro, all i needed to do was Install as detailed above (set BIOS to install  from cd/dvd drive) and installed windows. Grub gone, Linux gone. Just windows.

Shouldn't cause any problems.

(now use a dual boot and am 90 % of the time only using  Ubuntu)
Try clicking TAGS and inputting scanner, tons of stuff here that'll help installing one.

Success!

---

### Post by GrahamPR on 2007-01-10
> **ajmorris said:**
> what didn't you like about ubuntu?

Although I generally like Ubuntu here is a few issues I've had with. 

Mouse and keyboard issues (PS2) even on the live CD, and on main install. Freezes/dissapears when the main screen is loading after login. I found the way around this was to Ctrl-Alt-F1 as soon as the beige screen appears, give it half a minute then Ctrl-Alt-F7 back into the GUI.

Screws up Windows installations. It needs to be explained more clearly on the install that grub overwrites the mbr, and that if you have two drives, grub should be installed on the second, or use CD/Floppy etc. and that the Windows bootloader needs to be modified.

Right pain in the butt to get connected with a Speedtouch USB ADSL modem. Msnsged it thanks to a couple of good guides, but it wasn't easy, even for a old DOS man like me. :D More support for this needed as these modems are VERY common in the UK, given away by many providers.

Lack of NTFS support. This issue seems to be being resolved, but not being able to write NTFS is a major disadvantage if you have several disks all formatted to it already, and want to swap and share stuff.

Apart from that it's great. :p

---

### Post by xpod on 2007-01-10
> Right pain in the butt to get connected with a Speedtouch USB ADSL modem

A couple of my friends and family have the same modem compliments of tiscali and it`s mabey the one thing that stopped me jumping straight in and installing ubuntu for them when requested after another of their XP calamities a few months back.

Not that i didn`t think Ubuntu would be much better for them for what they do but that was a few months ago when i knew even less than the little i know now so i wasn`t taking chances with other peoples pc`s....their relatively happy at the moment with their fresh XP installs but mabey next time round i`ll utilise them partitions i left unallocated for them....

....just in case:twisted:twisted: 

Thankfully with NTL things aint been as complicated or i might not have made it through them first days:mrgreen: .
I`ve often contemplated what would have been had i went with Tiscali...lol:rolleyes:

---

### Post by ucsdrake on 2007-01-10
> **stoer said:**
> I did some experimenting with installing various linux distros before settling on Ubuntu.
Each one i did't like, i just installed the next one over it.
Before finding ubuntu i decided to get rid of my last linux dist and reinstall windows xp pro, all i needed to do was Install as detailed above (set BIOS to install  from cd/dvd drive) and installed windows. Grub gone, Linux gone. Just windows.

Shouldn't cause any problems.

(now use a dual boot and am 90 % of the time only using  Ubuntu)
Try clicking TAGS and inputting scanner, tons of stuff here that'll help installing one.

Success!

so the fact that Ubuntu and the Grub are on 2 different hard drives wont come interfere with trying to use windows after the fact? and i already have windows on my internal so i dont want to lose all the files by having to reinstall windows itself

but thanks for the help

---

