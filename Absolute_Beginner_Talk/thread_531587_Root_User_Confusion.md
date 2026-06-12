---
title: "Root User Confusion"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by insubstantial on 2007-08-21
Hi, while browsing some articles on Linux security I came across one that said to never log in as root for basic daily use.  My question is, exactly how do i know if im on root, i'm using the account i did on installation and it is an admin account, so is this root?  Because when i checked out User and Groups> User Privileges, my account is allowed the administer the system.

Also, can you suggest a good site/s for a beginner to learn the Linux command line?
thanks.

---

### Post by Deived on 2007-08-21
if you open your terminal and the command prompt shows a $, you are logged in as a user.  If it shows a #, you are logged in as root.
a user would have priveleges on the files he has rights to, so some system stuff is out of your hands.  root has all rights on EVERYTHING, so you can break something you don't mean to.

I don't have any suggestion for command line tutorial though.  Im sure there are a bunch out there though.  I picked up a little book called Linux Desktop Handbook.  A great resource for the beginner.  Only like $10

---

### Post by toidi on 2007-08-21
AFAIK ubuntu does not contain a 'root' account as default for security reasons.

If you want to run something as a 'root' (admin) then you have to type 'sudo' before the command ie.

sudo gedit /etc/X11/xorg.conf

This will let you edit your xorg.conf as 'root/admin' 

sudo basically stands for Super User DO.

Hope this helps

---

### Post by insubstantial on 2007-08-21
Thanks guys, clears up the situation a lot.

I however have one more question that slipped my mind to ask before.  My desktop isn't utilizing the entire monitor screen which leaves a black ring around it. Any solutions on how to fix this?
Current screen resolution is 800x600.

---

### Post by Dr Small on 2007-08-21
Click the menu button on the monitor and stretch the screen. :|

---

### Post by Deived on 2007-08-21
> **toidi said:**
> AFAIK ubuntu does not contain a 'root' account as default for security reasons.

If you want to run something as a 'root' (admin) then you have to type 'sudo' before the command ie.

sudo gedit /etc/X11/xorg.conf

This will let you edit your xorg.conf as 'root/admin' 

sudo basically stands for Super User DO.

Hope this helps

Right.  I don't think the root user is enabled by default.  You have to enable it yourself...
```
sudo passwrd root
```
Should enable it.  You need to create a password for it.  Then sudo and su - will work fine.

---

### Post by Dr Small on 2007-08-21
Ubuntu creates a root account by default on Ubuntu, so you can do "sudo"... Otherwise, how would you do "sudo passwd root" ? Eh?
A root account is automatically setup with your first user's password, by default.

Dr Small

---

### Post by toidi on 2007-08-21
> **insubstantial said:**
> 
Current screen resolution is 800x600.

Funny you should mention that, try clicking on the 'System' then 'Preferences' and finally 'Screen resolution'

If that does not fix your issue then maybe editing your xorg.conf will do.

My install never gave me widescreen support on my acer 26"lcd, so I did the following.

```
sudo gedit /etc/X11/xorg.conf
```

Found the following entries:

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Acer AL2671W"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1280x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1280x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1280x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1280x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1280x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1280x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection

Under the 'Modes' my 1280x768 was originally 1024x768, did a quick 'Search' 'replace' and changed all instances of 1024x768 to 1280x768 (as I would never be using 1024 res anyway).

Saved, logged out and restarted the desktop to get the new resolution.

Hope this helps..

---

### Post by Deived on 2007-08-21
I had the same thing, but havent messed with it.  Ubuntu displays fine with 1200x800, but VirtualBox does not.  Mine only has 1024x768.  Not a big deal, but I want full res when I go full screen.
I don't think it's an xorg.conf issue since Ub does just fine.  It's probably a configuration of VirtualBox, but haven't had a chance to mess with it.

---

