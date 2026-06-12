---
title: "Ubuntu under Parallels, 2 problems"
date: 2007-10-07
forum: Apple Intel Users
---

### Post by allenwatson on 2007-10-07
I'm running Mac OS X 10.4.10 with Parallels Desktop 3.0 (Build 5160). I have installed Windows XP under parallels and have two virtual machines running just fine. I installed Ubuntu (latest download) last week in a Parallels Virtual Machine. It appears to have installed fine. However, I have two huge problems;

* No connection to my wireless network
* No access to my Mac file system

I have never used Ubuntu before, never used Linux or Unix (well, for a month about 20 years ago on a DEC 11/70), and have no idea what "gutsy" or "feisty" might be (mentioned in a thread about wireless problems I tried to understand, but failed). 

I have tried using Parallels menus to connect my wireless device, as I have done successfully under Windows. Doesn't work.

I have tried connecting to my Mac's file system by using Windows Share, as instructed by an article in Macworld magazine, entering my IP address, and my Mac user name in both the User Name and Share fields. I get an icon for the connection on my desktop, but when I double-click it, I'm told I have no access to the files. I do not get prompted for my Mac password, which, apparently, should happen, even though I have enabled Windows Sharing in my mac Sharing prefs Services tab for my username.

Can anyone help?

---

### Post by pxwpxw on 2007-10-08
> **allenwatson said:**
> I'm running Mac OS X 10.4.10 with Parallels Desktop 3.0 (Build 5160). I have installed Windows XP under parallels and have two virtual machines running just fine. I installed Ubuntu (latest download) last week in a Parallels Virtual Machine. It appears to have installed fine. However, I have two huge problems;

* No connection to my wireless network
* No access to my Mac file system

I have never used Ubuntu before, never used Linux or Unix (well, for a month about 20 years ago on a DEC 11/70), and have no idea what "gutsy" or "feisty" might be (mentioned in a thread about wireless problems I tried to understand, but failed). 

I have tried using Parallels menus to connect my wireless device, as I have done successfully under Windows. Doesn't work.

I have tried connecting to my Mac's file system by using Windows Share, as instructed by an article in Macworld magazine, entering my IP address, and my Mac user name in both the User Name and Share fields. I get an icon for the connection on my desktop, but when I double-click it, I'm told I have no access to the files. I do not get prompted for my Mac password, which, apparently, should happen, even though I have enabled Windows Sharing in my mac Sharing prefs Services tab for my username.

Can anyone help?

One alternative is to set up a triple boot system for Macosx, XP and Ubuntu, but I assume you have considered multi-boot options.

I think there are 3 parts to a solution, the first 2 apply to standard physical systems.

1. Wireless in Ubuntu needs additional installation and setting up, depending your Macintel (core duo or C2d ) and Ubuntu version, before it works. Then Ubuntu 704 (Feisty) works well, but I think Gutsy still has some problems which you dont really need here  (it is not released yet). 

2. Access to macosx files - there is a basic file ownership and permissions issue even in direct phyusical access. Both Macosx and Linux use the same system but assign different User ID numbers so problems arise. Also ubuntu cannot write to macosx extended journalled systems, journalling can be disabled in macosx, but reduces file system strength.

3. Then you have the additional complication of running in parallels, 
access to wireless hardware, and file access between virtual systems.
 
Parts 1 and 2 are covered in howtos and other recent threads for standard physical systems. But Part3 Virtual Machine aspect - I dont know, there may be answers to both the files and wireless hardware issue. They seem like a normal requirement. 

It is a fairly daunting project - interesting. 

That is all I can offer, I hope someone else can take it from there.

---

### Post by cyberdork33 on 2007-10-08
> **allenwatson said:**
> I'm running Mac OS X 10.4.10 with Parallels Desktop 3.0 (Build 5160). I have installed Windows XP under parallels and have two virtual machines running just fine. I installed Ubuntu (latest download) last week in a Parallels Virtual Machine. It appears to have installed fine. However, I have two huge problems;

* No connection to my wireless network
* No access to my Mac file system

I have never used Ubuntu before, never used Linux or Unix (well, for a month about 20 years ago on a DEC 11/70), and have no idea what "gutsy" or "feisty" might be (mentioned in a thread about wireless problems I tried to understand, but failed). 

I have tried using Parallels menus to connect my wireless device, as I have done successfully under Windows. Doesn't work.

I have tried connecting to my Mac's file system by using Windows Share, as instructed by an article in Macworld magazine, entering my IP address, and my Mac user name in both the User Name and Share fields. I get an icon for the connection on my desktop, but when I double-click it, I'm told I have no access to the files. I do not get prompted for my Mac password, which, apparently, should happen, even though I have enabled Windows Sharing in my mac Sharing prefs Services tab for my username.

Can anyone help?
Hardware is seen differently in parallels (a 'virtual' machine) than you would see installing natively. you should not have to mess with connecting wirelessly from within a VM. if OSX can connect, you are using that connection in your VM.

---

### Post by pxwpxw on 2007-10-08
> **cyberdork33 said:**
> Hardware is seen differently in parallels (a 'virtual' machine) than you would see installing natively. you should not have to mess with connecting wirelessly from within a VM. if OSX can connect, you are using that connection in your VM.

How does that work. Don't you have to set up network sharing in Macosx and then an IP static address connection from Ubuntu and access it as a share?

---

