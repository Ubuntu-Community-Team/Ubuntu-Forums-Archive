---
title: "Gimp 2.5.0 Development DEB"
date: 2008-05-11
forum: Art &amp; Design
---

### Post by zeronet on 2008-05-11
Well, a friend had some issues with his wacom tablet with Hardy GTK and Gimp 2.4, so I´ve compiled Gimp 2.5.0 myself and made a deb because I wanted to give it to another friends too. It doesn´t deletes Gimp 2.4, it´s a parallel setup on /opt/gimp-2.5.

This deb was tested only on Hardy Heron and Feisty Fawn (doesn´t works there because Cairo is too old), but it should work on Gutsy Gibbon.

I hope it could be useful for someone :)

Here´s the download link:

Download through Mediafire
[http://www.mediafire.com/?wxlo9cimyqi](http://www.mediafire.com/?wxlo9cimyqi)

Download through RapidShare
[http://rapidshare.com/files/114420374/gimp-2.5.deb.html](http://rapidshare.com/files/114420374/gimp-2.5.deb.html)

Another mirror, thanxs to Dezine for it: 
[http://ubuntuist.com/downloads/gimp-2.5.deb](http://ubuntuist.com/downloads/gimp-2.5.deb)

Some screenshots:
New interface changes:
[[IMG]http://img227.imageshack.us/img227/1504/gimp2vq8.th.jpg[/IMG]]("http://img227.imageshack.us/img227/1504/gimp2vq8.jpg")

Just drawing a bit:
[[IMG]http://img227.imageshack.us/img227/7600/putasposersfa6.th.jpg[/IMG]]("http://img227.imageshack.us/img227/7600/putasposersfa6.jpg")

Release notes and changes since 2.4.x:
[http://gimp.org/release-notes/gimp-2.5.html](http://gimp.org/release-notes/gimp-2.5.html)


[SIZE="5"][COLOR=Red]**EDIT:**[/COLOR][/SIZE]
 
Gimp 2.5.1 Development Snapshot DEB for Debian Lenny, but it should work on Ubuntu Hardy:

[http://in.solit.us/archives/show/146113](http://in.solit.us/archives/show/146113)

Thanks Gadi for the uploading and Olskar for testing it on Hardy.

---

### Post by mech7 on 2008-05-12
the differt width of the panels make it look kinda sloppy

---

### Post by olskar on 2008-05-12
Could you perhaps upload it somewhere else? Mediafire doesnt like me..

---

### Post by eldragon on 2008-05-12
nice anime doodle.

---

### Post by Venko on 2008-05-12
I tried compiling this myself so that I could have a look at it but ran into problems.

Thanks for providing this package, I'll see if I can get it to work :)

**[Edit]** I'm having problems with Mediafire too. Any chance of uploading this elsewhere?

---

### Post by zeronet on 2008-05-12
Well, my upload speed is very low, 64k/s so It´s impossible for me upload 30Mb onn uploading web services, but a friend is going to upload the package on rapidshare, I´ll add the link when it finishes, I made the same with the mediafire link, If someone could download it from mediafire, and upload it to another host, it would be great :)

---

### Post by zeronet on 2008-05-12
[B]Uploaded to rapidshare:
[/B]

[http://rapidshare.com/files/114420374/gimp-2.5.deb.html](http://rapidshare.com/files/114420374/gimp-2.5.deb.html)

---

### Post by k99goran on 2008-05-12
They've solved the multiple window problem half-way. Only one icon is visible in the dock/taskbar (if you set it up properly), but if you minimize or move the main window, the other windows stays in their place.
I would like to see a dock/undock button in the main window to allow the user to easily switch between the traditional GIMP multi-window view and the more Photoshop-like single-window view.
The menus remind me a lot of GIMPshop.

---

### Post by tuggy on 2008-05-21
so can we get a deb for 2.5.1? :D

---

### Post by Sordelka on 2008-05-21
There is a 2.5.1?

---

### Post by Half-Left on 2008-05-22
> **k99goran said:**
> They've solved the multiple window problem half-way. Only one icon is visible in the dock/taskbar (if you set it up properly), but if you minimize or move the main window, the other windows stays in their place.
I would like to see a dock/undock button in the main window to allow the user to easily switch between the traditional GIMP multi-window view and the more Photoshop-like single-window view.
The menus remind me a lot of GIMPshop.

Thats because of compiz which doesn't manage the GIMP windows right, metacity does it proper.

---

### Post by Half-Left on 2008-05-22
> **Sordelka said:**
> There is a 2.5.1?

Not yet no.

---

### Post by Zeirus on 2008-05-25
> **Half-Left said:**
> Not yet no.

Changes in GIMP 2.5.1
=====================

 - further improvements to the status bar
 - made the center point of rectangles snap to the grid and rulers
 - improved Alpha to Logo filters
 - better cursor feedback in the Intelligent Scissors tool
 - rotate JPEG thumbnails according to the EXIF orientation
 - tweaked behavior of the new Polygon Selection tool
 - improved event smoothing for paint tools
 - prepared PSP plug-in to deal with newer versions of the file format
 - allow plug-ins to work in parallel on different layers of the same image
 - pass through GEGL command-line options
 - added 22 new variations to the Flame plugin
 - only show operations from relevant categories in the GEGL tool
 - added new translation (Icelandic)
 - bug fixes and code cleanup


Copy & Past from here: 
[http://developer.gimp.org/NEWS](http://developer.gimp.org/NEWS)

but in FTP server there is only the old version 2.5.0:
[ftp://ftp.gimp.org/pub/gimp/v2.5/](ftp://ftp.gimp.org/pub/gimp/v2.5/)

---

### Post by tuggy on 2008-05-25
i think thats the release notes for the *future* 2.5.1 version. its a work in progress, so it doesnt mean it is released. my mistake also :)

---

### Post by dezine on 2008-06-01
Just wanted to offer another option for downloading it.

[Download link]("ubuntuist.com/downloads/gimp-2.5.deb").

Thanks for the DEB. :).

---

### Post by zeronet on 2008-06-01
> Just wanted to offer another option for downloading it.

Download link.

Thanks for the DEB. 

Thank you for the mirror, added to the first post.

---

### Post by altonbr on 2008-06-02
Just announcing that it works for me on Hardy. Thank you!

---

### Post by tuggy on 2008-07-03
2.5.1 is out now!
can we see a deb around here? :) :)

---

### Post by lyceum on 2008-07-03
> **zeronet said:**
> Well, a friend had some issues with his wacom tablet with Hardy GTK and Gimp 2.4, so I´ve compiled Gimp 2.5.0 myself and made a deb 

What is the difference between the two in regards to the Wacom? I just got mine to work yesterday, but the pen is not pressure sensitive, I know there are different how-tos out there but haven't had time to work with them yet. Does this fix that?

---

### Post by olskar on 2008-07-03
> **tuggy said:**
> 2.5.1 is out now!
can we see a deb around here? :) :)

You can try this, dont know if it works

[http://in.solit.us/archives/show/146113](http://in.solit.us/archives/show/146113)

---

### Post by zeronet on 2008-07-03
> 
2.5.1 is out now!
can we see a deb around here? 

> You can try this, dont know if it works

[http://in.solit.us/archives/show/146113](http://in.solit.us/archives/show/146113)

Yes, a friend of mine (Gadi) has uploaded it, but I´m using Debian Lenny now, so I don´t know if it works on Ubuntu Hardy, it´s the same link posted by olskar, PLEASE TEST IT AND TELL ME IF IT WORKS ON UBUNTU HARDY!

[http://in.solit.us/archives/show/146113](http://in.solit.us/archives/show/146113)

---

### Post by olskar on 2008-07-04
I got it to work :)

---

### Post by zeronet on 2008-07-04
> I got it to work 

Great, thank you, I´m going to add the 2.5.1 deb on the first page!

---

### Post by phildaman46 on 2008-07-08
Missing dependency, libpango1.0-0 (>= 1.20.2). Where can I get it?

---

### Post by jeffegg2 on 2008-07-26
I am using the amd64 version of ubuntu, I guess the .deb files do not work with this. Can anyone tell me how to install this?

---

### Post by darkerlink on 2008-07-28
> **jeffegg2 said:**
> I am using the amd64 version of ubuntu, I guess the .deb files do not work with this. Can anyone tell me how to install this?

I got it to work with AMD64. You need to force the architect. First, install the 32 bit libraries with getlib.

```

getlibs -p gimp-2.5.deb
```

If gimp is on your desktop,make sure to cd Desktop first.

Then force the package to install.

```
sudo dpkg -i --force-all gimp-2.5.deb
```

You should now have gimp 2.5 install. I ran into problems with libdbus-1.so.2 so I fixed that by installing that library with

```
getlibs -l libdbus-1.so.2
```

run gimp-2.5 in the terminal or from the applications list and it should work. Hope this helps.

---

### Post by ragingmon on 2008-09-25
Can anyone upload 2.5.1 again?
The download link for it is broken

---

### Post by Neon Lights on 2008-09-25
2.5.4 is out though, why are you asking for 2.5.1? o.O

---

### Post by Black16V on 2008-09-25
Could someone Build 2.5.4 deb Package for Hardy?

---

### Post by altonbr on 2008-09-26
> **Black16V said:**
> Could someone Build 2.5.4 deb Package for Hardy?

Try [https://launchpad.net/~c-korn/+archive](https://launchpad.net/~c-korn/+archive). Works for me.

---

### Post by binbash on 2008-09-27
> **altonbr said:**
> Try [https://launchpad.net/~c-korn/+archive](https://launchpad.net/~c-korn/+archive). Works for me.

Thanks for the repo link.It is working fine

---

