---
title: "Digital Camera"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by BruschiOnTap on 2006-03-08
I bought an Oregon Scientific pocket camera (the one that's slightly thicker than a credit card and about the same dimensions) but then I switched to Linux from Windows.  I have a CD with drivers on it but I'm not sure if they are meant specifically for Windows/Mac.  If I *can* put them on Ubuntu, where would I stick the files?  I tried simply trying to get it recognized as a USB drive but the device isn't configured to work that way.

Will I be able to get it going on my machine?  If so, how?

---

### Post by Zimmer on 2006-03-08
Have had a quick look at their web site. Does your camera have support for an SD memory card?
If yes, then you can purchase a USB card reader(which automounts as a drive) and use the memory card to transfer pictures( but not the ones stored on the Camera's internal memory). I use this method in preference to attaching any camera to the PC (WinXP or Linux) . Also, the multi-card readers come in handy if you change camera or have a friend visit who has , say, a CF card  in their camera.

For manually mounting it this may help:
[http://linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=1845](http://linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=1845)
and
[http://home.gagme.com/greg/linux/usbcamera.php](http://home.gagme.com/greg/linux/usbcamera.php)
And apparently there is a program gphoto2 which might recognise the camera...I haven't investigated that yet, though.

---

### Post by cwaldbieser on 2006-03-08
[QUOTE=BruschiOnTap]I bought an Oregon Scientific pocket camera (the one that's slightly thicker than a credit card and about the same dimensions) but then I switched to Linux from Windows.  I have a CD with drivers on it but I'm not sure if they are meant specifically for Windows/Mac.  If I *can* put them on Ubuntu, where would I stick the files?  I tried simply trying to get it recognized as a USB drive but the device isn't configured to work that way.

Will I be able to get it going on my machine?  If so, how?[/QUOTE]
gphoto2 seems to support some Oregon Scientific models:
```

$ gphoto2 --list-cameras | grep regon
	"Oregon Scientific DShot II"
	"Oregon Scientific DShot III"

```
You could try
```

$ gphoto2 --auto-detect

```
to see if it detects your camera.

---

