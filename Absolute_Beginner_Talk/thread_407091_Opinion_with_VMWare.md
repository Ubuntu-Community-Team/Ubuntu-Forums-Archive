---
title: "Opinion with VMWare"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by ada2d on 2007-04-11
I have Ubuntu Edgy installed with Beryl and am loving it.  However, I continuously need to reboot into XP to use a couple Win32 apps.

I found a howto (see below for link) which allows VMPlayer to use your current windows installation but would like to know if it is better / safer / pros & cons to converting the windows installation into a virtual machine.

[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html")

Any opinions would be appreciated as I am still pretty new to Ubuntu.

---

### Post by Bachstelze on 2007-04-11
I never tried it myself but judging from what this says, I don't think it can do much harm. It's all up to you :)

---

### Post by bobplano on 2007-04-11
it depends on the applications. some of them can be run with [wine]("winehq.org"). if you have a lot of programs that have no alternative in ubuntu and can't run with wine then you can start thinking about VMware

---

### Post by PilotJLR on 2007-04-11
VMware is outstanding for cases when you MUST run a windows app. So long as you don't expect to play Quake on there, it works!
I keep a windows XP virtual machine on my workstation, since a few courses at my grad school require some windows programs.

---

### Post by igknighted on 2007-04-11
I would look into an open solution like Qemu or Xen first, but failing this VMWare isn't a bad choice.  With Qemu you even have some expirimental 3d support if you apply a patch, so you might be able to use some of the more basic 3d games in it.

---

### Post by jgatrell on 2007-04-11
I converted my Windows XP installation and run it in vmplayer on my Linux workstation and vmserver on my Linux server.  Everything works fine.  Photoshop and Truespace both run as well as any windows application can.

I have never tried method 2, but I will this weekend.

---

### Post by qpieus on 2007-04-11
VMWare works fine for me although sometimes apps inside it seem slow.
VirtualBox is an open source virtual machine application. It runs as well as VMWare, and is a good choice if you want to avoid proprietary apps like vmware. I have XP set up within a VirtualBox VM and it works great.
[http://www.virtualbox.org/]("http://www.virtualbox.org/")

---

### Post by Netherspirit on 2007-04-11
I am also happy with VMWare. I use it to run WinXP to use VS2005 and MSSQL2005. It does seem a little slow at times, but then again, I don't have a very powerful machine. I was surprised it worked at all. :D

---

