---
title: "Installing new programs without an Internet connection"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by Cadoret on 2007-07-16
Hi, I'm an experienced Windoze user but new to Linux/Ubuntu, so apologies if there's a similar post already.

I've recently installed Ubuntu, am **_VERY_** impressed so far, but don't have an Internet connection I can use for downloads to the Linux machine. At present I can only download to a USB hard drive (i.e. the connection I have access to isn't at home!)

Is there any central location I can go to, to download new programs & things like MP3 codecs & backends etc., and then install them locally?

Once again, apologies if the answer is RTFM!!! :-)

regards,

Graeme

---

### Post by Malta paul on 2007-07-16
Hi,
Welcome, The only way I know is if you have a friend that has installed Ubuntu on his computer and also has an internet connection. You can then use a small package called 'APTonCD' down load from >http://aptoncd,sourceforge.net<  This would enable you to pick your choice of packages and save to a CD or DVD and then install them on your computer without an internet connection..
Hope this is of some help :guitar:

---

### Post by freebird54 on 2007-07-16
@ possible answers to things.  One way is to get the repositories on disk from Canonical - takes little while, but you get the whole thing on DVD's, and can load from them instead of the net in the usual (synaptic Package manager) way.

Another way is to go to the repositories via other means and dload the .deb files (already packaged files) and when you get them to your system, just double-click on them.

As I have broadband I haven't tried method 2 as yet ( would probably use Synaptic from Live CD, then save on USB) but it SHOULD work :)  Method 1 I have used from Live CD's for various reasons - and is extremely easy to do (tell the package manager to look at the disk - or even insert the disk and it will ask!)

Hope this helps....

Oh - and given enough speed where you are dloading - it may be possible to dload ISO's of the repository disks - would have to check that out though...

EDIT:  A possible link for the DVD access is [here](http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/feisty/release/). I used the UK mirrors because I can't tell where you're from... :)

---

### Post by bodhi.zazen on 2007-07-16
+1 AptOnCD

---

### Post by RealG187 on 2007-07-16
IF you install them like normal you can get the DEBs from

```
/var/cache/apt/archives
```
I backup all my DEBs, it is kinda annoying..

---

### Post by harakiri1976 on 2007-07-17
Hello Guys!

I'm using Ubuntu Feisty Fawn at my laptop (ASUS A6JC) with Compiz-Fusion and everything rolling ok. At home I don't have internet so I tried to use ATPonCD to save all .deb files and "load" them via Synaptics. The problem was when I tried to make:

 sudo apt-get update

..and install all the .deb because there were a lot of dependency problems i was expecting:( I really don't know why is that because I've never deleted the installation files at my laptop. I tried to install from Synaptic and using:

 sudo dpkg -i *

 on the /var/cache/apt/archives directory.
You can see on the attachment most of problems encountered in the shell.

If someone can help me, please. 

Thanks!

---

### Post by RealG187 on 2007-07-17
I was thinkinf of making a site with all the debs for the applications, the problem is I use 6.10 and am not sure if the DEBs will work for people who use 7.04, 7.10 (October), or evern 6.06, 5.?? (Warty and Hoary)...

---

### Post by bodhi.zazen on 2007-07-17
Here is a how to for aptoncd :

[http://ubuntuforums.org/showthread.php?p=3004127](http://ubuntuforums.org/showthread.php?p=3004127)

Note : you will need to download the packages somehow ;) I suppose you could do it from a live CD if you had the hard drive space ....

---

### Post by bodhi.zazen on 2007-07-17
> **RealG187 said:**
> IF you install them like normal you can get the DEBs from

```
/var/cache/apt/archives
```
I backup all my DEBs, it is kinda annoying..

You can do this another way ...

Well, FYI, there is a way with a lot less disk space (not that aptoncd is not very cool) ...

Step 1 Make a list of all the applications you have installed :

sudo dpkg &#8211;-get-selections | grep -v deinstall > ubuntu-files

* Note : that is all one line and there are two - - in front of "get-selections" ;) 


Step 2 Save the file "ubuntu-files" on a flash drive or e-mail it to yourself ...


Step 3 Reinstall Ubuntu, update :

sduo apt-get update
sudo apt-get dist-upgrade


Step 4 Re-install all those applications ...

sudo dpkg &#8211;-set-selections < ubuntu-files

* Again, all one line and two - - in front of "set-selections"

Step 5 Install :

sudo deslect

This opens a deslect session. Just type 'I' to install (that is a capital i ).

Enjoy

---

### Post by harakiri1976 on 2007-07-19
Thank You guys!;)

I will try! :-)


PS: By the way, I am almost sure that .DEB files from different distributions don't work:(

---

### Post by Hitchhiker42 on 2007-07-19
Dunno if you've already solved your problem or not, but I had a similar one back when I was on dialup. I'm not sure of the exact commands, as I'm not at my home computer right now, but here goes: Select all the packages you need in Synaptic, then go to the first menu, and there should be an option saying something like "Generate download script." Generate your script, and use the URLs contained within to download the files from another computer (I gave the script to my Dad, who copied the files onto his XP laptop and gave them back to me. If you have a Linux computer, you can just run the script, but if you're running Windows on the downloading computer, you need to copy and paste the URLs.) After you've got your files, put them all in the same directory on your Ubuntu machine, and point Synaptic at them (There should be a command very close to the earlier one that will let you tell Synaptic where they are). 

Sorry for being so vague, I can try and be more detailed once I'm sitting in front of my own computer.

ETA: Found my thread on the subject, with the awesome help I was given and my own eventual solution: [http://ubuntuforums.org/showthread.php?t=344471](http://ubuntuforums.org/showthread.php?t=344471)

---

### Post by RealG187 on 2007-07-19
> **bodhi.zazen said:**
> You can do this another way ...

Well, FYI, there is a way with a lot less disk space (not that aptoncd is not very cool) ...

Step 1 Make a list of all the applications you have installed :

sudo dpkg –-get-selections | grep -v deinstall > ubuntu-files

* Note : that is all one line and there are two - - in front of "get-selections" ;) 


Step 2 Save the file "ubuntu-files" on a flash drive or e-mail it to yourself ...


Step 3 Reinstall Ubuntu, update :

sduo apt-get update
sudo apt-get dist-upgrade


Step 4 Re-install all those applications ...

sudo dpkg –-set-selections < ubuntu-files

* Again, all one line and two - - in front of "set-selections"

Step 5 Install :

sudo deslect

This opens a deslect session. Just type 'I' to install (that is a capital i ).

Enjoy

SO it copies all the programs into a single file?? COuld I replace ubuntu-files with any other filename??

Would this be a solution to [This](http://ubuntuforums.org/showthread.php?p=3048935#post3048935)?

---

### Post by bodhi.zazen on 2007-07-19
> **RealG187 said:**
> SO it copies all the programs into a single file??

No, it just makes a list of all the installed applications.

> COuld I replace ubuntu-files with any other filename??

Yep, you can call it what you want.

> Would this be a solution to [This](http://ubuntuforums.org/showthread.php?p=3048935#post3048935)?

Not exactly. When you re-install and then run through steps 3, 4, and 5 you will download and re-install the programs from the list you generated.

So, no more saving all those .deb files, unless you want to.

It will not back up either your data or customizations, just a complete lest of all installed applications.

To make life easier you may want to keep a coy of etc/apt/sources.list (you will need to re-enable your repositories before you do step 3, 4, and 5).

HTH

---

### Post by RealG187 on 2007-07-21
if it just makes a list an i still have to redownload then its still not wat i want, i like using debs to install better...

---

### Post by Cadoret on 2007-07-26
Thanks for all the suggestions and working through them. I've also found a site [www.getdeb.net](www.getdeb.net), and have successfully installed WINE, and from there 2 Windoze apps with (relative) success.

But through that I think I'm in the position of missing system files that would have been added in the normal install/Internet update procedure (things like codecs & drivers), so I think I need to knuckle down & look for specific Windoze migration support here or figure things out myself!

Will post any info & links I find as I go.

---

### Post by RealG187 on 2007-07-26
Codecs like MP3[COLOR="Red"]/[/COLOR]MP4[COLOR="Red"]/[/COLOR]WMA[COLOR="Red"]/[/COLOR]QT/MOV? etc dont come with.

You can downlad xMMS and I think that plays MP3 without any codec pack, but to get it in Totem/Banshee/Amarok/etc u need to install the codecs pack for G-Streamer. I think I have a DEB file I can give then u can use a flash drive or something to transfer it...

Do DEBS from sudo-apt get install [COLOR="Red"]program name[/COLOR] from 6.10 work in other versions (6.06, 7.04, 7.10, etc)?

---

