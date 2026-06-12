---
title: "I need WoW and Ventrilo Help with ubuntu"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by jejaxon on 2008-01-21
Hey guys,
Im newer to Linux and ubuntu. I decieded to use it because I am so sick of windblows. My only problem is that I like to game. I play WoW and other games while also on ventrilo. Ive seen youtube videos of people playing WoW and running ventrilo perfectly while in ubuntu. I am trying to figure out how they do this because I have gone through so many howto's and I am having a very hard time. I got my WoW to where it opens but it doesnt show any background and it basically freezes the machine. I havent even got anywhere on ventrilo yet because I have not seen many howto's on it. Here is what I am running:

Ubuntu Feisty Fawn (7.04)
Beryl
ATI x850XT pci-e (not sure on driver)
AMD 3XXX+ 64bit 2.2Ghz
1 gig ram

I am hoping someone might be able to get me off on the right track so I can better enjoy this OS. Once again I am new to Linux so please try to be very detailed on what to do so I wont have problems. Thanks!!

---

### Post by Kilz on 2008-01-21
> **jejaxon said:**
> Hey guys,
Im newer to Linux and ubuntu. I decieded to use it because I am so sick of windblows. My only problem is that I like to game. I play WoW and other games while also on ventrilo. Ive seen youtube videos of people playing WoW and running ventrilo perfectly while in ubuntu. I am trying to figure out how they do this because I have gone through so many howto's and I am having a very hard time. I got my WoW to where it opens but it doesnt show any background and it basically freezes the machine. I havent even got anywhere on ventrilo yet because I have not seen many howto's on it. Here is what I am running:

Ubuntu Feisty Fawn (7.04)
Beryl
ATI x850XT pci-e (not sure on driver)
AMD 3XXX+ 64bit 2.2Ghz
1 gig ram

I am hoping someone might be able to get me off on the right track so I can better enjoy this OS. Once again I am new to Linux so please try to be very detailed on what to do so I wont have problems. Thanks!!


Open a terminal and type
```
sudo apt-get install wine
```
[Then go here.]("http://appdb.winehq.org/appview.php?iVersionId=6482")

---

### Post by JoshuaRL on 2008-01-21
To find your driver:
```

sudo gedit /etc/X11/xorg.conf

```

As far as the rest, I'm not sure on all of it.  I know what WoW is, and I believe that WINE supports it really well.  So your best bet there is to go to the WINE site and follow their directions.  [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Also, with Feisty Beryl and Compiz were separate.  Since then they have merged.  Now if you download comiz in Gutsy you'll get more than Cube and wobbly windows.  In fact, that might be your problem.  I'm just not sure that Beryl is still supported.

As far as Ventrillo, I haven't used it.  I had to go to Google to find out what it was.  Does it work if you aren't the server?

---

### Post by JoshuaRL on 2008-01-21
> **Kilz said:**
> Open a terminal and type
```
sudo apt-get install wine
```
[Then go here.]("http://appdb.winehq.org/appview.php?iVersionId=6482")

That works well if you have a simple or old program, but if you want the most up-to-date WINE and all that it supports, you need to go to the site instead since the one in the repos is an older build.

---

### Post by jejaxon on 2008-01-21
yes, I forgot to mention that I am using WINE and have it all installed and stuff. I followed the steps on their site but it still gives me problems.

---

### Post by JoshuaRL on 2008-01-21
What kind of problems?

---

### Post by jejaxon on 2008-01-21
video problems. will open and it will show account name and password but thats it. then the whole thing freezes. Im going to uninstall ubunti 7.04 and get 7.10 and see if i can do any better with that

---

### Post by JoshuaRL on 2008-01-21
Cool.  Come back if you still have problems.  But I really suggest you install the latest version of Wine.  It will work better because it's under constant development.

---

### Post by Zaare on 2008-01-21
Have you read this [howto]("http://ubuntuforums.org/showthread.php?t=579378")? It worked just fine for me. I have not figured out how to install Ventrilo yet. Their site states that a Linux version is under development, so even if it doesn't help at this very moment, we will have it in a near future.

---

### Post by jejaxon on 2008-01-21
Yeah I tried that one. I am using Wubi. It installed Linux on my Hard Drive without me having to repartition anything. When Im logged in I can access the WoW on my windows drive but I was wondering if i should copy that over to my Ubuntu drive and see if it works. Ill try it after im done reinstalling.

---

### Post by JoshuaRL on 2008-01-21
Yeah, you should install it again through Wine.  It'll make sure it installs it correctly for Wine to be able to handle it correctly.

---

### Post by gletob on 2008-01-21
Wubi's great it started me with ubuntu but the live cd is extremely easy to use and my only problem with wubi is if I shut down wrong or something Wubi stopped working so I think you should install with the CD.  If you decide to install PM me with question and I'll help you with partitioning and such.

---

### Post by Dreamlocked on 2008-01-21
No need to reinstall anything, you're probably experiencing a graphics driver problem.
I've been experiencing this problem too with recent ATI drivers (for 3-4 months now, I think).

To fix this, open your Config.wtf file in the WTF folder of your World of Warcraft installation, and add the line :
```

SET M2UseShaders "0"

```

---

### Post by jejaxon on 2008-01-22
UPDATE

Ok so I found an old hard drive and I installed Linux 7.10 on it. Everything is good right now but the video drivers. Wine is working but my video drivers are all messed up. It keeps running me at a very low resolution and Ive installed drivers but every time I reboot after they install it tells me I need to run in low graphic mode or something like that. Ive tried Envy already and that did not work either.  I run an ATI x850XT PCIE card. Any help would be great.

thanks!

---

### Post by JoshuaRL on 2008-01-22
Alright, first of all try:
```

sudo dpkg-reconfigure xserver-xorg

```

That will attempt to reconfigure your xserver settings.  If that doesn't work we can try manually setting it up right.

---

### Post by jejaxon on 2008-01-22
Ok, I tried that this morning but nothing changed. Do I have to restart the system? I was in the middle of a long download so I didnt do it. I saw no graphic changes after I went through the process.

---

### Post by JoshuaRL on 2008-01-22
No, you shouldn't.  But just to be sure, hit Ctrl+Alt+Backspace.  That will restart Xserver.  If that doesn't work, we'll need to manually adjust the drivers.

---

### Post by jejaxon on 2008-01-22
Not working bro... 

joe@joe:~$ glxinfo | grep rendering
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

### Post by JoshuaRL on 2008-01-22
Alright.  Could you post the output of:

```

sudo gedit /etc/X11/xorg.conf

```

That will let us see the configuration file for Xserver.

---

### Post by jejaxon on 2008-01-22
made new post

---

### Post by JoshuaRL on 2008-01-22
Cool, I'm there.  You might want to mark this as solved though, since you've moved on.

---

### Post by dutchman72 on 2008-04-13
Their site says a Linux version is in dev, but dig further into that info and he states clearly he wants to keep the source closed and linux would force it to be open. He has NO plans to make a linux client for Ventrilo.

---

