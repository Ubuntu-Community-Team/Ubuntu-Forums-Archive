---
title: "Very new to Linux"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by richard978 on 2008-03-10
I've not installed linux before and I've never used it. I'm currently a CFML developer looking at PHP. I've tried developing PHP on windows but the version of apache I'm using just isn't the same as the linux server I host on. 

I've decided to download 6.06...is this the correct verion to download?

I've decided to install abuntu and will be looking at running a dual boot operating system XP and abuntu linux. I also want to install apache, php and mysql. Has anyone got any advice?

I will be looking at a products like dreamweaver, photoshop,topstyle etc etc....anyone got any advice on products worth buying?

---

### Post by Dr Small on 2008-03-10
6.06 was the last LTS (Long time support) version. It is currently out of date and will be replaced with 8.04 in April. So, you do have an older version that is about to drop support.

As for wanting to develop with Php, I find that XAMPP is an excellent resource for Apache / Php / MySQL etc, and I have written a guide on it, here:
[http://php.8ez.com/drsmall/blog/?p=96](http://php.8ez.com/drsmall/blog/?p=96)

As for what applications to buy, I recommend none. Most paid software on the market is designed to run on Windows and may not function properly (or at all) on Ubuntu. Instead, I recommend installing applications from Ubuntu's repositories, as there are loads of Applications that can be installed.

You can access Ubuntu's repository in GUI form from System > Administration > Synaptic Package Manager, or Application > Add / Remove.

Good luck!
If you have any questions or problems, please let us know :)

Dr Small

---

### Post by dgray_from_dc on 2008-03-10
> **richard978 said:**
> I've not installed linux before and I've never used it. I'm currently a CFML developer looking at PHP. I've tried developing PHP on windows but the version of apache I'm using just isn't the same as the linux server I host on. 

I've decided to download 6.06...is this the correct verion to download?

I've decided to install abuntu and will be looking at running a dual boot operating system XP and abuntu linux. I also want to install apache, php and mysql. Has anyone got any advice?

I will be looking at a products like dreamweaver, photoshop,topstyle etc etc....anyone got any advice on products worth buying?

6.06 is the LTS version and is a good starting point for stability.  However, later versions can be just as stable.  Plus there's more eye-candy :).  There will be, however, a new LTS release this year.

Ubuntu won't contain many of the Windows apps you're accustomed to, but there are many others that may suit your needs.  Here are links to some lists.
[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)
[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

There's also wine, a Windows API implementation that runs many Windows apps directly in Linux.

Hope this helps!

---

### Post by Inxsible on 2008-03-10
If you are looking specifically for a LTS version, you might just wait another month - month and a half to get the latest 8.04

If LTS is not a concern, then the latest stable release is the 7.10 (Gutsy Gibbon) which is pretty neat with a lot of eye candy and more importantly, stability, over the older versions.

---

### Post by richard978 on 2008-03-10
Ok I've just started to download 7.10, I will checkout the software available. 

Can anyone recommend virus software?

---

### Post by hyper_ch on 2008-03-10
what do you need anti virus software for?

(and I think you meant to write anti viruse and not just "virus" software)

---

### Post by Sef on 2008-03-10
> Can anyone recommend virus software?

You don't need anti-virus with Ubuntu or any GNU/Linux distros.

---

### Post by analoog on 2008-03-10
[http://clamtk.sourceforge.net/](http://clamtk.sourceforge.net/) 
You can easily install it via applications -> add/remove
But I don't think many people run a virus scanner on ubuntu.

---

### Post by sayakb on 2008-03-10
@OP
You do not need any antivirus software with Linux.
Also, you might run some of the Windows apps using Wine

```
sudo apt-get install wine
```

Check your program's compatibility at: [http://appdb.winehq.org](http://appdb.winehq.org)

---

### Post by kwacka on 2008-03-10
After installing , go to System --> Admin  --> Synaptic package manager. Click on settings in the software manager that opens, and click all the boxes (do for 3rd party software too). Apply.

Now click on the reload button to update.

Next, click on 'Edit --> Select Packages by task and click on 'install LAMP server' OK. Apache, MySQL & PHP5 will be installed.

Alternatively, check out the page at howto forge: [http://www.howtoforge.com/howtos/linux/ubuntu?from=70](http://www.howtoforge.com/howtos/linux/ubuntu?from=70)

(There's pretty good Ubuntu install solutions at the same site).

---

