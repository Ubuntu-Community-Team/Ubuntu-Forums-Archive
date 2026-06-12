---
title: "install linux 8"
date: 2013-08-05
forum: Any Other OS
---

### Post by menschtx on 2013-08-05
After rebooting with the burned copy of Linux 8 in the cdrom tray I get a message to 'Select a boot first drive' Ch3 M. :atapi dvd a dh16s6s. How do I get pass this since it just waits. I like to boot the Linux 8 from the cdrom tray. I did go through an install of Lite 7 thinking if I could install it I could upgrade but now I've got troubles and would like to fdisk and start afresh. What's next?

---

### Post by QIII on 2013-08-05
Hello!

Are you asking about Sabayon?

Thanks.

---

### Post by The Cog on 2013-08-05
I don't know what version of Linux you have there, but I don't think it's Ubuntu (or if it is, it's probably 5 years old). 
Can I suggest that you download a copy from here and try again? [http://releases.ubuntu.com/13.04/](http://releases.ubuntu.com/13.04/)

---

### Post by sandyd on 2013-08-05
> **menschtx said:**
> After rebooting with the burned copy of Linux 8 in the cdrom tray I get a message to 'Select a boot first drive' Ch3 M. :atapi dvd a dh16s6s. How do I get pass this since it just waits. I like to boot the Linux 8 from the cdrom tray. I did go through an install of Lite 7 thinking if I could install it I could upgrade but now I've got troubles and would like to fdisk and start afresh. What's next?

Are you talking about Linux Mint 8?

---

### Post by Tom 6 on 2013-08-05
Hi :)
Please let us know where you got the Cd from.  Was it from a magazine cover?  

Can you boot into Lite 7?  Can you boot into anything at all or is that the problem?   If you can boot into any Gnu&Linux system then there are things we could do such as get to a command-line and run

sudo fdisk -l

to see 
1.  how much hard-drive space you have in total and 
2.  find out how many partitions you currently have on your system and get some idea of how large they are.  

Ideally we might be able to try to help you get Windows back too.  Errr which version of Windows was on this machine before?  That might give us a rough idea of what sort of spec your machine is.  Cpu speed, Ram size, hard-drive space would be good to know but just giving us the version of Windows usually gives a rough indication.  

Regards from 
Tom :)

---

### Post by Hylas de Niall on 2013-08-05
@ OP: Please provide details of your system, and a little more info about which type of linux you're trying to install. 'Linux 8' doesn't appear to be any OS we've ever heard of, and Linux Lite hasn't reached version 7 yet (and won't for a long time to come) either. Did you mean Zorin 7?

Details please or we can't help i'm afraid.

---

### Post by menschtx on 2013-08-06
That's right Sandy and on my 5th try this time using a 12.04 download and burnt to dvd hoping to update later after install and trying the install I'm gett Warning: file:///cdrom/pool/main/g/glib2.0-0_2.22.2-Oubuntu1_i386.db was corrupt. It seems I've gotten this error a couple of times. My last result will be to purchase Ubuntu from the site and try that. I've gone through checking the bios settings, checking burnt dvds for files and all seem correct.

---

### Post by menschtx on 2013-08-06
Tom6 no I can't boot into Lite 7, I got Lite 7  from a website [http://distrowatch.com/?newsid=07171](http://distrowatch.com/?newsid=07171), and since have downloaded and burnt 8, 9 and 12.04 and getting an error message: file:///cdrom/pool/main/g/glib2.0-0_2.22.2-Oubuntu1_i386.db was corrupt. 
Windows Vista
Memory - 1gb
Cpu - ?
HD - 300+gb

---

### Post by Tom 6 on 2013-08-06
Hi :)
Ahah, so it's Mint 8 rather than straight Ubuntu! :)  

We should push you to the Mint forums then but i suspect we have a few suggestions here 1st.  

1.  Do you have a working OS of any sort, even if it's Windows, running on the target machine?  (target = one you want to do stuff to).  If so then maybe try installing a Virtual Machine such as VirtualBox and see if that can read the Cd.  

2.  Can you test the Cd itself in some other machine?  

This might give us a clue whether it's the Cd that is corrupted somehow or the Cd-drive is not as good as it used to be.  They do wear out after a while.  personally i started using really expensive CDs but then found they were much worse for this sort of thing than much cheaper ones.  It turned out that the cheaper the CD the better it seemed to work as a LiveCd.  Perhaps more expensive ones are somehow optimised for storage rather than running?? or maybe i just didn't care as much when i had to bin one.  

Also it might be good to try to find how to to check the Cd using "md5sum" or Sha.  Once you figure it out it is incredibly simple to test Cds and even the initial downloads to check something weird didn't happen in the middle of the process.  Errrr, i have long since forgotten how to do it and it scares me a little tbh.  

So, my suggestions would be to try another CD in the same drive, or the same CD a different way.  And then try the same CD somewhere else.  Then i would probably burn a new CD but using a really really cheap CD rather than a decent one.  All to avoid doing the Sha or Md5 checking.  
Apols and regards from 
Tom :)

---

### Post by howefield on 2013-08-06
Thread moved to "*Other OS/Distro Support*".

---

### Post by Tom 6 on 2013-08-06
Hi :)
Ahh, that is interesting that you are getting the same error message each time.  Btw you can write a single reply to cover multiple topics from multiple people.  Sometimes it is clearer to do as you have done.  All of us did the separate messages to start with so don't worry about having done something wrong.  There is no wrong really, just different approches.  

DistroWatch is an excellent site to get things from.  Usually because it gives good links to proper official sites.  For example you could find the Mint forums by going to 
[http://distrowatch.com/mint](http://distrowatch.com/mint)
which redirects you to their proper page about Mint and that lists the link to their official forums fairly on in the 1st table.  


Btw your hardware sound sufficiently high enough spec for almost any distro, even Ubuntu.  It might be smart to pick something a little lighter such as Mint so that was a good choice.  However, unlike Windows it is not better to go for older version just to get something working on a lower-spec machine.  It's better to just choose different distros, and to keep on hopping from one to the next until you find one distro that does work.  DW also have a "Readers Comments" which is also well worth asking for suggestions of what to try on a particular set of hardware.  They sometimes get a bit side-tracked and loopy so bringing them back on-topic does them a favour too.  (it might not be so bad now i have kinda left it) 
Regards from 
Tom :)

---

