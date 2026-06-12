---
title: "[SOLVED] Codecs issues"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Walc on 2008-01-07
Ok
Im done here....some of avi files r displayed properly whilst some r not, not mentioning about .rmvb format
Tbh im not even sure how to get this all sorted where to begin etc...
I did install some of the codecs, thats for sure, 
What do u want me to post here, screenshot of source or??? etc - > so that we know what i have installed so far..?
Help me out guys, cuz its drivin me crazy

---

### Post by stalker145 on 2008-01-07
> **Walc said:**
> Ok
Im done here....some of avi files r displayed properly whilst some r not, not mentioning about .rmvb format
Tbh im not even sure how to get this all sorted where to begin etc...
I did install some of the codecs, thats for sure, 
What do u want me to post here, screenshot of source or??? etc - > so that we know what i have installed so far..?
Help me out guys, cuz its drivin me crazy

For the RealMedia Variable Bitrate (rmvb) you can try [this tutorial]("http://ubuntuforums.org/showthread.php?p=4050384") and see if it works for you.

For the avi files, have you installed the Restricted Extras? (Add/Remove on your Applications menu)

Give those a shot right quick and if they don't work, c'mon back.

---

### Post by hyper_ch on 2008-01-07
rmvb run fine with RealPlaer - but nothing else as I've found out so far. VLC can play the sound of it but didn't show any vide...

---

### Post by Walc on 2008-01-07
stalker145: 
* Restricted Extras did the job in avi case :)
*im having problems with following rmvb tutorial tho: [http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/](http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/)

in step 6 when prompting: sudo mkdir /usr/lib/win32  i get this:  mkdir: cannot create directory `/usr/lib/win32': File exists

any ideas???

---

### Post by childofstrings on 2008-01-07
I'd just download VLC, [http://www.videolan.org]("http://www.videolan.org").

You can find in the Synaptic Packet Manager I believe.

---

### Post by Walc on 2008-01-07
VLC didnt do the job.......
basiclly nth happens when tryin to open rmvb with VLC

---

### Post by Walc on 2008-01-08
bump

---

### Post by stalker145 on 2008-01-08
> **Walc said:**
> stalker145: 
* Restricted Extras did the job in avi case :)
*im having problems with following rmvb tutorial tho: [http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/](http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/)

in step 6 when prompting: sudo mkdir /usr/lib/win32  i get this:  mkdir: cannot create directory `/usr/lib/win32': File exists

any ideas???

Have you tried deleting the directory that's there and then recreating it? Sounds kinda foolish now that I say it, but it's worth a shot.

---

### Post by Walc on 2008-01-08
btw. when tryin to install MPlayer....thru Synaptics...i was able to snatch all of its components excpept 1: mplayer nogui

[[IMG]http://img170.imageshack.us/img170/3995/61486729ua1.th.png[/IMG]](http://img170.imageshack.us/my.php?image=61486729ua1.png)

when i do mark it for installation this is what i have: [[IMG]http://img166.imageshack.us/img166/310/81709869la0.th.png[/IMG]](http://img166.imageshack.us/my.php?image=81709869la0.png)

---

### Post by mcduck on 2008-01-08
> **Walc said:**
> btw. when tryin to install MPlayer....thru Synaptics...i was able to snatch all of its components excpept 1: mplayer nogui

[[IMG]http://img170.imageshack.us/img170/3995/61486729ua1.th.png[/IMG]](http://img170.imageshack.us/my.php?image=61486729ua1.png)

when i do mark it for installation this is what i have: [[IMG]http://img166.imageshack.us/img166/310/81709869la0.th.png[/IMG]](http://img166.imageshack.us/my.php?image=81709869la0.png)

That's normal mplayer-nogui is just an alternative package for mplayer that only includes the command-line program without the graphical user interface. The normal mplayer package includes bith command-line mplayer _and_ the GUI.

You can only have one or other installed, not both (As having both wouldn't make any sense).

---

### Post by Walc on 2008-01-08
ok
so shall i remove the directory as stalker145 adviced?

---

### Post by mcduck on 2008-01-08
> **Walc said:**
> ok
so shall i remove the directory as stalker145 adviced?

No. If the directory is already there it makes no difference if you remove it and then immediately create it again. Just skip that step on the tutorial.

---

### Post by Walc on 2008-01-09
like i said, when skipping that step it still doesn not work.................

---

### Post by Walc on 2008-01-13
bump..?

---

### Post by Kimm on 2008-01-13
I dont understand why noone just tells him to install RealPlayer??

[http://www.real.com/linux](http://www.real.com/linux)

It should also be in the repositories: sudo apt-get install realplay (if not, just get it from the site)

---

### Post by Walc on 2008-01-13
when tryin to install via terminal i get this: Couldn't find package realplay

also the link u gave me...when clicking on download site goes blank and nth happens.....

               v  v  v  v  v  v  v

[[IMG]http://img104.imageshack.us/img104/6631/screenshotgr5.th.png[/IMG]](http://img104.imageshack.us/my.php?image=screenshotgr5.png)

---

### Post by Kimm on 2008-01-13
> **Walc said:**
> when tryin to install via terminal i get this: Couldn't find package realplay

also the link u gave me...when clicking on download site goes blank and nth happens.....

               v  v  v  v  v  v  v

[[IMG]http://img104.imageshack.us/img104/6631/screenshotgr5.th.png[/IMG]](http://img104.imageshack.us/my.php?image=screenshotgr5.png)

Hmm.. it seems not to be in the repositories, and the link seems to not work at the moment.

Try downloading from this page: [http://forms.helixcommunity.org/helix/builds/?category=realplay-current](http://forms.helixcommunity.org/helix/builds/?category=realplay-current) the links seem to be working. I think this is the correct package: [http://forms.helixcommunity.org/helix/builds/index.html?filename=20080112/player_all-realplay_gtk_current-20080112-linux-2.2-libc6-gcc32-i586@rhel4/realplay-10.1.0.3920-linux-2.2-libc6-gcc32-i586.bin](http://forms.helixcommunity.org/helix/builds/index.html?filename=20080112/player_all-realplay_gtk_current-20080112-linux-2.2-libc6-gcc32-i586@rhel4/realplay-10.1.0.3920-linux-2.2-libc6-gcc32-i586.bin)

Edit:
NO, that link is wrong... wait for a minute... What architecture do you have btw? (if you dont know, type: uname -a in the terminal and paste the output here)

---

### Post by Kimm on 2008-01-13
This should be right. Go to this page:
[https://player.helixcommunity.org/](https://player.helixcommunity.org/)

and click the big "RealPlayer" Button. The link works :)

---

### Post by Walc on 2008-01-13
its: Linux tehpc 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

btw. how can i open that *.bin file?

---

### Post by Kimm on 2008-01-13
> **Walc said:**
> its: Linux tehpc 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

btw. how can i open that *.bin file?

Good, than that package is the right one :)

Oh, I should have told you that...
The .bin file is more like a Windows installer than a package, you need to make sure that it is executable and then run it, type this in the terminal (replace "filename" with the name of the file)

chmod +x filename
sudo ./filename

It should then install. I'm not sure to weather or not it will show up in your menu (if it doesn't, let me know and I can help with that too), but you can run it by typing "realplay" in your terminal :)

---

### Post by Walc on 2008-01-13
lol :

[[IMG]http://img112.imageshack.us/img112/8860/screenshotne5.th.png[/IMG]](http://img112.imageshack.us/my.php?image=screenshotne5.png)

similar thing happens when im giving it with the full path

---

### Post by Kimm on 2008-01-13
> **Walc said:**
> lol :

[[IMG]http://img112.imageshack.us/img112/8860/screenshotne5.th.png[/IMG]](http://img112.imageshack.us/my.php?image=screenshotne5.png)

similar thing happens when im giving it with the full path

Hmm... you must be in the wrong directory. Are you sure you downloaded it to home? and if that is the case, are you sure you have the right filename?

The standard settings in Firefox is to download files to your desktop, unless you changed that, do a "cd Desktop" and try the commands I gave you before again.

---

### Post by Walc on 2008-01-13
u were right m8
its all working now
thx m8

<btw...by mistake ive installed it on the desktop...now id like to reinstall it but its not in the add/remove nor in synaptics....>

---

### Post by Kimm on 2008-01-14
> **Walc said:**
> u were right m8
its all working now
thx m8

<btw...by mistake ive installed it on the desktop...now id like to reinstall it but its not in the add/remove nor in synaptics....>

No, the RealPlayer installer doesnt work well with Synaptic or package management in general. Do you have a RealPlayer icon in the applications menu? In that case, typ this in terminal:

sudo rm -f /usr/share/applications/realplay.desktop
sudo rm -f /usr/local/share/applications/realplay.desktop

Then delete the files on the desktop (use "sudo rm -rf <directory>" if you need to be root) and reinstall.

You should install to /opt or /usr/local

---

### Post by philinux on 2008-01-14
The realplayer version for feisty works best as it correctly install the helix dna plugin required for rm streams.

[http://archive.canonical.com/pool/partner/r/realplay/](http://archive.canonical.com/pool/partner/r/realplay/)

The link at the bottom is a .deb file. Just download to desktop. Double click it and it's installed no fuss.

---

### Post by Walc on 2008-01-15
thx Kimm uve saved my life again
:D

---

