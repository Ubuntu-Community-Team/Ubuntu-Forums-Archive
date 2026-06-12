---
title: "Ubuntu in windows XP"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Big_Kiwi on 2007-05-11
**[COLOR="RoyalBlue"]Can any one help me out with this one[/COLOR]**
When in ubuntu I can see my windows drive and retrive data off of it but when I am in windows I can not see my ubuntu drive or retrive data off of it dose any onr know how I can make my ubuntu drive visable in windows Xp.
Also I use a progam calld MS Moiney for my accounts and budgeting, can I get this progam to install and work in Ubuntu

---

### Post by divague on 2007-05-11
I use explore2fs  to access my linux partition from windows

---

### Post by skwishybug on 2007-05-11
> **Big_Kiwi said:**
> **[COLOR=RoyalBlue]Can any one help me out with this one[/COLOR]**
When in ubuntu I can see my windows drive and retrive data off of it but when I am in windows I can not see my ubuntu drive or retrive data off of it dose any onr know how I can make my ubuntu drive visable in windows Xp.
Also I use a progam calld MS Moiney for my accounts and budgeting, can I get this progam to install and work in Ubuntu

[FS-Drive]("http://www.fs-driver.org/") will apparently allow you to read an ext3 drive from Windows. I don't know for sure if it will, but I sure hope so since I set up my home partition as ext3. Unfortunately windows cannot read ext2/3 natively.

For an equivalent to MS Money check out GnuCash. I find it to be in between Money and Quicken in terms of what it can do. It is in the repositories.

Edit: Or you can try Wine ([http://appdb.winehq.org/appview.php?iAppId=79](http://appdb.winehq.org/appview.php?iAppId=79))

---

### Post by phiphedog on 2007-05-11
yeah you can, just install ext2-IFS from here [http://www.fs-driver.org/](http://www.fs-driver.org/) and you can assign your linux partitions drive letters in the control panel of windows.

---

### Post by icechen1 on 2007-05-11
> **Big_Kiwi said:**
> **[COLOR="RoyalBlue"]Can any one help me out with this one[/COLOR]**

Also I use a progam calld MS Moiney for my accounts and budgeting, can I get this progam to install and work in Ubuntu

There is an alternative called gnucash

---

### Post by Big_Kiwi on 2007-05-11
If I want to keep using MS Money can I install it using wine

---

### Post by icechen1 on 2007-05-11
> **Big_Kiwi said:**
> If I want to keep using MS Money can I install it using wine
This will help you knoing if it works:
[http://appdb.winehq.org/appview.php?iAppId=79](http://appdb.winehq.org/appview.php?iAppId=79)

---

### Post by skwishybug on 2007-05-11
Depends on the version. Check the link I posted and see if your version is listed there and what the results are, that will give you an idea. Ultimately you won't know unless you try.

Personally Wine and I don't get along all--and I haven't tried it for many applications since I have found most of what I need from the repositories anyway.

---

