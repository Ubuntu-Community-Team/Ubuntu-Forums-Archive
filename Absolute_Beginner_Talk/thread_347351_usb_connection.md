---
title: "usb connection"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by terapatrick on 2007-01-27
help cannot connect palm device + creative zen m

---

### Post by yabbadabbadont on 2007-01-27
Please post the exact error message, if any.  Also, provide details on the exact steps you take and what happens when you take them.  Help us help you.  :D

---

### Post by an.echte.trilingue on 2007-01-27
I'm sorry but I do not understand your problem.

Do you mean that you can't use [this device]("http://www.amazon.com/Creative-Portable-Media-Player-Black/dp/B0007Y79G2")?

---

### Post by jvc26 on 2007-01-27
He means this creative Zen: [http://www.amazon.co.uk/exec/obidos/search-handle-url/index=electronics-uk&field-keywords=creative%20zen%20m&results-process=default&dispatch=search/ref=pd_sl_aw_tops-2_electronics-uk_13825729_2&results-process=default?tag2=gb-en-google-21](http://www.amazon.co.uk/exec/obidos/search-handle-url/index=electronics-uk&field-keywords=creative%20zen%20m&results-process=default&dispatch=search/ref=pd_sl_aw_tops-2_electronics-uk_13825729_2&results-process=default?tag2=gb-en-google-21)
@terapatrick: We do need more information though, what have you tried thus far? What errors have you come across? What hasnt worked?
Il

---

### Post by bapoumba on 2007-01-27
Hello :)
I own both of these babies. You need **gnomad2** for the creative zen micro and **gnome-pilot** for some palm (which one do you have ? For a lifedrive, it's okay).

To install them, you need to enable universe repositories.

---

### Post by terapatrick on 2007-01-27
no real errors just fails to detect them 
 gnomad2 installed
 gpilot installed and in gnome panel.
 Palm tungsten E2

GNOMAD2 2.8.1
error
no jukeboxes found on usb bus

---

### Post by bapoumba on 2007-01-27
What is the output to **lsusb** when devices are plugged in ?

---

### Post by terapatrick on 2007-01-27
Bus 008 Device 001: ID 0000:0000
Bus 007 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluet ooth Adapter
Bus 003 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 003: ID 06b9:4061 Alcatel Telecom SpeedTouch ISDN or ADSL Modem
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

hope this what you want.

---

### Post by NESFreak on 2007-01-27
> **terapatrick said:**
> no real errors just fails to detect them 
 gnomad2 installed
 gpilot installed and in gnome panel.
 Palm tungsten E2

GNOMAD2 2.8.1
error
no jukeboxes found on usb bus

i can't help you with your palm, but for your zen you need libmtp installed (from the repositories) and gnomad2 compiled with it.
for gnomad2 see [this thread]("http://www.ubuntuforums.org/showthread.php?t=199250").

or if you wish to use amarok. Add t[his repository]("http://kubuntu.org/announcements/amarok-1.4.4.php") and update or install amarok. Then unzip the zip file from [this thread]("http://www.ubuntuforums.org/showthread.php?t=273137"). 

NESFreak

---

### Post by bapoumba on 2007-01-27
```
~ $ lsusb
Bus 004 Device 004: ID 041e:411e Creative Technology, Ltd Zen Micro
Bus 004 Device 003: ID 0830:0061 Palm, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 062a:0001 Creative Labs Notebook Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```
This what I get with both of them plugged in, without launching neither gnomad2 nor gnome-pilot.
I do not know much about usb things, so please someone else have a look at this. I can also do some tests if necessary.

edit : I just use gnomad2 from the edgy repositories (used to have dapper previously, no problem either with dapper's release).
```
Package: gnomad2
State: installed
Automatically installed: no
Version: 2.8.3-1
Priority: optional
```

---

### Post by terapatrick on 2007-01-27
tried but still does not detect either device.

---

### Post by terapatrick on 2007-01-28
[FONT="Arial Black"][SIZE="3"][/SIZE][/FONT]
Did a complete reformat K PILOT installed properly able to sync and detect device
if only  my creative zen vision M would do the same I will be a happy person.

---

