---
title: "Manipulating photos in Ubuntu"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by MoiraA on 2006-10-23
I haven't had much success with Ubuntu (and that's the understatement of the year):

[http://ubuntuforums.org/showthread.php?t=189966](http://ubuntuforums.org/showthread.php?t=189966)

I've come back to thinking I might ditch XP on my laptop and just install Ubuntu.  I'm fairly sure it would install if I didn't mind it wiping out the windows partition.

The problem is that one of the things I really use the laptop for is to tweak photos from a digital camera (normally with a very simple but perfectly adequate program called jpeg optimiser).

Do you think Ubuntu would recognise either a memory card reader, or the lead from a digital camera, and are there programs which would reduce photos in pixel size for the web, as well as enhance and get rid of redeye?  Would it recognise a bluetooth dongle and pick up my phone camera pictures?  Would it recognise a usb stick (assuming I formatted it with the correct file system) as this is something else which would be absolutely essential?

If I could do all that, OpenOffice would take care of any other spreadsheet or word processing needs - at least for the moment.  I plan to upgrade to a better laptop at xmas and may try to dual boot, but for the moment I feel this low spec laptop might actually run Ubuntu better than XP.  And since I can't get Ubuntu to install on either of my desktop computers, this seems to be my only chance to get to learn it a little, before I take the step of making it my main OS when it becomes necessary to either upgrade to Vista or get left behind with XP.

---

### Post by Marsolin on 2006-10-23
Ubuntu should do everything that you are asking for. Some good photo management apps that import and touch up pictures are [Picasa]("http://linuxappfinder.com/package/picasa"), [Digikam]("http://linuxappfinder.com/package/digikam"), and [F-Spot]("http://linuxappfinder.com/package/f-spot").

---

### Post by MoiraA on 2006-10-24
Many thanks!  Are these photo management apps included with Ubuntu or do they need downloading separately?  When I had Suse on the same laptop as part of a dual boot, these were packages contained on the CDs which you could elect to install.

---

### Post by Sef on 2006-10-24
> Are these photo management apps included with Ubuntu

GIMP is included with Ubuntu.  GIMP = Gnu Image Manipulation Program.

---

### Post by mercurysquad on 2006-10-24
F-spot and gThumb are also included in the latest Ubuntu releasing on 26 Oct.

But I recommend Picasa for Linux, which you can download and install separately. It's way better and easier, IMHO.

As for Ubuntu detecting memory card or digital cameras, I've had no problems with that so far. I just plug in my cam's lead into the USB and it shows up on the desktop, along with asking me if I want to import the photos. Unless your cam uses some non-standard protocol, it will work fine.

---

### Post by Super King on 2006-10-24
> Do you think Ubuntu would recognise either a memory card reader, or the lead from a digital camera, and are there programs which would reduce photos in pixel size for the web, as well as enhance and get rid of redeye?

Does your card reader automatically show up as a 'drive' (ie. drive E) in Windows when you plug it in? If so, it should work the same way in Ubuntu. The programs Marsolin listed can pull images directly off your camera, and should provide the lite image editing/resizing you want. 

> Would it recognise a bluetooth dongle and pick up my phone camera pictures?

Not sure, don't know a lot about Bluetooth and Ubuntu. Someone else should be able to help you there.

> Would it recognise a usb stick (assuming I formatted it with the correct file system) as this is something else which would be absolutely essential?

Yup, assuming the USB stick is FAT or FAT32 formatted (I think 99% of them are 'out of the box') Ubuntu can read and write to it.

---

### Post by Marsolin on 2006-10-24
> **MoiraA said:**
> Many thanks!  Are these photo management apps included with Ubuntu or do they need downloading separately?  When I had Suse on the same laptop as part of a dual boot, these were packages contained on the CDs which you could elect to install.

[Digikam]("http://linuxappfinder.com/package/digikam") and [F-Spot]("http://linuxappfinder.com/package/f-spot") are available from the Ubuntu repositories. [Picasa]("http://linuxappfinder.com/package/picasa") is not. It does have a deb file that you can download though.

---

### Post by fragos on 2006-10-24
I have bluetooth up and running on Ubuntu and use it to send files to my Palm E2.  There are some inconsistecies in the way devices with bluetooth have implemented the protocol.  There's ocassionaly bluetooth devices that don't pair together.

---

### Post by IYY on 2006-10-24
> Do you think Ubuntu would recognise either a memory card reader, or the lead from a digital camera,

Memory cards and digital cameras are usual recognized as simple USB storage, so that will most likely work.

> and are there programs which would reduce photos in pixel size for the web, as well as enhance and get rid of redeye?

Google's Picasa has a Linux version. For finer tuning, you could use The Gimp (like Photoshop). For mass resizing, you could use Imagemagick. It's a command line tool, but easier to use than you would imagine. For example, to resize all files in a folder you could use:

```
convert -resize 800x600 *
```

>  Would it recognise a bluetooth dongle and pick up my phone camera pictures?

Not sure.

>  Would it recognise a usb stick (assuming I formatted it with the correct file system) as this is something else which would be absolutely essential?


Yes.

---

### Post by MoiraA on 2006-10-25
Many thanks for all the helpful replies!  I daren't risk it till I get back from a day trip to Belfast on 7th November to fix my daughter's computer (it's caught this MS spyware WGA stuff) because I don't really want to be grappling with a less than familiar OS when I've got a plane to catch back home etc etc and I might just want an internet connection and irc that works in a familiar way for that day.

You've given me the confidence to install Ubuntu after that though - at worst I'll just have to do what I feel like I've spent the past couple of months doing, ie reinstall Windows.

Super King, my card reader does indeed show up as a separate drive, several in fact.  I suppose I could probably transfer photos quite easily, picking a program to work on them would be the challenge, but you've given me plenty of suggestions.

IYY, when I said reduce in size, what I really meant was turn a jpeg that started out as 400 kb into one that was less than 100 kb in size, so it downloaded on the web very quickly.

Bluetooth will just have to take its chance, I do have a cable connection too, that might work.  However I realise that at present I use the Nokia phone software, which is pretty flakey even in Windows and the chance of it working in Ubuntu is non existant.  I'm not sure if you can transfer phone photos by any other method.

---

