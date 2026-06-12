---
title: "first time used ubuntu"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by SNAKE2 on 2006-12-12
I am deaf, it my first time used it.

I already download 6.06 and have burn it on cd. when I reboot it then it say a>   ( every time i type any words so they cant found anything, what should I do now?](*,) :confused:

---

### Post by kd7swh on 2006-12-12
I don't fully understand what the problem is but I am wondering if you burned the .iso file as data and not a disk image. 

You may also want to make sure that your bios is set to allow the CD to boot rather than your hard disk.

If the CD is booting you can check it for errors in the menu.

good luck!

---

### Post by BarfBag on 2006-12-13
What program did you use to burn the CD?  If it was Nero, did you burn it with the "Burn Image to Disk" option?  Otherwise, weird things like that happen.

If you know for sure that you burned it the right way, you should re-burn it.  It might have skipped.

---

### Post by drphilngood on 2006-12-13
Here is a really good guide to help you get going:

[psychocats-guide_iso]("http://www.psychocats.net/ubuntu/iso")

Good luck!

---

### Post by SNAKE2 on 2006-12-13
yes it was nero 6, i burn it twice, 1) burn cd data 2) burn bootup data....but both are useless. it wont install just like a:>(with white box blinking. ask me commad / file. what should i do with it

---

### Post by Dusty545 on 2006-12-13
You need to make sure you're burning an ISO image to CD.

I'm not overly familiar with using NERO as I tend to use Gnome Baker but there'll most likely be an option (possibly under the 'tools' menu) to burn a CD from an ISO file.

The other option is to extract the ISO image to a folder and burn the contents of the folder to CD.

Burn this to CD and all should be well.

---

### Post by SNAKE2 on 2006-12-13
drphilngood, thanks for the link. It works and so helpful :)

snake2

---

### Post by Atomic Dog on 2006-12-13
In nero you need to File --> open and select the .iso.  A burn window will appear and burn it properly for you.

---

### Post by SNAKE2 on 2006-12-13
now a little problem is..when i install it then it show up:
uncompressing linux____ok, booting the kernel
[17179571.27600]..MP_BIOS bug: 8254 timer not connected to IO-APIC
[17179571.316000] PCI: cannot allocate resource region0 of device 0000:00:11.0


now what is problem?

---

### Post by purplearcanist on 2006-12-13
> **SNAKE2 said:**
> now a little problem is..when i install it then it show up:
uncompressing linux____ok, booting the kernel
[17179571.27600]..MP_BIOS bug: 8254 timer not connected to IO-APIC
[17179571.316000] PCI: cannot allocate resource region0 of device 0000:00:11.0


now what is problem?
Hmm...  There probably is a problem with the installation.  It could be because of your CD.  Try reinstalling it with the CD you used to install it.  If you still get the same error, you could always try a reinstallation with a different CD.

---

### Post by purplearcanist on 2006-12-13
oops, I accidentily tried to post again

---

### Post by lyceum on 2006-12-13
If you are really having too many problems burning, you can get one mailed to you. Free through ship it or buy one form amazon or e-bay, distrowatch links, etc.... I have seen a lot of magazines with it on a disk as well, with instructions on how to boot up.

---

### Post by SNAKE2 on 2006-12-14
it ok now, I have download it again and burn it on disk, it running fine:)
but now it wont let me on internet. i have build in wireless in my laptop. how do I set them up? installed cd or something? 
sorry for asking more help:/ it my first time with linux, had window xp for 2 yrs before that acorn (microsoft)

---

### Post by macogw on 2006-12-14
Click System, Administration, Networking and configure your wireless card for the name of your network and the network password if there is one.  If this isn't the problem, you might need to get the driver and ndiswrapper.  For that, Google for the name of your wireless card and download the Windows driver and then download ndiswrapper.  Go [http://packages.ubuntu.com/dapper/net/ndisgtk](http://packages.ubuntu.com/dapper/net/ndisgtk) there and download ndisgtk (it's a graphical frontend to make set-up easier) along with the 4 packages listed on that page.  If those packages say they need any others, download those too.  Burn those on a disk and copy them to your computer, then double click on the packages to install them.

---

