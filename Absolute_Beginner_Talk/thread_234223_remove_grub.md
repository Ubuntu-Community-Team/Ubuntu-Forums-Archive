---
title: "remove grub"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by kigina on 2006-08-11
i need to get grub off the MBR.  I want to install vista on it and the CD wont boot with grub there.

---

### Post by rowanparker on 2006-08-11
Providing your BIOS is set to boot from CD it should do whether grub is there or not.

---

### Post by stoeptegel on 2006-08-11
+1
The cd should boot with or without grub.
You might have to make sure the cd/dvd drive you'd like to use is on the master channel if the drive is using a PATA data cable (although newer systems/BIOS also do the slave channel).
Also, you might have to enable booting from cd/dvd in BIOS.

---

### Post by kigina on 2006-08-11
it is set to boot to the CD, i had a slackware CD in there when i turned it on and that booted to the install screen

---

### Post by stoeptegel on 2006-08-11
In that case, the iso is not bootable by design or by burning.
Or maybe you're using a dvd in a cd drive?

---

### Post by cjm5229 on 2006-08-11
Vista is a DVD doesn't come as a CD. Did you go to Windows Vista website and run the system check to see if it is installable on your computor? Another thing, I have noticed when installing a Win OS that you have to hit "Any Key" to boot it. You don't seem to have to do that with Linux. Vista is not real compatible with a lot of hardware yet either, and most of the drivers available aren't Vista compatible either. I had it in my computer for about two weeks and decided it just isn't worth the trouble, I was sure glad I still had Ubuntu!

---

### Post by kigina on 2006-08-11
i have installed vista on this computer before, i know what im talking about.  it does have dvd drive i just said cd because i assume people would know what i meant.

---

### Post by stoeptegel on 2006-08-11
You wanted grub off the mbr, that is as simple as "fdisk /mbr".
Countion here is that this will install NTLDR in the MBR with a linux entry. And therefor linux will not be able to boot. 
And older versions of fdisk.exe also zero the partition table, so you might be carefull in using it on the MBR.

But like i said, it will not solve the boot issue though.

---

### Post by kigina on 2006-08-11
i think it might
the vista cd will boot on the computer i am on right now just now the other one

---

### Post by stoeptegel on 2006-08-11
Well, you're free to try it. Just boot with the windows cd into recovery modus and do fdisk /mbr. Read this though:
[http://www.cknow.com/vtutor/FDISKMBR.html](http://www.cknow.com/vtutor/FDISKMBR.html)

---

### Post by mcduck on 2006-08-11
The BIOS handles booting order of devices, and if the BIOS is configured to boot from a CD before HDD, it will never even access your HDD or GRUB when you have a bootable CD in drive.

It doesn't matter if you have Grub, LILO, Windows, FreeBSD or DOS on your HDD as the HDD isn't accessed.

---

