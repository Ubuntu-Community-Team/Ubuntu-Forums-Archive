---
title: "Porblems playing DVDs"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by poordamnedfool on 2008-01-24
I have installed all of the extras and codes but i still cannot get totem to play dvds or vlc for that matter.  the error that comes up is:

"An error occurred"
"Could not open location; you might not have permission to open the file."

any ideas?

---

### Post by gvartser on 2008-01-24
Maby this post will help:

[http://ubuntuforums.org/showthread.php?t=406688](http://ubuntuforums.org/showthread.php?t=406688)

/g

---

### Post by stchman on 2008-01-24
> **poordamnedfool said:**
> I have installed all of the extras and codes but i still cannot get totem to play dvds or vlc for that matter.  the error that comes up is:

"An error occurred"
"Could not open location; you might not have permission to open the file."

any ideas?

You need the CSS decoder.

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

---

### Post by gunksta on 2008-01-24
Make sure you have the following packages installed:

[LIST]
[*]libdvdnav4
[*]libdvdread3[/LIST]Without these, you can't read DVDs. There is also the dreaded fact that DVDs are encrypted. I'm not sure if the libdvdread3 will let you read encrypted DVDs or not. So, make sure you have these two installed first.

If things still don't work. Go to:
[http://www.videolan.org/developers/libdvdcss.html](http://www.videolan.org/developers/libdvdcss.html)

And download libdvdcss. This useful little library (not in the repos) will allow you to decrypt the DVDs. But, you may not need it these days. I've had it on my system for years and I haven't tried removing it in many many moons so try without it first.

---

### Post by wolfen69 on 2008-01-24
while you are at it, install the medibuntu repos too. [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Dumpy Dumpster on 2008-01-24
As a newbie, I was advised to install VLC player, I did and all has worked well since!

---

### Post by mocoloco on 2008-01-24
Here's what I think is the cleanest way, no changing sources or getting libdvdcss2 from questionable places. Also it's from a [page on the official Ubuntu Wiki]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs").
```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
```
The libdvdread3 package includes a shell script that will download and install [libdvdcss2]("http://en.wikipedia.org/wiki/Libdvdcss2").  Run that with
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

VLC is great but I like Totem better for DVD playback, it gives me gui controls full screen, better menu handling, etc.  BUT you have to install totem Xine, which is done with the above code.
I do however use VLC to play dvd videos from an ISO file, so I can put my movies on a hard drive and not have to swap discs.

---

### Post by cjm5229 on 2008-01-24
Once you get all the codecs installed, get Ogre, It's in the repos, It's a great player for DVD's with full Menu support. for the codecs make sure you have the medibuntu repos installed.    	 	 	 	 	 	  deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free  
 wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

---

### Post by diddler on 2008-01-24
[QUOTE=mocoloco;4199316]Here's what I think is the cleanest way, no changing sources or getting libdvdcss2 from questionable places. Also it's from a [page on the official Ubuntu Wiki]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs").
```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
```
The libdvdread3 package includes a shell script that will download and install [libdvdcss2]("http://en.wikipedia.org/wiki/Libdvdcss2").  Run that with
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Brilliant.  Worked like a charm!  EXCEPT . . . I cannot get any English dialog!  I get Music, I get sound effects, I get Spanish and French dialog.  I even get sub-titles.  But NO English dialog!  Any suggestions?

---

### Post by poordamnedfool on 2008-01-25
Thanks for all the help. i will try these out when i get back to my gf's moms computer.

---

### Post by diddler on 2008-01-27
I finally downloaded VLC and it plays the DVD WITH English dialog.  NOW, how do I make it my default rather than Totem?

---

### Post by gvartser on 2008-01-28
From a terminal:

type


```
gconf-editor
```

Click on the arrow to Expand Desktop

then

Click on the arrow to Expand Gnome

Then click on Volume Manager

Look for autoplay dvd command on th right side of the screen
Double Click

The value should be

totem %M

change it to

/usr/bin/vlc dvd://


same thing for VCD

/usr/bin/vlc vcd://

/g

---

### Post by mocoloco on 2008-01-28
Thanks gvartser.  Didn't know you could also set VCD prefs.  
If you don't care about VCD there's a GUI way to set DVD prefs:
System > Preferences > Removable Drives and Media
Click the **Multimedia** tab
I think you can change "totem %m" to "vlc %m", if that doesn't work do "vlc dvd://" as gvartser suggested.

Incidentally, very strange that English dialog won't work for you.  I assume you tried more than one DVD?  Some discs don't use the "standard" way of defining audio or subtitle tracks, maybe totem just had an issue with that one title?
Either way, glad you found a solution.  Hopefully poordamnedfool resolved the issue also.

---

### Post by diddler on 2008-01-28
> **mocoloco said:**
> 
Incidentally, very strange that English dialog won't work for you.  I assume you tried more than one DVD?  Some discs don't use the "standard" way of defining audio or subtitle tracks, maybe totem just had an issue with that one title?
Either way, glad you found a solution.  Hopefully poordamnedfool resolved the issue also.

Yes I tried more than one DVD and even more than one DVD drive.  For some reason, Totem will not read audio track 1 which is normally the English.  As a side note, Ubuntu as a whole doesn't like my Plextor drive, but oddly enough, really works well with my older Sony.  I am about to try to change the default for DVD playing, we will see what happens.

---

### Post by diddler on 2008-01-28
Worked great.  Thanks a bunch.  I have been finding all sorts of menus that are actually useful but it has taken me a while to forget Windowsspeak and understand why Ubuntu calls things what they call them.  It has been a journey, and not always smooth. Now if I could just figure out how to get Ubuntu to remember my screen reolution, I will consider the week well spent.

---

### Post by gunksta on 2008-01-30
> **diddler said:**
> Worked great.  Thanks a bunch.  I have been finding all sorts of menus that are actually useful but it has taken me a while to forget Windowsspeak and understand why Ubuntu calls things what they call them.  It has been a journey, and not always smooth. Now if I could just figure out how to get Ubuntu to remember my screen reolution, I will consider the week well spent.



If nothing else works, hand-edit your xorg.conf file and remove ALL of the screen resolutions except the one that you want to use. I'm sure there are some good explanations on the forum to tell you how to edit this file in detail. It's located @

/etc/X11

---

### Post by diddler on 2008-01-31
Well, editing the xorg.conf didn't do anything but disable my restricted drivers, HOWEVER, reloading the restricted drivers caused the system to default to the desired resolution!  Go figure.

---

### Post by gunksta on 2008-01-31
Well, I can't say I understand, but I'm glad it worked out for you.

---

