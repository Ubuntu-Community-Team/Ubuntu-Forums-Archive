---
title: "External drive problems"
date: 2007-01-10
forum: Apple PPC Users
---

### Post by xsphat on 2007-01-10
I just installed 6.10 on my G4 PowerMac and everything works great, except that I can't write files to my external hard drive. I can not use my thumb drive either. I can read files off of both, but I REALLY need to be able to write to them as well. I messed around with the permissions and it just won't let me change them (in Ubuntu). Both drives are used by my MacBook and my girlfriend's Mac Mini with no problems. Any help would be great, and I am a newbie to Linux, so please be gentle. Thanks.

---

### Post by moeFinley on 2007-01-10
Ubuntu can only read from NTFS drives (unless you install extras).  Are they NTFS?

---

### Post by xsphat on 2007-01-10
I do not know. The bigger one is a Maxtor 200 GB USB 2 drive, the other is just a cheepy 128  MB deal. I tried messing with the permissions on my MacBook in Tiger and that didn't help. How can I tell if a drive is NTFS?

---

### Post by xsphat on 2007-01-10
What I need is a drive that I can read and write to in OS X and Ubuntu, can that be done?

---

### Post by moeFinley on 2007-01-10
If your willing to reformat then yes.  Simple make the drive FAT32 using GParted in Ubuntu or Disk Manager (I think?) on OSX.  Then the drive can be read on Linux, Mac and Windows (because Macs and Linux are so accommodating ;) )


If you don't want to re-format open GParted and you will be able to see if the drive is NTFS.  If it is you can get Ubuntu to read NTFS by following [this guide]("http://ubuntuforums.org/showthread.php?t=217009").  I've not done this and know very little about it.  [COLOR="Red"]**Read the BETA warning at the top of the page.**[/COLOR]

---

### Post by xsphat on 2007-01-10
Thank you for your help, I didn't even know what the Disk Utility app in Ubuntu was called. I am savvy on Mac, so I will have to learn an entire new language for Linux but I am ready to.

---

### Post by moeFinley on 2007-01-10
I know how you feel.  I started using Ubuntu about 7 months ago and sometimes you feel like ](*,) because you can't do the simplest thing.  But just remember you've done it all once when you started with Macs and doing it again will give you a free OS for life (plus all the other advantages)!  And it does get easier ;)

---

