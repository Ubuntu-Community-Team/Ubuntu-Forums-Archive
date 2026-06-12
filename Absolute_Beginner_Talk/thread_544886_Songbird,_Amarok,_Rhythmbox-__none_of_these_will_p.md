---
title: "Songbird, Amarok, Rhythmbox-  none of these will play WMAs! What do I need to do!"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by acelin on 2007-09-06
Songbird, Amarok, Rhythmbox-  none of these will play WMAs! What do I need to do?!!!

---

### Post by sumguy231 on 2007-09-06
You need to add the Medibuntu repository and install the w32codecs package:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by acelin on 2007-09-06
Thanks- I really like songbird-i use it vista all the time- but I want to stop using vista and only use ubuntu!

---

### Post by reckless2k2 on 2007-09-06
TMI bro.......just follow the info in the sumguy231 post and mark the thread as solved already.

hahahahaha...just kidding....i'm only trying to boost my post numbers. hahaha

---

### Post by SOULRiDER on 2007-09-06
You should keep the link to thsi guide, you may need it int he future with other formats.
[https://help.ubuntu.com/community/Beginners/Guide/Feisty/Multimedia](https://help.ubuntu.com/community/Beginners/Guide/Feisty/Multimedia)

---

### Post by acelin on 2007-09-06
How do I add medibuntu to the sources list? whhere would i find its deb?

---

### Post by SOULRiDER on 2007-09-06
Youre running Feisty so it should be:
```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

All the info is here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) but ask any questions you want.

---

### Post by acelin on 2007-09-06
non eof these are working...

---

### Post by acelin on 2007-09-06
Can someone give me step by step instructions? I am really new to Linux in general- I have it for forever, just havent used it much-

---

### Post by SOULRiDER on 2007-09-06
Press alt + f2 and type
```
gksu gedit /etc/apt/sources.list
```
At the bottom of the file add:
```
deb http://packages.medibuntu.org/ feisty free non-free
```

Save the file and opena  Terminal, **Applications > Accessories > Terminal ** and paste this:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
Oce its done type:
```
sudo apt-get install w32codecs
```

Now WMA files should work!

---

### Post by ubuntu27 on 2007-09-06
Ok, here is the step by step instructions:
First, Make sure you know what version of UBuntu you are running. Your profile says you are running Ubuntu 7.04 (Feisty Fawn), is that correct? NOw, here is an important question, **Did you install Ubuntu 32bit or 64bit ? **

Then let's do the following:

Step 1 - Add the Mediabuntu repository.

I will give you [Terminal]("http://www.psychocats.net/ubuntu/terminal") commands in which you only have to Copy&Paste. To Open the Terminal, just go to Applications/Accessories/Terminal.

Press "enter" after each command.. You will be asked for [your password]("http://www.psychocats.net/ubuntu/passwordinterminal"), type your password and pres enter again.

```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Step 2 - Install library designed for accessing DVD

Open the [Termina]("http://www.psychocats.net/ubuntu/terminal")l and type (or copy and paste):

```
sudo aptitude install libdvdcss2
```

Step 3 - Install Win32Codecs

Type this if you are using Ubuntu **32bit**
```
sudo aptitude install w32codecs
```

Type this if you are using Ubuntu **64bit**
```
sudo aptitude install w64codecs
```

That's it :)

For more info, please follow 

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by acelin on 2007-09-06
Songbird stil wont pick up those WMA's!!

---

### Post by sloggerkhan on 2007-09-06
I thought songbird is based on gstreamer and vlc I think... 
see [http://publicsvn.songbirdnest.com/wiki/SettingUpGStreamer](http://publicsvn.songbirdnest.com/wiki/SettingUpGStreamer)

---

### Post by acelin on 2007-09-06
Any thoughts on what to do?

---

### Post by sloggerkhan on 2007-09-07
Did you look at the webpage and have installed all gstreamer package via synaptic after having added medibuntu?

[http://www.yolinux.com/MIME-EXAMPLES/WMV-VideoAppletTest.html](http://www.yolinux.com/MIME-EXAMPLES/WMV-VideoAppletTest.html) is a test for .wmv
If songbird is using gstreamer, and it plays in my browser using totem-gstreamer, I think the right gstreamer plugin is in medibuntu. 


Also, if you are desperate, fluendo sells wma gstreamer plugins.

---

### Post by sloggerkhan on 2007-09-07
ps: on my machine, w/ songbird, the wmv/wma files don't display on wbpages, but they show up as playable files and play fine in their own windows... probably I could link the songbird browser to the totem browser plugin and get it playing in browser instead of a separate window somehow. ( I don't really use songbird, even though it's pretty cool, I might when it's out of development. So I am not 100% certain about using the browser plugin)

---

### Post by ubuntu27 on 2007-09-07
> **acelin said:**
> Songbird stil wont pick up those WMA's!!

Just a though. Maybe those WMA files has [DRM ]("http://www.masternewmedia.org/2004/06/19/why_drm_is_bad_for.htm")(Ofiicially called Digital Rights Management. We call them Digital _Restriction_ Manager)?

---

