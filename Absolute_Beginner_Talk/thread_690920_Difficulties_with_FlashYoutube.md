---
title: "Difficulties with Flash/Youtube"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by stinkywizzlecheeks on 2008-02-07
Hello,

I've had 7.10 installed for about a month now and I've never been able to get Flash working properly. Sometimes it works fine and other times the images are all jumbled and wrong. On top of this, Youtube never seems to work properly either. The video is all choppy (about 1fps) and the audio cuts in and out. The only time it worked properly was when I clicked a link straight to a Youtube user page, then the video worked fine.
I've been looking around the forums for possible solutions and have tried a few, but nothing seems to work. The last thing I tried was uninstalling flashplugin-nonfree, but that seems to have had no effect - flash is still working in it's semi-functional way.
Help is much appreciated but I truly am a beginner and not super-confident with work in the terminal (in other words, please spell things out as if you were talking to an idiot). Thanks!

---

### Post by spiderbatdad on 2008-02-08
the flashplayer in synaptic was buggy. IDK if it has been patched. The best place to get it is right from adobe:[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash) get the tar.gz
the installation is very simple, and the instructions are right there below the download. Also install the ubuntu restricted extras...and accept the license agreements during the set up process.[HTML]sudo apt-get install ubuntu-restricted-extras[/HTML]

---

### Post by papuccino1 on 2008-02-08
Follow the instructions here word for word.

[http://ubuntuforums.org/showthread.php?t=664242]("http://ubuntuforums.org/showthread.php?t=664242")

---

### Post by BandD on 2008-02-08
It may be possible that you have gnash installed as well (a free and open source flash plugin, that is still in early development and very buggy).  Go into the Synaptic Package Manager (System--> Administration--> Synaptic Package Manager).  Once you've inputted your password and it's opened, click anywhere on the package screen and then type: gnash

if there is a green box next to it, then it is installed.  In this case click the green box and select "Mark For Complete Removal".  Then click the Apply button and in the window that pops us, click Apply.  This will then remove Gnash.  

Then go to the Adobe site:  [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux")

And download Option 1: .tar.gz

Then read the instructions toward the bottom of that page.

That should get you going.

Let us know.

---

### Post by jruhl on 2008-02-08
I also was having the same trouble with U Tube and this fixed it. Thanks for your help.

---

### Post by pjones0404 on 2008-02-08
i was having issues with youtube as well. i followed the instructions listed here and it worked great. 

thanks every one!

---

### Post by stinkywizzlecheeks on 2008-02-08
Awesome, guys! It worked like a charm. I did indeed of gnash installed so uninstalling that and following the straight forward install instructions from the link worked perfectly.
Thanks again!

---

### Post by pakkispower on 2008-02-08
Thanks guys, i followed the instructions and it works great for me too! But when i play a video in full screen i cant see the bar on the bottom that lets you forward the video and tells you the duration of the video. Its kinda annoying not having that... Any suggestions? Thanks!

---

### Post by HappyFeet on 2008-02-08
just an FYI. i just did a fresh install today and flash from ubuntu-restricted-extras works flawlessly. it is now fixed.

---

### Post by paradoc on 2008-02-08
arrgh! just beat me to it happyfeet!........however, for more detail:
 ....if this fails for any reason (dependencies etc) you could try the GUI approach (which I posted for Feisty last Sept) > 
Launch Add/Remove (from Applications)
Enter restricted in the search bar, choose 'All available applications', with 'All' highlighted, (top of left hand menu), if no tick on 'Ubuntu restricted extras', then tick it and  you will be downloading Java 6 runtime, Flash 9 player, and a few popular MS fonts, when you click on APPLY.

If APPLY is greyed out, it means you already have it installed, and 'OK' simply removes the app window leaving you possibly wondering why it didn't work! 

GUIs forever!:)

---

### Post by ThomasTangNJ on 2008-02-08
I did what the instruction said and the terminal shows the error below when I try to run that file
```

./flashplayer-installer

```
And the error is shown like this......
```

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

```

what should I do?

Thanks

Thomas

---

### Post by BandD on 2008-02-08
Thomas, it looks like you have the 64-bit version of ubuntu and the flash plugin is designed for 32-bit architecure.  So have a look at this thread and see if it fixes your problems:
[URL="http://ubuntuforums.org/showthread.php?t=476924"]
http://ubuntuforums.org/showthread.php?t=476924[/URL]

Good luck!

---

### Post by ThomasTangNJ on 2008-02-11
Yes, I'm using 64bit edition of ubuntu Studio.

And I just tried the link. No luck for me....:(

don't know what to do?

But still, Thanks for your help.

Thomas

---

### Post by jan quark on 2008-02-11
try this , run in terminal

```
sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```

---

