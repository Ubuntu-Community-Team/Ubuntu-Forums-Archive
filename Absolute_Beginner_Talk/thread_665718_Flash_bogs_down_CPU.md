---
title: "Flash bogs down CPU"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by occams_beard on 2008-01-12
So is there anything that can be done about Adobe Flash being such a CPU hog? Whenever I got to a flash heavy website, my CPU spikes up to 100% and the browser gets unresponsive. The frustrating thing about this is that under Windows the very same sites work just fine. UGH!

---

### Post by eapache on 2008-01-12
The adobe flash plugin for linux has always been poorly written. You could try the gnash plugin (open-source), but it can't handle the latest version of Flash.

---

### Post by occams_beard on 2008-01-12
I tried gnash, it wasn't much better, plus it can only do Flash 7 so lots of stuff looks screwy.

I guess we're stuck then with broken Flash and unresponsive browsers? That seems like a real deal breaker since more and more sites use Flash.

---

### Post by eapache on 2008-01-12
I know it's a pain. You could email adobe if you want :P

---

### Post by mandrill on 2008-01-12
go to adobe website, there is a linux section with a tar.gz file and installation instructions, install to firefox locally, not globally - works perfect for me.....and I would uninstall any other versions first....

---

### Post by eolson on 2008-01-12
I don't have the problem.  I can get it to spike to around 30% once in a while.   But that's the absolute max.

---

### Post by occams_beard on 2008-01-12
Installing it locally did not help.

> I don't have the problem. I can get it to spike to around 30% once in a while. But that's the absolute max. 

If it's just a single simple Flash advertisement or something, the cpu usage stays low, but for instance playing a youtube movie nearly maxes out my cpu cycles.With a youtube movies AND a busy flash ad it's all over.

---

### Post by mandrill on 2008-01-12
> **occams_beard said:**
> Installing it locally did not help.



If it's just a single simple Flash advertisement or something, the cpu usage stays low, but for instance playing a youtube movie nearly maxes out my cpu cycles.With a youtube movies AND a busy flash ad it's all over.

Only thing I can think is 1) equipment not up to it (doubtful) or 2) vestiges of old installs still there, 3) installed to wrong mozilla folder.
I just went to utube and watched 4 in a row with zero problem, and I am running an antique pc......did you check aboutplugins in firefox to see if flash9 is there?

---

### Post by eolson on 2008-01-12
Ran the Youtube Compiz video just now and max cpu usage was 24 percent.  I now it don't help,  but might help point in the right direction.

---

### Post by occams_beard on 2008-01-12
Well, the CPU is a P4 1.7 ghz, it's old, but that ought to be more than enough to watch a youtube movie at less than 100% cpu. At least I'd hope so, as even the most demanding flash works fine in Windows.

This page, for example, renders firefox unresponsive: [http://mypetjawa.mu.nu/](http://mypetjawa.mu.nu/)

Adobe flash is indeed installed. There's only one instance of it installed. It shows up on about:plugins.
    ```
File name: libflashplayer.so
    Shockwave Flash 9.0 r115

```

---

### Post by mandrill on 2008-01-12
> **occams_beard said:**
> Well, the CPU is a P4 1.7 ghz, it's old, but that ought to be more than enough to watch a youtube movie at less than 100% cpu. At least I'd hope so, as even the most demanding flash works fine in Windows.

This page, for example, renders firefox unresponsive: [http://mypetjawa.mu.nu/](http://mypetjawa.mu.nu/)

Adobe flash is indeed installed. There's only one instance of it installed. It shows up on about:plugins.
    ```
File name: libflashplayer.so
    Shockwave Flash 9.0 r115

```

I have a P4 1.8, just ran [http://mypetjawa.mu.nu/](http://mypetjawa.mu.nu/) no problem. Try re-installing firefox from the synaptic repos, -- process of elimination at this point....good luck!

---

### Post by occams_beard on 2008-01-12
How weird...

Actually, this is a fresh install of Ubuntu. I tried Fedora previously to see if I'd have the same problem with Flash. I did, so I reinstalled Gutsy.  

I ran top while playing a youtube video... It reported that firefox was using 60% and xorg was using 20% while the movie was playing.

---

### Post by eapache on 2008-01-13
I have a P3 1Ghz, and while it runs slow, it doesn't use nearly 100% of my cpu. Mind you, I'm running Xubuntu, not Ubuntu, but it uses the same Flash plugin. This is very peculiar. You could try deleting your firefox profile. In your home folder, press Ctrl-H to view hidden files, then rename .mozilla to just mozilla (no period in front). If that helps, then it's a corrupted profile problem. To restore your old profile, just add the . back in front and hit Ctrl-H again.

---

### Post by afeasfaerw23231233 on 2008-03-17
> **occams_beard said:**
> Well, the CPU is a P4 1.7 ghz, it's old, but that ought to be more than enough to watch a youtube movie at less than 100% cpu. At least I'd hope so, as even the most demanding flash works fine in Windows.

This page, for example, renders firefox unresponsive: [http://mypetjawa.mu.nu/](http://mypetjawa.mu.nu/)

Adobe flash is indeed installed. There's only one instance of it installed. It shows up on about:plugins.
    ```
File name: libflashplayer.so
    Shockwave Flash 9.0 r115

```

i have exactly the same problem! my computer is p4 1.8g and when it loads your link it almost hangs up. initially i think it's because my box is old. my version of flash is  9.0 r115. i wonder if this a problem of IGP or dedicated graphic card. my system has a i845gv IGP and doesn't have graphic card. but i remember flash just ran fine in winxp

---

### Post by afeasfaerw23231233 on 2008-03-18
> **occams_beard said:**
> Well, the CPU is a P4 1.7 ghz, it's old, but that ought to be more than enough to watch a youtube movie at less than 100% cpu. At least I'd hope so, as even the most demanding flash works fine in Windows.

This page, for example, renders firefox unresponsive: [http://mypetjawa.mu.nu/](http://mypetjawa.mu.nu/)

Adobe flash is indeed installed. There's only one instance of it installed. It shows up on about:plugins.
    ```
File name: libflashplayer.so
    Shockwave Flash 9.0 r115

```

i've tried that link on my another PIII 1G WinXp box in firefox and ie6. it doesn't hang. cpu utilization is around 35% in ff and 25% in ie. why is that? i also find out the speed of firefox to load page in winxp is faster than in ubuntu, it is not a joke. why is that?

---

### Post by forumonlooker on 2008-03-26
> **afeasfaerw23231233 said:**
> i've tried that link on my another PIII 1G WinXp box in firefox and ie6. it doesn't hang. cpu utilization is around 35% in ff and 25% in ie. why is that? i also find out the speed of firefox to load page in winxp is faster than in ubuntu, it is not a joke. why is that?

I have noticed the same problem on my machine. I have AMD Athlon 1Ghz machine. It is an old machine. This problem has to do with the revision of flash 9.0 you are using. Version r115 (Linux) takes up more CPU time on older machines.

I tried the link [http://mypetjawa.mu.nu/](http://mypetjawa.mu.nu/)  and I had the following CPU load with the flash 9.0 r48  :  53.5%  ( this was the peak value while loading the page)  and on the flash 9.0r115  I had the following reading.   ~73%  on Dapper. 

On the same machine I have the latest gutsy and flash content using the r115  fares even worse. I could barely run the  daily show website without using the flash blocker addon to remove flash ads.  The problem stems,I believe, from the way the latest player has been written and the compile options in either firefox or X in the latest ubuntu(Gutsy) that is causing this or incompatible compile options in the latest flash build and that of the latest ubuntu. 

What I suggest you do is downgrade to the version just bellow r115 ( which i believe is the r48)  which works well and use that instead. I am not sure what improvements r115  brings over the r48 but it is not worth an unresponsive firefox and better than the alternative (gnu flash player).

---

### Post by rjmoerland on 2008-03-26
I have the same problem on the Windows version of firefox as well, since version 0.9. The same page viewed in IE works just fine. Never found anything to fix it though, so I usually switch to IE (when using Windows) temporarily on flash-heavy websites. :(

---

### Post by Roger Mudd on 2008-03-26
I've had Flash problems using Firefox on each of the three major platforms (Windows, OS X and Linux). Problems range from pegged CPU usage to the inability to play more than five consecutive seconds of Flash video at a time. Part of me wonders if it's a Firefox integration issue as I don't use other browsers.

---

### Post by rapiddl on 2008-03-27
ok i have the same problem and i think it might be to do with totem plugin which seems like it has flash plugin also, im not sure but having both adobe and totem might give the increased processor load im uninstall totem plugin now i report back. :)


k0

---

### Post by rapiddl on 2008-03-27
It didnt help cpu still remains at 100% when watching flash videos. :(


k0

---

### Post by gsiliceo on 2008-05-04
I recommend you to install the 9,048 flash player, it is a LOT less cpu intensive.
First test your current version of flash here
[COLOR="Blue"][SHow my flash player version]("http://www.mediacollege.com/adobe/flash/player/version/show.html")[/COLOR]
Then normally you'd have to download a 94 meg package that adobe provides with lots of flash player version but i'd make it easier for you uploading just the recommended 9.048.
[COLOR="Blue"][Download it here 2.5 megs to your desktop]("http://www.mediafire.com/?znhecmwx0j4")[/COLOR]

Close firefox.

Then extract it, right click on the package and *"extract here"*
Open the folder and copy the file libflashplayer.so 
Now open a terminal and do this
> sudo nautilus
Once is opened go to /usr/lib/flashplugin-nonfree/
And paste the file you just copied, replace when asked. 
Then go back to the extracted folder in your desktop and double click the flashplayer-installer, and choose execute in terminal, then hit enter and you are done.

Test your new version of flash.

---

### Post by afeasfaerw23231233 on 2008-05-06
> **gsiliceo said:**
> I recommend you to install the 9,048 flash player, it is a LOT less cpu intensive.
First test your current version of flash here
[COLOR="Blue"][SHow my flash player version]("http://www.mediacollege.com/adobe/flash/player/version/show.html")[/COLOR]
Then normally you'd have to download a 94 meg package that adobe provides with lots of flash player version but i'd make it easier for you uploading just the recommended 9.048.
[COLOR="Blue"][Download it here 2.5 megs to your desktop]("http://www.mediafire.com/?znhecmwx0j4")[/COLOR]

Close firefox.

Then extract it, right click on the package and *"extract here"*
Open the folder and copy the file libflashplayer.so 
Now open a terminal and do this

Once is opened go to /usr/lib/flashplugin-nonfree/
And paste the file you just copied, replace when asked. 
Then go back to the extracted folder in your desktop and double click the flashplayer-installer, and choose execute in terminal, then hit enter and you are done.

Test your new version of flash.
Hi, i followed your instruction and after a pressed enter it stopped response. But the old file in /usr/lib/flashplugin-nonfree/ has been replaced by the newly downloaded libflashplayer.so from your link. What to do? 
```
Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved.

Adobe Flash Player 9 for Linux

Adobe Flash Player 9 will be installed on this machine.

You are running the Adobe Flash Player installer as a non-root user.
Adobe Flash Player 9 will be installed in your home directory.

Support is available at http://www.adobe.com/support/flashplayer/

To install Adobe Flash Player 9 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...
```
EDIT: sorry! i overlooke the line **Press ENTER to continue...** i have just installed it and now testing it with flash sites
EDIT: it told me to remove xpti.dat. do i need to and how do i do it?

---

### Post by gsiliceo on 2008-05-07
firefox told you? or the flash installer?
the file can be found in 
/home/**$YOURUSERNAME**/.mozilla/firefox/**RANDOMNAMEOFYOURPROFILE**/xpti.dat

---

### Post by afeasfaerw23231233 on 2008-05-07
the flash installer told me. do i need to remove it?
the link provided by:
> **occams_beard said:**
> Well, the CPU is a P4 1.7 ghz, it's old, but that ought to be more than enough to watch a youtube movie at less than 100% cpu. At least I'd hope so, as even the most demanding flash works fine in Windows.

This page, for example, renders firefox unresponsive: [http://mypetjawa.mu.nu/](http://mypetjawa.mu.nu/)

Adobe flash is indeed installed. There's only one instance of it installed. It shows up on about:plugins.
    ```
File name: libflashplayer.so
    Shockwave Flash 9.0 r115

```
doesn't contain many flash now.
i visit cbsnews.com and watch 60 minutes and usage of cpu maintains >90%

---

### Post by gsiliceo on 2008-05-07
You did something wrong because the flash version didn't installed.

---

### Post by afeasfaerw23231233 on 2008-05-09
how can i check if my flash is installed properly? i click this link [http://www.mediacollege.com/adobe/flash/player/version/show.html](http://www.mediacollege.com/adobe/flash/player/version/show.html) and it says flash 9,0,48,0 is installed. high cpu usage problem still exists.

---

