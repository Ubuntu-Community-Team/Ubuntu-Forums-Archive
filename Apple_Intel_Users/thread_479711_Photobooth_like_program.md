---
title: "Photobooth like program"
date: 2007-06-20
forum: Apple Intel Users
---

### Post by ivesjd on 2007-06-20
Does anyone know of a photobooth like program for Ubuntu? I got my iSight working and was wondering if anyone had seen anything like photobooth.


****EDIT>   [Here ]("http://ubuntuforums.org/showthread.php?t=486722")it is. </EDIT*****

---

### Post by kzm. on 2007-06-20
while we are asking this questions.. i would rather like to know if there is an app for ubuntu capable doing what quicksilver is

[http://en.wikipedia.org/wiki/Quicksilver_(software](http://en.wikipedia.org/wiki/Quicksilver_(software))

---

### Post by ivesjd on 2007-06-20
> **kzm. said:**
> while we are asking this questions.. i would rather like to know if there is an app for ubuntu capable doing what quicksilver is

[http://en.wikipedia.org/wiki/Quicksilver_(software](http://en.wikipedia.org/wiki/Quicksilver_(software))
Katapult is the launcher I use, it doesnt have all the functionality of quicksilver, but it still does the basic app launching.

---

### Post by kzm. on 2007-06-20
i saw how you could chain a whole bunch of programms and actions like selecting files, resizeing them, select a contact and send them the images. that was amazing.. anything out there like this?

---

### Post by ronocdh on 2007-06-20
> **ivesjd said:**
> Katapult is the launcher I use, it doesnt have all the functionality of quicksilver, but it still does the basic app launching.
Awesome, thanks for the recommendation. From the [screenshots]("http://katapult.kde.org/screenshots"), it looks like a pretty close copy of Quicksilver. Too bad I hate KDE. ;)

---

### Post by ivesjd on 2007-06-20
> **ronocdh said:**
> Awesome, thanks for the recommendation. From the [screenshots]("http://katapult.kde.org/screenshots"), it looks like a pretty close copy of Quicksilver. Too bad I hate KDE. ;)
Im quite sure you know, that it will run in gnome.

---

### Post by ronocdh on 2007-06-20
> **ivesjd said:**
> Im quite sure you know, that it will run in gnome.
Yes of course, it was more of an underhanded burn. I'll be the first to admit that some of my favorite software is designed with KDE in mind... but I then, I *have* heard people defend Rhythmbox over Amarok! Thanks again for the rec, this is exactly what I've wanted.

---

### Post by kzm. on 2007-06-21
it looks like katapult is not working under compiz.. next to having a shadow around the transparent area of the icon the key shortcuts are lost.. anybody knows how to fix?

---

### Post by ivesjd on 2007-06-21
I've got no idea about compiz, I use beryl and it is fine. You could try messing with the different rendering settings, or the look of Katapult itself.

---

### Post by ronocdh on 2007-06-21
> **kzm. said:**
> it looks like katapult is not working under compiz.. next to having a shadow around the transparent area of the icon the key shortcuts are lost.. anybody knows how to fix?
I agree with ivesjd, use Beryl. I fail to see any advantages of Compiz over Beryl, except maybe that it doesn't require much configuration. Not try to start a flamewar! But try out Beryl if you're at all interesting in desktop effects.

---

### Post by ivesjd on 2007-06-24
Ya, so now I'm using compiz. Well, compiz fusion, I like it alot. The config menu is so much nicer. I'm just frusterated with the way katapult works in it. Oh well. ATM Im kinda ubuntued out. Spent two days trying to get my macbook to boot right into compiz fusion and it just wont do it.

---

### Post by ivesjd on 2007-06-25
So I think I finally found something like Photobooth. Its called cheese. Im working on installing it right now. Heres the link:) [http://live.gnome.org/Cheese](http://live.gnome.org/Cheese)

---

### Post by ronocdh on 2007-06-25
> **ivesjd said:**
> So I think I finally found something like Photobooth. Its called cheese. Im working on installing it right now. Heres the link:) [http://live.gnome.org/Cheese](http://live.gnome.org/Cheese)
Ah! I knew this thread would be fruitful! Ubuntu Community comes through again, hurray! I'll work on installing that this week. (I never bothered to set up my webcam at all.)

---

### Post by ivesjd on 2007-06-25
> **ronocdh said:**
> Ah! I knew this thread would be fruitful! Ubuntu Community comes through again, hurray! I'll work on installing that this week. (I never bothered to set up my webcam at all.)

I tried installing it and just can't get it. It seems to be a strange install process. And there doesn't seem to be much documentation on it. Other then the readme file.

---

### Post by ronocdh on 2007-06-25
> **ivesjd said:**
> I tried installing it and just can't get it. It seems to be a strange install process. And there doesn't seem to be much documentation on it. Other then the readme file.
I laughed. Yay open source! I found [the thread you used]("http://ubuntuforums.org/showthread.php?t=225621") to configure your iSight. I was going to set mine up with that and go from there. Perhaps our hardware is different enough that we'll have different experiences? Who knows. I'll post back later on about it.

---

### Post by cyberdork33 on 2007-06-26
I got it to compile...

dependencies: ( I think this gets them all)
```
sudo aptitude install build-essential libdbus-1-dev libgtk2.0-dev libglade2-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libgnome-vfs-dev libgnome-vfsmm-2.6-dev
```

then just run 'make' in the source directory.

While still in the cheese directory:
  - copy cheese somewhere in your PATH (/usr/bin)
```
sudo cp cheese /usr/bin/cheese
```
  - copy cheese/cheese.desktop to /usr/share/applications
```
sudo cp cheese.desktop /usr/share/applications/cheese.desktop
```
  - copy cheese/cheese.glade to /usr/share/cheese
```
sudo mkdir /usr/share/cheese
```
```
sudo cp cheese.glade /usr/share/cheese/cheese.glade
```
  - install cheese/po/$lang.mo as /usr/share/locale/$lang/LC_MESSAGES/cheese.mo
Only German? There are only a few translations. Only have to copy these if you need something other than English.
Example:
```
sudo cp po/de.mo /usr/share/locale/de/LC_MESSAGES/cheese.mo
```

After moving the various files around, I get errors that the cheese.glade file isn't found
I can launch cheese as long as the cheese.glade file is in the directory I launch from, but then no video. This is gonna take some work.

---

### Post by ivesjd on 2007-06-26
> I can launch cheese as long as the cheese.glade file is in the directory I launch from, but then no video. This is gonna take some work.
If/when you get it working, a short how-to would be awesome. I have yet to get it to compile. :/
And the cheese website says translations are in progress. I just read into there site abit more, I think they started on this april 21st!

---

### Post by ivesjd on 2007-06-26
> **kzm. said:**
> it looks like katapult is not working under compiz.. next to having a shadow around the transparent area of the icon the key shortcuts are lost.. anybody knows how to fix?
I figured out how to get it to work. Open ccsm and go to the window decerations menu.
And for shadow windows put in none instead of any. As far as I can see, most windows still have shadows, but katapult doesn't! Im sure you could do other options but I didnt care enough about shadows to mess with it.

---

### Post by cyberdork33 on 2007-06-26
ok, fixed the glade error. The second line in the window.h ... if you comment that one out, and uncomment the third line (that specifies where the readme says to put the file) then compile. 

Now the application starts, but no video showing. I know the iSight is working because I can run ekiga, as well as the raw gstreamer test (as found in the iSight thread). Can someone else try to compile and run?

you can get the latest source by using darcs (install first) as shown on the application's page which has a couple more translations as well:
[http://live.gnome.org/Cheese](http://live.gnome.org/Cheese)

all you have to do is install all the dependencies (I posted the line in a previous post to do this) and then run make in the source directory for cheese. then you have to copy all the files all over your machine as stated in the README as well.

---

### Post by ivesjd on 2007-06-26
> **cyberdork33 said:**
> ok, fixed the glade error. The second line in the window.h ... if you comment that one out, and uncomment the third line (that specifies where the readme says to put the file) then compile. 

Now the application starts, but no video showing. I know the iSight is working because I can run ekiga, as well as the raw gstreamer test (as found in the iSight thread). Can someone else try to compile and run?

you can get the latest source by using darcs (install first) as shown on the application's page which has a couple more translations as well:
[http://live.gnome.org/Cheese](http://live.gnome.org/Cheese)

all you have to do is install all the dependencies (I posted the line in a previous post to do this) and then run make in the source directory for cheese. then you have to copy all the files all over your machine as stated in the README as well.
Okay sounds good, I'll give it a try later tonight (I hope).

---

### Post by ivesjd on 2007-06-27
Okay, I tried it again, but I think I'm missing some dependencies. And I have no idea which ones. Kinda new to the whole compiling thing. If you could add to your list of dependencies, all of the dependencies, I will gladly try again.

---

### Post by cyberdork33 on 2007-06-27
well all the dependencies are listed in the README... but they can be named weird in the repositories. I should have added the "build-essentials" package as well if you have not compiled anything yet on your machine.

If you still get a compile error, just look at the first error and try to determine what dependency it belongs to...

I fixed the dependencies command... should be copy and paste now.

---

### Post by ivesjd on 2007-06-27
> **cyberdork33 said:**
> well all the dependencies are listed in the README... but they can be named weird in the repositories. I should have added the "build-essentials" package as well if you have not compiled anything yet on your machine.

If you still get a compile error, just look at the first error and try to determine what dependency it belongs to...

I fixed the dependencies command... should be copy and paste now.
I have compiled before. But usually with a guide. So I did have build-essential installed.
I found the first error (the very first line>_<) "Package gstreamer-0.10 was not found in the pkg-config search path." I do have the package installed. Any ideas?

---

### Post by cyberdork33 on 2007-06-27
OK, ivesjd helped me out a bit, and I got it working. Once you get it compiled and all the files thrown in every which direction, then you can run:
```
$ gstreamer-properties
```
and on the video tab, 
1. make sure that Video for linux 2 (v4l2) is selected in the Plugin dropdown box, and 
2. Built-In iSight is selected in the Device dropdown box. 

Then cheese should use the iSight by default!

The icons are not showing up on the effects page for some reason... I think the images need to moved somewhere. If you run the compiled binary in the source package folder, then you can see them.

---

### Post by ivesjd on 2007-06-27
Just as he got it working last night, my iSight quit working. Now I'm getting the 
```
 uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp: 26).
``` But only when I try to run cheese. The gstreamer test works fine as does ekiga. I'm at a loss. If I start the gstreamer test, and then start cheese. Cheese will start with a gray screen. I've done both, reinstalled the iSight and recompiled and reinstalled cheese all to no avail. Anyone have an idea?

---

### Post by cyberdork33 on 2007-06-27
I tried to use a usb webcam last night once (which didn't work with v4l2, just v4l), but when I changed the gstreamer-properties, it really got things screwy and broke the iSight. I couldn't get settings to stick unless I rebooted each time I changed something. I was getting lots of weird errors like that when trying to use the iSight until I got all the settings changed back to what they were supposed to be. Don't know if this helps...

---

### Post by ivesjd on 2007-06-28
Well, I'm not getting that error anymore. Ive uninstalled and recompiled cheese and now I'm not getting any errors, but it still crashes. I can get cheese to start if I do the gstreamer test first. But its the gray screen. Im gonna try to compile the "release" version see if that helps at all. When I compiled today, they had a few more languges in.

---

### Post by cyberdork33 on 2007-06-28
Those languages were included in the final package I compiled... (at least I think they all were... there were 3 or 4 or so I know).

Did you finally get iSight to show up in the gstreamer properties?

The grey screen is what i was getting everytime until you tipped me off to set the default video device in the gstreamer-properties dialog.

I also posted a full howto  thread here:
[http://ubuntuforums.org/showthread.php?t=486722](http://ubuntuforums.org/showthread.php?t=486722)

---

### Post by ivesjd on 2007-06-28
Ya, I saw the how-to. I do have the iSight in gstreamer-properties. But cheese keeps crashing. There is nothing in dmesg. I tried the release version (even though it was only 3 days ago) and all I'm getting is this:
The program 'cheese' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 44 error_code 11 request_code 141 minor_code 19)
I've only seen this type of error with cheese. I'm gonna poke around the net and see if I can find anything on it.

---

### Post by cyberdork33 on 2007-06-28
might want to poke around in /var/log and see if there is something in another log file. Actually, looking around, it sounds like an Xorg related error, so might check the xorg log file.

EDIT: I am guessing this is related to the gdk requirement... You may have gotten the dev package for compiling, but it needs the binary package to actually run stuff... I must have had that one for some reason already.

---

### Post by cyberdork33 on 2007-07-02
[B][SIZE=3]For those that are interested in cheese, please see this thread:
[http://ubuntuforums.org/showthread.php?t=486722](http://ubuntuforums.org/showthread.php?t=486722)
[/SIZE][/B]

---

