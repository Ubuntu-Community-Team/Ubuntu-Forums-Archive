---
title: "input output error"
date: 2005-09-06
forum: Absolute Beginner Talk
---

### Post by pinbrook on 2005-09-06
Hi Guys

I'm a complete newbie to linux, I'm trying to do my first install to a Dell lattitude.

I bought a boot/instal disk from ebay to get me started, everything has gone fine, I've booted, the cd has copied to disk, I've rebooted removed the Cd and the install is now unpacking. BUT I've hit an error

dpkg-deb (sub process): error in buffer_read stream: failed to write pipe in copy: input output error

dpkg-deb: subprocess paste returned error exit status 2

free(): invalid pointer 0xb7fe3038!

Can anyone offer any ideas please, I think it may be Hard Disk or memory failure but I'd like to be sure

---

### Post by pinbrook on 2005-09-06
[QUOTE=pinbrook]Hi Guys

I'm a complete newbie to linux, I'm trying to do my first install to a Dell lattitude.

I bought a boot/instal disk from ebay to get me started, everything has gone fine, I've booted, the cd has copied to disk, I've rebooted removed the Cd and the install is now unpacking. BUT I've hit an error

dpkg-deb (sub process): error in buffer_read stream: failed to write pipe in copy: input output error

dpkg-deb: subprocess paste returned error exit status 2

free(): invalid pointer 0xb7fe3038!

Can anyone offer any ideas please, I think it may be Hard Disk or memory failure but I'd like to be sure[/QUOTE]
 Further to this, how can I use linux to determine if the problem I have is a faulty HD.

I have a linux boot disk, I assume I can run the OS from the CD, how do I do this and what tests can I run

---

### Post by Kapre on 2005-09-06
[QUOTE=pinbrook]Further to this, how can I use linux to determine if the problem I have is a faulty HD.

I have a linux boot disk, I assume I can run the OS from the CD, how do I do this and what tests can I run[/QUOTE]

pinbrook - Is the HD working (meaning does it have windows on it)? if there is none, try using the Live CD first and scan the HD. Also, is this a notebook that you're installing? If it is a notebook, try searching for "notebook install" in the search menu on this forum.

K

---

### Post by pinbrook on 2005-09-07
No there is no windows.  The laptop only has 128mb memory which is why I thought I'd try the linux route since i only want it for email and internet.

Yes its a dell latitude.

I've just found the download for the"LiveCd" so I'll see if I can find a scan disk option on it. 

Thanks for any help given

Jo

---

### Post by Kapre on 2005-09-07
[QUOTE=pinbrook]No there is no windows.  The laptop only has 128mb memory which is why I thought I'd try the linux route since i only want it for email and internet.

Yes its a dell latitude.

I've just found the download for the"LiveCd" so I'll see if I can find a scan disk option on it. 

Thanks for any help given

Jo[/QUOTE]
 Pinbrook - you might want to read [http://www.ubuntuforums.org/showthread.php?t=55498&highlight=dell+latitude](http://www.ubuntuforums.org/showthread.php?t=55498&highlight=dell+latitude) for your installation of Ubuntu on your laptop.

---

### Post by pinbrook on 2005-09-11
[QUOTE=Kapre]Pinbrook - you might want to read [http://www.ubuntuforums.org/showthread.php?t=55498&highlight=dell+latitude](http://www.ubuntuforums.org/showthread.php?t=55498&highlight=dell+latitude) for your installation of Ubuntu on your laptop.[/QUOTE]
 I'm sort of making progress, I've got Ubuntu working on my Dell using Live CD - dead chuffed with that.

I can mount an external HD, I can see my digital camera card to all looks fine. Gnome is running fine, I can play solitaire!! and use open office and gimp etc etc.

But i am still stuck with my Hard Drive which I need to reformat or scan disk to see if it is faulty or not , how do I do this, I can't find anything on the GUI and having searched the forums I don't really understand alot of the documentation (sorry, but i need a bit longer to get my head around this)

Additionally I've been to the linuxmodem sites to get help on how to get my modem working for dial up access.  and that has gone way over my head.  I have an internal WinModem which appears to be a no goer.  But I also have a Xircom PCMCIA card CBEM56G 100 ethernet and 56k modem - scan modem has identified this.  The modem has supported Lucent/Agere DSP chipset.  Having gathered all this info, sadly I don't know what to do with it.

I'd be grateful for any help, Thanks

---

### Post by pinbrook on 2005-09-13
[QUOTE=pinbrook]I'm sort of making progress, I've got Ubuntu working on my Dell using Live CD - dead chuffed with that.

I can mount an external HD, I can see my digital camera card to all looks fine. Gnome is running fine, I can play solitaire!! and use open office and gimp etc etc.

But i am still stuck with my Hard Drive which I need to reformat or scan disk to see if it is faulty or not , how do I do this, I can't find anything on the GUI and having searched the forums I don't really understand alot of the documentation (sorry, but i need a bit longer to get my head around this)

Additionally I've been to the linuxmodem sites to get help on how to get my modem working for dial up access.  and that has gone way over my head.  I have an internal WinModem which appears to be a no goer.  But I also have a Xircom PCMCIA card CBEM56G 100 ethernet and 56k modem - scan modem has identified this.  The modem has supported Lucent/Agere DSP chipset.  Having gathered all this info, sadly I don't know what to do with it.

I'd be grateful for any help, Thanks[/QUOTE]
 Sorry about the bump!! I'm just having one final attempt to get help before I put my hand in my pocket and pay....

---

### Post by bprof on 2008-03-24
I had this same error, the reason why I got it was because one of my partitions reached 100% and 0 left space. The fix was deleting some files.

---

