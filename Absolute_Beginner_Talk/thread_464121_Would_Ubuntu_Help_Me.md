---
title: "Would Ubuntu Help Me?"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Zeph79 on 2007-06-04
Currently we have a workgroup of about 15 computers that share files on a server running windows server (bleh).   

I want to install a version of linux that I can use for this purpose as well as a place to send backups to at night.  


The only real requirement is that I can create shares and limit who has access to them (via username or whatever).    Meaning if I make a share called "stuff" and I only want 3 people to have access to that folder, I want to block everyone else out of it.   Should be easy right?


Also, does the LAMP server have a GUI?   Just wondering, I havent installed it yet.

---

### Post by phr0ze on 2007-06-04
Of course Ubuntu or any flavor of linux can do this. But so can alot of Network appliances too. SOHO NAS devices work well and take up less room. I use the buffalo Terastation. Even windows XP Pro will do this fine.

Again, Ubuntu is fine for this.

---

### Post by gerscht on 2007-06-04
Samba will give you all these options. You can either do it on a workgroup basis or set up samba to act as a domain controller. Have a look here: [http://www.samba.org/samba/docs/SambaIntro.html](http://www.samba.org/samba/docs/SambaIntro.html)

To do backups, I've got a setup where snapshots are written using rsnapshot (available via apt [http://packages.ubuntu.com/dapper/utils/rsnapshot](http://packages.ubuntu.com/dapper/utils/rsnapshot)). This has the advantage, that users can go back to older versions themselves (just read access of course).

---

