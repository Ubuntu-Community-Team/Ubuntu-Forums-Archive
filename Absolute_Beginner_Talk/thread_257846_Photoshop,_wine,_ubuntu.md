---
title: "Photoshop, wine?, ubuntu ??"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by carrobarro on 2006-09-15
Hello fellow ubuntu users. Im very new to this so please keep it simple. I am very proud to say that I have installed wine and figured out how to write winecfg in the terminal window to start it. Thats how far i have gotten. I have not yet had any succesfully program started on wine but my goal is to get photoshop to work. Is this possible?, is it just to write "wine setup.exe" ?and that should do the trick?..

Thanks :-\"

---

### Post by Obor on 2006-09-15
I think that people managed to get photoshop 7 working on wine. I haven't heard of anyone getting a more recent version to work.

---

### Post by Najand on 2006-09-15
Wow, photoshop and wine? It just sounds like a huge big slow application to me. There is an alternative for Photoshop which supports every kind of files and it is installed by default on Ubuntu. It can be found at:
Application -> Graphics -> GIMP Image Editor.
Try it and see if it is enough for your use or not.

---

### Post by carrobarro on 2006-09-15
Manage to work? sounds like a hard thing to do?. and does it work slow if you use wine?.
I tried gimp but i miss and need ps. maybe I should just install windows on dualboot and use that for ps.

---

### Post by Slychilde on 2006-09-15
You could also try gimp-shop, which is gimp made to look like photoshop.  It's a nice interim step until you get used to GIMP.  It might be easier to run photoshop under VMWare, rather than wine.  Wine can be rather fickle at times.

---

### Post by carrobarro on 2006-09-15
> **Slychilde said:**
> You could also try gimp-shop, which is gimp made to look like photoshop.  It's a nice interim step until you get used to GIMP.  It might be easier to run photoshop under VMWare, rather than wine.  Wine can be rather fickle at times.

how do i get/install VMWare? and whats the difference?.

---

### Post by Obor on 2006-09-15
> **carrobarro said:**
> Manage to work? sounds like a hard thing to do?. and does it work slow if you use wine?.
I tried gimp but i miss and need ps. maybe I should just install windows on dualboot and use that for ps.

GIMP should do most or all you need but to be honest Photoshop CS2 is the main reason why I'm dual booting with XP :(

---

### Post by Slychilde on 2006-09-15
Sorry about the slow response.  The difference between wine and VMWare, from what I understand, is wine tries to 'emulate' a single windows application whereas VMWare runs a virtual install of the entire windows OS.  [Here]("http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+howto") is a HowTo on installing VMWare for Windows XP.  After you install VMWare and XP, you can then run Xp within ubuntu and install whichever version of PS you like.  I'm guessing it will be slower than running just XP, but it might be fun/worth it to try.

---

### Post by aktiwers on 2006-09-15
> **carrobarro said:**
> Manage to work? sounds like a hard thing to do?. and does it work slow if you use wine?.
I tried gimp but i miss and need ps. maybe I should just install windows on dualboot and use that for ps.

You could also install Windows XP through Vmware, and install Photoshop in there. On my PC, Xp runs as fast in Vmware, as it would without being a guest OS.

[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

Check it out :)

---

### Post by steve.horsley on 2006-09-15
Back to the question of Photoshop in wine - I gather that photoshop 7 can run in wine (done it myself) but that later versions don't run in wine. However, later versions of wine keep coming out (another version came out today), so it may be that later versions of PS do now run. Photoshop is not slow under wine (somebody asked). 

To install PS into wine, use the command **wine setup.exe** or find setup.exe in the file browser and choose to open it with wine. Running PS is trickier - use the command something like:
**wine C:\\Program\ files\\Adobe\\photoshop\\photoshop.exe**
but remember it's case sensitive. To find the real path, look in your home folder in .wine/drive_c. To find the .wine folder you must click Ctrl-H in the file browser to turn on seeing hidden files (files starting with a dot are normally hidden).

If you want the latest and greatest version of wine, add these lines to /etc/apt/sources.list:
> ## WineHQ APT Repository
deb http://wine.budgetdedicated.com/apt dapper main
deb-src http://wine.budgetdedicated.com/apt dapper main

---

### Post by bodhi.zazen on 2006-09-15
You have several options:

First, I agree GIMP is worth looking at. There are other image viewers. 

Light and fast.
[gqview](http://gqview.sourceforge.net/)

Built by Google, runs on wine.
[Picasa](http://picasa.google.com/)

There is also eog and [feh](http://www.linux.com/article.pl?sid=06/07/14/184218).

eog is also light. feh is CLI but powerful. will do for example a slide show with your desktop background....

f-spot also works.

for information on wine, however, the best source is wineHQ.
[wineHQ](http://appdb.winehq.org/)

Put the name of you app in the gray search box on the left, search, and you find the most up-to-date info re how to run your application in wine.

Example:

[Photoshop on Wine](http://appdb.winehq.org/appview.php?iAppId=17)

---

### Post by carrobarro on 2006-09-16
> **Slychilde said:**
> Sorry about the slow response.  The difference between wine and VMWare, from what I understand, is wine tries to 'emulate' a single windows application whereas VMWare runs a virtual install of the entire windows OS.  [Here]("http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+howto") is a HowTo on installing VMWare for Windows XP.  After you install VMWare and XP, you can then run Xp within ubuntu and install whichever version of PS you like.  I'm guessing it will be slower than running just XP, but it might be fun/worth it to try.

oh I installed VMware and installed windows on that. really cool i think. but just a question. where does the file goes? how do i get the stuff i do in VMware into ubuntu?

---

### Post by narky on 2006-11-03
Hi there,

I know nothing about trying to run photoshop on linux via wine. Well or anything about wine for that matter. I haven't really used gimp much either, or vmware, why am I still typing you ask? Well a google search did find these articles:

[http://blog.publicidadpixelada.com/2006/10/10/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/](http://blog.publicidadpixelada.com/2006/10/10/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/)

[http://www.lifehacker.com/software/photoshop/how-to-install-photoshop-on-ubuntu-206827.php](http://www.lifehacker.com/software/photoshop/how-to-install-photoshop-on-ubuntu-206827.php)

Best of luck!

narky.

---

### Post by HereInOz on 2006-11-03
If you have installed XP in a VMWare server on Ubuntu, all you need to do is to set up a Samba share of your ubuntu home directory (/home/[username]) and make sure that you use the same username and password on XP that you set up in Samba.  

Set up the samba share in System > Administration > Shared folders, then create the username and password in a terminal:

sudo smbpasswd -a [samba username]

This will then ask for your ubuntu password, and then ask for the samba password to be entered.  This creates a samba user and password.  The square brackets are not to be used - I have merely put them there to let you know to put your usernames and passwords in these places.

You should then be able to see the samba share from the XP virtual machine in My Network Places.  You can even map a drive to it if you want.

Hope this helps.

---

### Post by SunnyRabbiera on 2006-11-03
Worse comes to worst there is always corssover office.

---

### Post by Alcem-nos tots! on 2006-11-07
How can I install the GIMP-Shop???? :'(

---

### Post by chocbar31 on 2006-11-07
I have not tried this method yet, but it looks as promising as any other for isntalling PS on linux.

[http://blog.publicidadpixelada.com/2006/10/10/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/]("http://blog.publicidadpixelada.com/2006/10/10/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/")

---

