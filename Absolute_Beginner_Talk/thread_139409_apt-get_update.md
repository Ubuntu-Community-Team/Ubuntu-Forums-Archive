---
title: "apt-get update?"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by masooga on 2006-03-04
So I recently tried to add more repositories following the instructions from another forum thread and I get these error messages.

hmasuga@Rilo:~$ sudo apt-get update
Password:
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release [30.9kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages [31.3kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources [15.7kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Fetched 78.4kB in 34s (2246B/s)
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: Read error - read (5 Input/output error)
E: Problem opening /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

and when I try to open synaptic I get 

E: Read error - read (5 Input/output error)
E: Read error - read (5 Input/output error)
E: Problem opening /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Also, when I reboot my computer I get the error message

translated ATA stat/err 0xc8/00 to SCSI SK/ASC/ASCQ 0xb/47/00

Any help as to what is going on and how to fix it?

Thanks :)

---

### Post by Xian on 2006-03-04
[QUOTE=masooga]Any help as to what is going on and how to fix it?
[/QUOTE]

I would advise not using the us.archive.ubuntu.com in your source list, and instead select another mirror. It has demonstrated itself to have consistent problems.

---

### Post by masooga on 2006-03-04
Thank you!

---

