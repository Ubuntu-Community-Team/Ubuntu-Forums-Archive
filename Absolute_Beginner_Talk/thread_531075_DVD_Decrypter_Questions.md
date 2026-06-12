---
title: "DVD Decrypter Questions"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by frostbytes on 2007-08-21
Hey all, I use DVD Decrypter on my machine.  All the movies that I hsave ripped lately have been 7+ gigs.  If anyone out there knows what setting I have wrong so that I can get them below 4.7 gigs, I would appreciate it.  Thanks!

---

### Post by johnlm on 2007-08-21
If you are just ripping them, then they will come out to this size, as they are usually on a dual layer disc (about 8gb). When I did this in my XP days I used DVD shrink to get it onto a single layer disc (about 4gb). If anyone knows of an Ubuntu equivalent that would be useful.

---

### Post by HotShotDJ on 2007-08-21
k9Copy works a treat.

---

### Post by C.S.Cameron on 2007-08-21
Try DVD Shrink with Wine.

---

### Post by hyper_ch on 2007-08-21
I also use dvd shrink in wine :)

---

### Post by frostbytes on 2007-08-21
thanks every1!

---

### Post by Amazona aestiva on 2007-08-22
You can also see my signature!

---

### Post by stchman on 2007-08-22
> **frostbytes said:**
> Hey all, I use DVD Decrypter on my machine.  All the movies that I hsave ripped lately have been 7+ gigs.  If anyone out there knows what setting I have wrong so that I can get them below 4.7 gigs, I would appreciate it.  Thanks!

DVD Decryptor is a DVD ripping program only.  It does not recode to fit a 4.7GB disc.  Use K9Copy as it rips and recodes.

---

### Post by frostbytes on 2007-08-22
alight thanks for that man, i was unaware...thanks for the response!

---

### Post by kornface13 on 2007-08-26
I know that you can burn .iso files by using Ubuntu's default burning program (dragging the file to the blank CD), but it doesn't work for .img files.  I'm going to try using DVD Decryptor with wine.  Anyone else have success with that combination?

---

### Post by HotShotDJ on 2007-08-26
There is no reason to use a Windows application under WINE for ripping and/or shrinking DVD's.  The native Linux applications such as K9Copy work perfectly.

---

### Post by hyper_ch on 2007-08-27
whats wrong about using the best application for a given task?

---

### Post by claytor on 2007-10-26
I tried using K9copy, but 30 seconds into the Authoring, it stops and gives this error msg:

An error occured while running DVDAuthor:

I tried a few times, and the settings seem to be correct.  I notice it is a KDE app, and I am using Gnome.  Could that be the problem?  I am going to continue searching forums...

---

### Post by Drakkor on 2007-10-26
Re: shrinking

---

### Post by jusmurph on 2007-10-26
> **claytor said:**
>  I notice it is a KDE app, and I am using Gnome.  Could that be the problem?

I would like to know the answer to that too..

---

### Post by Drakkor on 2007-10-26
No,coz I use gnome and it works perfectly :)

---

### Post by CSMatt on 2007-10-26
The Qt toolkit should download automatically the first time you download a KDE program from the repositories.  I believe all GNOME and Xfce programs have a GTK+ dependency and all KDE stuff has a Qt dependency.

---

### Post by claytor on 2007-10-26
i just switched to KDE, and I got the exact same error within 30 seconds of Authoring...

---

### Post by CSMatt on 2007-10-26
It's probably something with dvdauthor then.  I've often found myself to have dvdauthor problems as well if I ever try to author a disc from a video file, usually because of something trivial like the absence of a semicolon or the presence of incompatible characters in the disk label.  Sadly the error messages aren't that helpful in and of themselves, but entering them into search engines and asking the program's author for support does help most of the time.

---

### Post by Hallvor on 2007-10-26
I did have some problems of my own with K9copy crashing (with Gnome). It was also the only KDE application I used, so I needed the KDE libraries as well. 

Fortunately, I found a great application called dvd9 to 5, which shrinks the dvd like dvdshrink. It is in the synaptic package manager.

Edit: Screenshot

[IMG]http://dvd95.sourceforge.net/images/Capture-DVD%209%20to%205-1.png[/IMG]

---

### Post by claytor on 2007-10-26
Installed 9TO5.  Read the disc fine, but when I went to make the iso, it told me:

Read Error!  Ignore all read errors?

I chose no, and it stopped making the iso.  I restarted the program and chose to ignore the errors.  It started creating the iso at around 2X, then stopped at 1% finished and crashed.  I cleaned the disc (very clean, no scratches) and tried again.  Same issue.

Could it be a protection issue?  Do I need an linux-equivalent anydvd app?

---

### Post by Hallvor on 2007-10-26
I may be way off here, but do you have vobcopy installed? (In the synaptic package manager.) If not, install it and then run dvd9to5 again.

---

### Post by spyderone on 2007-10-26
You could also try 

[http://dvdshrink.sourceforge.net/](http://dvdshrink.sourceforge.net/)

and

[http://www.exit1.org/dvdrip/](http://www.exit1.org/dvdrip/)

---

### Post by claytor on 2007-10-27
> **Hallvor said:**
> I may be way off here, but do you have vobcopy installed? (In the synaptic package manager.) If not, install it and then run dvd9to5 again.

Installed, still get the same error...

> **spyderone said:**
> You could also try 

[http://dvdshrink.sourceforge.net/](http://dvdshrink.sourceforge.net/)

and

[http://www.exit1.org/dvdrip/](http://www.exit1.org/dvdrip/)

Heh, both those gave me issues too...

---

### Post by Kalifornia909 on 2007-10-27
i get a mkisofs is missing error in dvd 9-5. can anyone help me out here

---

### Post by dwhitney67 on 2007-10-27
install cdrtools for mkisofs

---

### Post by Kalifornia909 on 2007-10-27
is that in the default repos or do i have to manually install

---

### Post by dwhitney67 on 2007-10-28
beats me... just do a google search.

---

### Post by Hallvor on 2007-10-28
Just in case. Did you install dvd read capability?
```

sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by claytor on 2007-10-29
Yes libdvd3 is installed.

---

### Post by Hallvor on 2007-10-29
Do you get the same read error with other DVDs as well? Some copy protection mechanisms give a ton of read errors to make it difficult to backup the DVD.

---

### Post by Mud.Knee.Havoc on 2007-10-30
> **claytor said:**
> Yes libdvd3 is installed.

But did you run the script that Hallvor posted?

---

### Post by claytor on 2007-11-09
Sorry I haven't got back to you guys...

I got DVD9to5 working fine.  That script did the trick.

Thanks for all the help!!!

---

