---
title: "Choppy Browsing"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by chesman on 2006-12-30
Okay, whenever i am browsing the Internet the pages are VERY choppy, just like in windows just after i do an install and i do not have the graphics drivers installed. But i have isntalled the ATI graphics drivers in Ubuntu, and it is still choppy, any ideas?

---

### Post by thomasa93 on 2006-12-30
Search the forums on how to install your graphics drivers.  

As a temporary solution, you can:  
Go to edit --> preferences || Advanced and un-check "smooth scrolling"

---

### Post by chesman on 2006-12-30
well i used alien to change the .rpm to a .deb file and it installed fine, thats why i am confused as to why its not working right. how do i check my current driver?

thanks, ill give that a try

---

### Post by jordanmthomas on 2006-12-30
What kind of graphics card do you have?

After you install the proprietary drivers you will need to modify /etc/X11/xorg.conf to tell X to use your new driver instead of the old one.

---

### Post by chesman on 2006-12-31
hmm im useing an ATI X1300.

Now how do i edit that file?

---

### Post by chesman on 2006-12-31
Okay, i am in the file, and i found the section for my ATI card. Just wondering what i would change it to?

> Section "Device"
	Identifier	"ATI Technologies, Inc. ATI Default Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

---

### Post by jordanmthomas on 2007-01-01
For the Driver option you would need to put "fglrx"

Just in case you haven't done all the necessary steps, you should follow this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

and you should be good to go, hopefully

---

