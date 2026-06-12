---
title: "Catastrphe!  GRUB broken!"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Northsider on 2008-02-11
OK, I recently had a dual boot working fine with Kubuntu and XP.  I wanted to try to install Fedora to give it a real test.  for some reason my computer shut down haflway through the install.  Now I have an empty Linux partition with a broken grub loader, and an XP partition, which I assume is still in tact because I did not touch it.

Ok, tried to boot after computer failed, and got a grub error.  Googled to find answer: boot with windows cd, ran fixmbr and fixboot.  Now when I reboot I get "Operating system not found".  I am 99% sure that the XP partition is still there and in tact...but how to boot to it?  any ideas?  Thanks.

---

### Post by hyper_ch on 2008-02-11
do you have the alternate install cd? Or Grub Super Disk?

---

### Post by Northsider on 2008-02-11
I have Linux restore cd, as well as Windows install cd.

---

### Post by renzokuken on 2008-02-11
not sure quite how to do it but a kick in right direction would be to "reinstall grub using a live cd" i think........ there should be plenty of guides how to do that on the net

---

### Post by hyper_ch on 2008-02-11
what is that linux restore cd?

---

### Post by xeth_delta on 2008-02-11
Here is a link on how to install grub from a live CD: [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

Are you sure the linux partition is empty, and not only unmounted? If you are able to mount the linux partition, please do make a backup of /boot before reinstalling grub.

---

### Post by Northsider on 2008-02-11
> **hyper_ch said:**
> what is that linux restore cd?

I believe it is this one:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by xeth_delta on 2008-02-11
> **Northsider said:**
> I believe it is this one:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Given that you are trying to repair an Ubuntu installation, wouldn't it perhaps be better to first try with an Ubuntu live CD, of the same version you already have installed?

---

### Post by Northsider on 2008-02-11
> **xeth_delta said:**
> Given that you are trying to repair an Ubuntu installation, wouldn't it perhaps be better to **first try with an Ubuntu live CD, of the same version you already have installed?**

I attempted that as well.  I booted with live cd (7.10), and tried to reinstall.  It got pretty far along with the installation and then it just ended.  No messages, no errors, it just crashed to the desktop.

---

### Post by xeth_delta on 2008-02-11
> **Northsider said:**
> I attempted that as well.  I booted with live cd (7.10), and tried to reinstall.  It got pretty far along with the installation and then it just ended.  No messages, no errors, it just crashed to the desktop.

I don't mean completely reinstalling Ubuntu, just grub.

---

### Post by Northsider on 2008-02-11
> **xeth_delta said:**
> I don't mean completely reinstalling Ubuntu, just grub.

Ok, I can do that with live 7.10 cd?

---

### Post by xeth_delta on 2008-02-11
> **Northsider said:**
> I attempted that as well.  I booted with live cd (7.10), and tried to reinstall.  It got pretty far along with the installation and then it just ended.  No messages, no errors, it just crashed to the desktop.

One more idea. Did you check the integrity of the image you burnt to the CD, the MD5 sum? You should also know that it is recommended to burn the image at 4x or less.
Here is a link about it: [https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28]("https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28")

Bad written CDs can cause a lot of problems.

---

### Post by xeth_delta on 2008-02-11
> **Northsider said:**
> Ok, I can do that with live 7.10 cd?

Sure you can, follow the steps suggested in the link from post #6

---

### Post by Northsider on 2008-02-11
I always burn with lowest speed, when I make music cds they come out horribly, so I always burn at lowest speed.
> Sure you can, follow the steps suggested in the link from post #6

Ok. Ill try that.

---

### Post by xeth_delta on 2008-02-11
> **Northsider said:**
> I always burn with lowest speed, when I make music cds they come out horribly, so I always burn at lowest speed.

Not to be picky, did you also check the MD5 sum for image integrity, before burning?

---

### Post by Northsider on 2008-02-11
> **xeth_delta said:**
> Not to be picky, did you also check the MD5 sum for image integrity, before burning?

No I did not.:(

---

### Post by xeth_delta on 2008-02-11
> **Northsider said:**
> No I did not.:(

You should do that. Follow the instructions on MD5 sums in the link I gave you in post #12

---

### Post by Northsider on 2008-02-11
ok, I will.  Thanks for the help.

---

### Post by xeth_delta on 2008-02-11
> **Northsider said:**
> ok, I will.  Thanks for the help.

No problem! Hope it works, and let us know how it went.

---

