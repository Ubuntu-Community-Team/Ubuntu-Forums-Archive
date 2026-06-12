---
title: "Live CD &quot;hard drive&quot;"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2007-02-02
Hi!

I've experimented more with the LiveCD now, and I am curious to know where it actually stores the things you download.  For example, I downloaded over 13 different programs and suffered no performance hits at all!

Also, why is everything so fast?!  With 3.06 Pentium D processor and a GB of RAM, my computer is faster running Linux from the CD than it is running Windows XP from the hard drive.  :lolflag:

---

### Post by kebes on 2007-02-02
Everything you download or install is (as far as I know) being kept in memory. The linux filesystem is mounted off the CD of course, but any changes you make are resident in memory.

How does it do that? Well some very clever programming is involved, no doubt! Linux is fairly well-optimized and thus can fit in memory and run reasonably well even in a LiveCD session. Of course it runs even faster once its installed to the hard drive!

---

### Post by Darklighter137 on 2007-02-02
Awesome!

Has anyone made any progress on being able to run Visual C++ .NET Express Edition 2005 on Linux yet?  That, along with Halo, are the only things I would miss from Windows.

---

### Post by kebes on 2007-02-02
According to the [wine app database]("http://appdb.winehq.org/"), Visual C++ is not running well:
[http://appdb.winehq.org/appview.php?iVersionId=4813](http://appdb.winehq.org/appview.php?iVersionId=4813)

However it appears that people have gotten Halo working:
[http://appdb.winehq.org/appview.php?iVersionId=2720](http://appdb.winehq.org/appview.php?iVersionId=2720)


Hope that helps!

---

### Post by kebes on 2007-02-02
> **Darklighter137 said:**
> Visual C++ .NET Express Edition 2005

Recently I had to do some Visual Basic development, and I installed Windows into a QEMU virtual machine. It worked fine for my temporary needs. If you have a fast machine, virtualization can be a great way to run some Windows programs.

---

### Post by Darklighter137 on 2007-02-03
Thank you!  I will look into these things. =)

---

### Post by Darklighter137 on 2007-02-03
Do I need a copy of Windows to use QEMU?  I own Windows, but like most people I don't have the disk. =(

---

### Post by kebes on 2007-02-03
Yes, you need a copy of windows. QEMU creates a virtual machine that you then install Windows into. However if you don't have a copy of a Windows install CD then this will not work.

---

### Post by Darklighter137 on 2007-02-03
Is there any way to (legally) get around this using a different piece of software?  I already have Windows XP, and I assume that means it is OK for me to use virtualizations software that doesn't need the disk (if there is any).  Alternatively, I was going to buy Windows Vista Home Premium (upgrade) this April.  Will this work?

---

### Post by kebes on 2007-02-03
Well, you'll have to read the lengthy Windows EULA to be sure....

but I believe that if you have a valid Windows license key (and the "Certificate of Authenticity" sticker) then you can install Windows using someone else's Windows CD, and enter your license key, and it's all "legit." However you need to get an install media of some kind to use virtualization.



If you have Windows XP currently installed on your computer, you can, of course, dual-boot, so that when you turn on the computer you have the option of which OS you want to use (Ubuntu or Windows). Alot of people do this and it works great.

---

### Post by Darklighter137 on 2007-02-03
Thank you for all of your help. ^_^

---

