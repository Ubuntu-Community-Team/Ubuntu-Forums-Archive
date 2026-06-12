---
title: "Linux Security Concern"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by lollypop929 on 2006-12-15
I am about to make the plunge and transition from XP to Ubuntu. I do have a concern since I have a lot of data that needs to be secure. At present, I use PGP desktop to encrypt the boot drive. If my computer is lost or stolen, the data cannot be accessed. 

It appears that in Ubuntu, anyone can use a boot CD to change my passwords and access the data. Is there a program available that will allow me to encrypt my boot partition to keep it secure?  

Thanks.

---

### Post by deadgobby on 2006-12-15
[https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=encryption&titlesearch=Titles](https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=encryption&titlesearch=Titles)

---

### Post by bodhi.zazen on 2006-12-15
Yes these Live CD's are very powerful and physical access is a liability :P

first, disable booting from CR/Floppy, etc

Password protect GRUB and BIOS

Put you data on a separate partition and only keep it mounted when you need it.

for encryption: [TrueCrypt](http://doc.gwos.org/index.php/TrueCrypt)

There is a great book you may check out:

[Hardening Linux](http://www.amazon.com/Hardening-Linux-James-Turnbull/dp/1590594444?tag2=gp04-20)

---

### Post by 23meg on 2006-12-15
Note that with any OS, not just Ubuntu, anyone with physical access to your machine can boot with a live CD and do whatever they like to your data; it's a matter of physical security rather than software security. Even if it's encrypted, with unlimited physical access, they can find means of copying it and then decrypting it with brute force.

With that said, check out [this guide]("https://help.ubuntu.com/community/EncryptedFilesystemHowto3") if you want an encrypted filesystem. I'm not sure it works in Edgy though; doing a forum search 
will certainly help.

---

### Post by Hendrixski on 2006-12-15
If you think the Ubuntu Live CD totally cancels out the security of your hard-drive, try KNOPPIX.  It comes with tools for computer forensics (so you can even read files that have been recently deleted) as well as network security testing tools, and a whole bunch of other stuff.  Everything that you think is safe behind a password - in both windows and Linux - can be read, modified, and any other sorts of unsafeness.

---

