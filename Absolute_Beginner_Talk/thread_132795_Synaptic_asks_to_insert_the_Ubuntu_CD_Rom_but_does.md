---
title: "Synaptic asks to insert the Ubuntu CD Rom but does not see/access it"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-19
Hello all !!!

I tried to get through Synaptic, the program "alien".

Before I started, I cleared all "Cached Package Files".

I did this, because I wanted to Backup the Downloaded Program & its dependencies.

So, before I started, I cleared all "Cached Package Files".

To do this, I did the following:

	a. Launch "Synaptic"
	b. From the Menu, select "Settings\Preferences"
	c. Select the Tab named "Files".
	d. Click on the button named "Delete Cached Package Files".

Then from "Synaptic" I went to download "alien", BUT I selected to NOT install (just download), since I wanted to Backup.

While in the process of downloading, Synaptic asked for the Ubuntu CD-ROM.

Please insert the disk labeled:
Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)
in drive /cdrom/

I put the CD, pressed "OK" & nothing, the Ubuntu can NOT see/access the CD-ROM.

What is wrong?

I have never had such problem...

Thanks.

---

### Post by dvarsam on 2006-02-19
... and If I press cancel, I get the following:

The following problems were found on your System:

W: Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/pool/main/m/make/make_3.80-9_i386.deb

---

### Post by unbutuju on 2006-02-19
hello, you may have to wait a little bit for the cdrom mounts itsself before telling it to go forword... I guess!

and you could check without closing all your working windows at Places > Computer if the cdrom is there!

hope it helps

---

### Post by dvarsam on 2006-02-19
Yes, but the problem is, that when I press on "OK", the same window launches again:

Information:

Please insert the disk labeled:
Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)
in drive /cdrom/

... as if it is NOT trying at all to look in the CD.

---

### Post by nalmeth on 2006-02-19
Can you see the cdrom icon popup on your desktop behind all the windows? If so can you right click it and 'mount'?

---

### Post by dvarsam on 2006-02-19
[QUOTE=nalmeth]Can you see the cdrom icon popup on your desktop behind all the windows? If so can you right click it and 'mount'?[/QUOTE]

Yes, I can see the CD-ROM's icon on the Desktop.

If I right-click on it, there is NO mount choice in the list.

Any Ideas?

---

### Post by cotcot on 2006-02-19
Do you have the install CD in the sources list (/etc/apt/sources.list) ?
You should find a line like this :

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

If not you have to add it.

And if you have 2 CD-drives try the other one.

---

### Post by unbutuju on 2006-02-19
hello again!

try this first just to make sure you are not having any cdrom issues, close everything and just put your ubuntu in your cd-rom and wait, if all is ok acoording to its normal operation, it will open by itself in a short time, openning a window with its root content, if this is not happening then you may have a cd-rom configure problem...

c ya later

---

### Post by dvarsam on 2006-02-19
I solved it !!!

The CD Rom could NOT be Found inside the BIOS.

So I had to swap the cables of: IDE1 & IDE2.

Strange, but now everything is OK...

However, in Ubuntu everythings seemed Fine - I could see the CD-Rom, open it, copy & paste...

... the only problem was the Synaptic working with it....

Strange, huh...

---

### Post by nalmeth on 2006-02-19
> Strange, huh...
computers have personalities sometimes don't they

---

