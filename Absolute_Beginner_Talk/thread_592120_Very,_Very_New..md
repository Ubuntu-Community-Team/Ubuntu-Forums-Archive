---
title: "Very, Very New."
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-10-26
Hi there, yesterday I tried to install ubuntu on my computer, in attempts to dual boot it with windows vista. that failed miserably and I ended up formatting my drive and installing only ubuntu. Vista is gone (probably for the better).  Having doing that, I can see where some of the intimidation comes from when transferring to linux. I've never used anything like this before. Only windows.  I've been playing around with a few things, getting to learn the ropes, and i've still got a few questions. If someone wouldn't mind helping me out with some problems i may encounter by posting responses in here, it would make my life a thousand times easier.  
My first question:  my web browser is running slow. i was reading some other posts and they said that i probably need to disable some setting that is running.  They told me i needed to create a bad_list file in my modprobe.d folder  I tried doing this, but upon trying to save it told me i didnt have the permissions to do this. apparently i needed to run it as a superuser.

this is the line inside of the badlist file:
alias net-pf-10 off

if someone could tell me how to save, or run commands as a superuser that would be much appreciated.  I know that the sudo command in the terminal is used for commands there, but i wouldn't know how to save this file in the terminal, if even possible.
Any help would be very much appreciated, and thank you in advance.
I'm sure there are more problems to come.

---

### Post by Maestro23 on 2007-10-26
Need sudo command for terminal. Also for using gedit (to edit files), use gksudo.

> gksudo gedit....

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jordank on 2007-10-26
haha, i dont think you understand how new to this i am. I don't know what gksudo is even. And is that something i would get from the synaptics package manager?  When i get it what do i do with it?  am i going to be running it from the terminal? i'm only trying to save a file.

---

### Post by Maestro23 on 2007-10-26
> **jordank said:**
> haha, i dont think you understand how new to this i am. I don't know what gksudo is even. And is that something i would get from the synaptics package manager?  When i get it what do i do with it?  am i going to be running it from the terminal? i'm only trying to save a file.

Open a terminal.  Then you will use the command to open the file with root privileges.

> gksudo gedit /etc/modprobe.d/(filename)

Make your changes, Save the file.

Once you are inside gedit, it is pretty self-explanatory.

---

### Post by SunnyRabbiera on 2007-10-26
relax the terminal in ubuntu is super easy.

---

### Post by jordank on 2007-10-26
Perhaps i need to clarify my question:
How do i save as a superuser?

while i'm at it, i'm going to toss out a couple more very newbie questions:

1) What exactly are tarballs? how to i use them? are they similar to zip files? what program do i use to open them? 
2) What is Gutsy? i see everyone talking about it, but have no idea what it is.  I got my version of ubuntu by downloading it from the site, burning it as an image onto a cd and loading it off the live cd.  Is gutsy something entirely different?
3)Is there perhaps another reason why my browser seems to be exceptionally slow? while running windows it was working fine.
4) While in windows, i was using a program called Apex DC++ to connect to a hub at my university.  Can i run apex somehow off ubuntu, or is there a similar program i should use that is more compatible with linux?
5) Are there, in general, any packages or tweaks or suggestions, or anything of that array that I should do to my operating  system, being a very new install? to maybe boost performance?

---

### Post by Hallvor on 2007-10-26
If this was a game of Doom, gksudo would be something like God-mode, and Gedit is the default text editor of Gnome... :???:

the command ```
gksudo gedit
``` will launch the text editor so that you can make changes everywhere in your system, and not only in your home directory.

If I type ```
gksudo gedit /etc/apt/sources.list
``` I will be able to edit that file with Gedit, even if the file is outside my home directory.

---

### Post by Maestro23 on 2007-10-26
> **jordank said:**
> Perhaps i need to clarify my question:
How do i save as a superuser?

while i'm at it, i'm going to toss out a couple more very newbie questions:

1) What exactly are tarballs? how to i use them? are they similar to zip files? what program do i use to open them? 
2) What is Gutsy? i see everyone talking about it, but have no idea what it is.  I got my version of ubuntu by downloading it from the site, burning it as an image onto a cd and loading it off the live cd.  Is gutsy something entirely different?
3)Is there perhaps another reason why my browser seems to be exceptionally slow? while running windows it was working fine.
4) While in windows, i was using a program called Apex DC++ to connect to a hub at my university.  Can i run apex somehow off ubuntu, or is there a similar program i should use that is more compatible with linux?
5) Are there, in general, any packages or tweaks or suggestions, or anything of that array that I should do to my operating  system, being a very new install? to maybe boost performance?

**sudo** and **gksudo** give you SuperUser privileges.  Did you not read my link to RootSudo.

---

### Post by jordank on 2007-10-26
awesome. that worked. thank you :) now hopefully it speeds up my browser. still need to restart to check.

---

### Post by jordank on 2007-10-26
that makes sense. 
does anyone have a link to a site that lists a bunch of commonly used terminal commands?
It's weird going from windows to a mostly text based system.
not familiar with this at all.

---

### Post by jordank on 2007-10-26
for anyone interested, by adding that line to the modprobe.d directory it did help speed up my browser (or so it seems).

---

### Post by Siph0n on 2007-10-26
LinuxCommand.org may help... try it out :)

---

### Post by SunnyRabbiera on 2007-10-26
well lucky for you in ubuntu you will most likely never even have to touch the terminal much.
the most commands you will probably have to use are:
apt-get
sudo
alien (if needed)
sh
thats all i had to use of course.
for administration stuff such as updating apt just use sudo, so your command will be:
sudo apt-get
apt is a terminal application to get applications and you will most likely never have to use it in the terminal unless you have severe issues.
to update the packages the command will be:
sudo apt-get update
to upgrade whatever you have on your system the command is:
sudo apt-get upgrade
most likely you wont have to encounter the terminal much, ubuntu is very GUI oriented.

---

### Post by Maestro23 on 2007-10-26
> **jordank said:**
> that makes sense. 
does anyone have a link to a site that lists a bunch of commonly used terminal commands?
It's weird going from windows to a mostly text based system.
not familiar with this at all.

Man, there are so many sites, just google "Linux commands". Here's a couple:

LinuxCommand.org: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Unix and LInux Commands: [http://www.computerhope.com/unix.htm](http://www.computerhope.com/unix.htm)

Installing Software in Ubuntu:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

*Remember, you switching to a whole new OS.  You gotta walk before you can run.  Luckily this is one of the best forums for any Distro I"ve used.  I'ts like FREE tech support.

Welcome to Ubuntu. :guitar:

---

### Post by jordank on 2007-10-26
Hrmm. i still dont think the browser is running at full speed.
is there something that may be slowing it down?
is there a default firewall with ubuntu? would removing that speed me up any?

With windows i would never run with a firewall. Mind you i could clear about any virus i contracted with that os.  Ubuntu is a different story.
Also, if anyone has answers to some of the other questions i posted that would be awesome.  I think they're on the first page.
Thank you.

---

### Post by jordank on 2007-10-26
well that's kind of relieving. I had it in my mind that this would be very much based out of the terminal.
I'll check out those sites, but it doesn't look like i'll be using too many commands.

I used most of the ones you listed too.
I found a site that told me how to set up gcc.  I had to do a bunch of sudo apt get commands and sudo updates
that's working for me now.

as for a program to write c and c++... i went to the synaptic package manager and downloaded something called pype.
I had heard of people using python before as their programming program, and i wasnt sure if pype is the same as python.
Anyone know?

---

### Post by mali2297 on 2007-10-26
> **jordank said:**
> 
1) What exactly are tarballs? how to i use them? are they similar to zip files? what program do i use to open them? 

Yes, they are similar to zip files. If you double-click one of them  in the file browser, an archive manager will open and you can choose to unpack it. It is also possible to use the terminal:
```

tar xvzf filename.tar.gz

```

> 
2) What is Gutsy? i see everyone talking about it, but have no idea what it is.  I got my version of ubuntu by downloading it from the site, burning it as an image onto a cd and loading it off the live cd.  Is gutsy something entirely different?

Gutsy Gibbon is a codename for Ubuntu 7.10. You can see which version of Ubuntu you have with the command
```

cat /etc/issue

```
in the terminal.

> 
5) Are there, in general, any packages or tweaks or suggestions, or anything of that array that I should do to my operating  system, being a very new install? to maybe boost performance?

I suggest you get familiar with the system before you try to boost performance. Of course, you can do whatever you want.:)

---

### Post by Siph0n on 2007-10-26
PyPy is not python... It is for python, but not the actual python interpreter... Ubuntu comes with python already installed :) So your all set there...

---

### Post by SunnyRabbiera on 2007-10-26
your browser issues might be from firefox then anything else,.
I have noticed that sometimes firefox in ubuntu is slower then on windows and on certain other distributions, a re install of firefox would be a good fix if it wasn't so tied into ubuntus core (it has some dependencies that gnome needs in ubuntu thus why it can be slow)
you can try another browser such as opera and see how that speeds around, if it works better then I know what your issue is.

---

### Post by escobar_ on 2007-10-26
> **jordank said:**
> Perhaps i need to clarify my question:
How do i save as a superuser?

while i'm at it, i'm going to toss out a couple more very newbie questions:

1) What exactly are tarballs? how to i use them? are they similar to zip files? what program do i use to open them? 
2) What is Gutsy? i see everyone talking about it, but have no idea what it is.  I got my version of ubuntu by downloading it from the site, burning it as an image onto a cd and loading it off the live cd.  Is gutsy something entirely different?
3)Is there perhaps another reason why my browser seems to be exceptionally slow? while running windows it was working fine.
4) While in windows, i was using a program called Apex DC++ to connect to a hub at my university.  Can i run apex somehow off ubuntu, or is there a similar program i should use that is more compatible with linux?
5) Are there, in general, any packages or tweaks or suggestions, or anything of that array that I should do to my operating  system, being a very new install? to maybe boost performance?

1. Yes, tarballs are like zip files. The compression used is just different. They can be opened with for instance [PeaZip]("http://peazip.sourceforge.net/").

2. Gutsy is the newest Ubuntu release, version 7.10. If you downloaded the image after the 19th of October, you are running Gutsy.

4. I'm not sure about Apex DC++ but here's [a guide]("http://ubuntuforums.org/showthread.php?t=28378") how to install normal DC++ on Ubuntu. Perhaps you could run Apex DC++ with wine?

5. [Here]("http://ubuntuforums.org/showthread.php?t=189192") are some tweaks, I haven't applied them myself so I'm not sure how powerful they are.

I hope these answers are good enough. :)

---

### Post by jordank on 2007-10-27
Hey, can someone explain the idea behind wine, how to use it, and if i need plugins for it?  I want to run apex dc++, how would i go about it?

---

### Post by icechen1 on 2007-10-27
> **jordank said:**
> Hey, can someone explain the idea behind wine, how to use it, and if i need plugins for it?  I want to run apex dc++, how would i go about it?

WINE(**W**ine **I**s **N**ot an **E**mulator) is a program to run many Windows programs,to install it see [http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)
Their website is [http://winehq.com](http://winehq.com)

---

### Post by Orbital75 on 2007-10-27
Oh, your really going to like Ubuntu.....  there are all kinds of programs you can try that are just
as good as or even better than most windows programs. 

Some programs you may want to check into is

**( Media Programs )**
Gimp :  ( Photo Editor )
GQview :  ( Photo Viewer )
Banshee : ( Music Player )
Pidgin : ( Instant Messenger )
Totem : ( Video Player )

**BackUp Programs** These are important .....
huBackup : Backup your home directory
sbackup : Backs up any folder you would like
Partimage : will make a bit for bit image of any partition ( Similar to Norton Ghost )

You may also like Simdock and gdesklets
Simdock is a little dock that programs can sit on like OSX on the Mac.
gdesklets are similar to konfabulator on windows, it's basically widgets that sit on your desktop.

If you have a Gig of Ram and would like to use windows with out a duel boot you
could use a virtual machine. 

Virtual Box : Will run any Windows or Linux OS in a Virtual Machine.

---

### Post by jordank on 2007-10-27
I'll have to look more in to wine a bit later.  But recently i was trying to watch a movie i had saved in .rm format  anyone know how to get this to play? totem doesnt seem to play it? nor does xine. I've read a lot of websites saying that totem plays everything, but i think i need to get another codec package or something, because when i double click it to open it, it goes to my movie player screen and closes instantly. I'm not sure why.

also, does anyone know if the windows button on my keyboard has a default use for anything in ubuntu?  it doesnt appear to.

thanks

---

### Post by wheredidrealitygo on 2007-10-27
I would recommend downloading a program from the repositories known as VLC. It may be slightly ugly, but it is one of the, if not best itself, program to open media files (at least video files). It contains all of the most popular codecs used to encode video, so that should help you with your .rm file.

You can assign your "Windows" (known as "Super" in Ubuntu) key to do anything :)

---

### Post by mali2297 on 2007-10-27
> **jordank said:**
> I'll have to look more in to wine a bit later.  But recently i was trying to watch a movie i had saved in .rm format  anyone know how to get this to play? totem doesnt seem to play it? nor does xine. I've read a lot of websites saying that totem plays everything, but i think i need to get another codec package or something, because when i double click it to open it, it goes to my movie player screen and closes instantly. I'm not sure why.


I think you need the w32codecs package which is in the Medibuntu repository, see here how to install it:
[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html)

(Xine can also use those codecs, so you don't need to install mplayer.)

---

### Post by jordank on 2007-10-27
i tried to download some required codecs, but upon typing sudo apt-get update, i noticed what appeared to be a bunch of errors in the terminal.  Anyone know if this is normal, and if not, how can i clean this up?

terminal::


Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_CA
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_CA
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_CA
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_CA
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_CA
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_CA
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_CA
  Could not resolve 'archive.ubuntu.com'
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_CA.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_CA.bz2) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_CA.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_CA.bz2) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_CA.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_CA.bz2) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_CA.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_CA.bz2) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_CA.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_CA.bz2) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_CA.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_CA.bz2) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_CA.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_CA.bz2) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz) Could not resolve 'archive.ubuntu.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by SpiritIsReality on 2007-10-27
howdy
looks like you could try this
[http://ubuntuforums.org/showthread.php?p=3615924](http://ubuntuforums.org/showthread.php?p=3615924)

then try to install w32codecs like this?
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)

[http://www.google.ca/search?hl=en&q=linux+%22failed+to+fetch%22+%22could+not+resolve%22&meta=&btnG=Google+Search](http://www.google.ca/search?hl=en&q=linux+%22failed+to+fetch%22+%22could+not+resolve%22&meta=&btnG=Google+Search)

trails

---

### Post by jordank on 2007-10-28
Anyone? is this normal to see when you type sudo apt-get update?

---

### Post by jordank on 2007-10-28
Another question, what can i do with wine?  I still need to get apex running, but i'm not sure how to go about doing that.  Does wine emulate windows? if so, would i, in that case, just install wine (i'm assuming that's just done by the synaptics package manager and selecting wine), then continueing to go download apex from the site? would i download the windows version and install it using wine? (if that's even possible?) or what would be my procedure?    any help appreciated :) thanks

---

### Post by icechen1 on 2007-10-28
> **jordank said:**
> Anyone? is this normal to see when you type sudo apt-get update?

it means it can't connect to the server,try choose a other server in system>administration>software sources.

---

### Post by icechen1 on 2007-10-28
> **jordank said:**
> Another question, what can i do with wine?  I still need to get apex running, but i'm not sure how to go about doing that.  Does wine emulate windows? if so, would i, in that case, just install wine (i'm assuming that's just done by the synaptics package manager and selecting wine), then continueing to go download apex from the site? would i download the windows version and install it using wine? (if that's even possible?) or what would be my procedure?    any help appreciated :) thanks

Only **some** Windows apps. run properly on linux. [http://appdb.winehq.org/](http://appdb.winehq.org/) is a site where you can search if apex is ok.

---

### Post by jordank on 2007-10-28
would it be worth running a virtual machine to get some programs that normally use windows working?  For example, apex, or for gaming?  Would i need a cd/cdkey to have a virtual machine of windows vista?  is it hard to set up?

---

### Post by icechen1 on 2007-10-28
> **jordank said:**
> would it be worth running a virtual machine to get some programs that normally use windows working?  For example, apex, or for gaming?  Would i need a cd/cdkey to have a virtual machine of windows vista?  is it hard to set up?

I don't know,you can do a search on google or in this forum.
I never did this.

---

### Post by jordank on 2007-10-28
alright, i'm going to give wine a try. i tried searching to see if apex was compatible but came up with nothing. Instead i'm just going to try and find out.  After getting wine from synaptics, how do i access it?  does it download to somewhere? to check if it is compatible, would i download the windows version apex and attempt to run that?

---

### Post by icechen1 on 2007-10-28
> **jordank said:**
> alright, i'm going to give wine a try. i tried searching to see if apex was compatible but came up with nothing. Instead i'm just going to try and find out.  After getting wine from synaptics, how do i access it?  does it download to somewhere? to check if it is compatible, would i download the windows version apex and attempt to run that?

after you install it you should see wine menu in application menu,go to configure wine,it will create the files it needs then you are ready to open wine files.
a guide here: [http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

a theme to make wine beautiful : [http://editplus.info/wiki/Running_on_Linux#Windows_Theme](http://editplus.info/wiki/Running_on_Linux#Windows_Theme)
another site here: [http://frankscorner.org/](http://frankscorner.org/)

---

### Post by Maestro23 on 2007-10-28
> **jordank said:**
> alright, i'm going to give wine a try. i tried searching to see if apex was compatible but came up with nothing. Instead i'm just going to try and find out.  After getting wine from synaptics, how do i access it?  does it download to somewhere? to check if it is compatible, would i download the windows version apex and attempt to run that?

This will help with Wine in Ubuntu: [https://help.ubuntu.com/community/Wine?highlight=%28Wine%29](https://help.ubuntu.com/community/Wine?highlight=%28Wine%29)

You can also look into running Windows as a virtual machine, using Vmware or Virtual Box.

VirtualBox: [http://www.virtualbox.org/](http://www.virtualbox.org/)

Vmware: [http://www.vmware.com/download/ws/](http://www.vmware.com/download/ws/)

*If you are running Wine, always rember to check the Wine App DB to see if there are any issues in running a particular Windows program.

---

### Post by jordank on 2007-10-28
Hrmm, i think i may have screwed something up.  I had wine installed before to try to run warcraft, but it didnt work, so i uninstalled warcraft, and uninstalled wine.  Or at least i think i did.  after uninstalling wine it remained in the applications pulldown menu, so i went to system > preferences > main menu, and removed it from there. 

Now after installing wine again, it isn't showing up in the applications menu.  Is there a way to get it back in there? i cant do much to the configuration of wine if i can't reach it.

---

### Post by jordank on 2007-10-28
hrmm. is there a way of completely removing wine so i can try starting this again?

---

### Post by jordank on 2007-10-28
i've tried reinstalling, i've tried uninstalling and installing, i've tried installing from the terminal (sudo apt-get install wine), i read and followed all the steps maestro provided with that website, nothing seems to work.  regardless of what i do 
a) the wine application does not get created in the applications drop down menu
b) i can't open up .exe files with wine
c) when i type winecfg in the console i get various errors.

it looks like it is installed, because i can choose to uninstall it in the add/remove programs window, however nothing about it appears.   I fear this is due to a crude uninstallation of it the first time.  I tried just using the delete button from my filesystem directory.  Wasn't very clean.  If this is the case, how, if there is a way, can i get it back in the applications dropdown menu?  Wine is not liking me right now.

---

### Post by jordank on 2007-10-28
i just noticed in my trash i have things like
a dosdevices folder
drive_c folder
system.reg file
user.reg file
userdef.reg file

these are all from uninstalling wine the first time.  Is there a way to restore these?

---

### Post by icechen1 on 2007-10-28
> **jordank said:**
> i just noticed in my trash i have things like
a dosdevices folder
drive_c folder
system.reg file
user.reg file
userdef.reg file

these are all from uninstalling wine the first time.  Is there a way to restore these?

use completely remove wine in synaptics then in the menu editor see if the wine menu is enabled after installing it and you can try to log out/log in again.

---

### Post by jordank on 2007-10-28
i uninstalled all components of wine, logged out, logged in, then went to the main menu editor.  wine wasn't in there, but i pressed revert.
it reverted all menus to their originals, and then wine appeared.
This is weird though, because it says wine isn't installed on my computer, yet it's now in the drop down menu

when i go to the applications drop down menu, i can hover over the wine application, and another menu sprouts out saying "wine programs" i hover over than and it says warcraft

(because i tried installing warcraft a couple days ago)

there are no configuration files or anything like that, so it seems like half of wine is there, and half not.  I don't know how to restore wine to it's original form

---

### Post by icechen1 on 2007-10-28
> **jordank said:**
> i uninstalled all components of wine, logged out, logged in, then went to the main menu editor.  wine wasn't in there, but i pressed revert.
it reverted all menus to their originals, and then wine appeared.
This is weird though, because it says wine isn't installed on my computer, yet it's now in the drop down menu

when i go to the applications drop down menu, i can hover over the wine application, and another menu sprouts out saying "wine programs" i hover over than and it says warcraft

(because i tried installing warcraft a couple days ago)

there are no configuration files or anything like that, so it seems like half of wine is there, and half not.  I don't know how to restore wine to it's original form

delete the directory called .wine in your home florder(enable show hidden files in view)
install wine again

---

### Post by jordank on 2007-10-28
worked. :) thank you.
Now that it's gone, i have the configure wine option, what were you saying before to do with that?

such a relief.

---

### Post by icechen1 on 2007-10-28
> **jordank said:**
> worked. :) thank you.
Now that it's gone, i have the configure wine option, what were you saying before to do with that?

such a relief.

you can go to configure to configure wine to your fit(i posted something about this in page 4 of this topic).Then you can try to install that program you were trying to install.

---

### Post by jordank on 2007-10-28
you posted:
a theme to make wine beautiful : [http://editplus.info/wiki/Running_on...#Windows_Theme](http://editplus.info/wiki/Running_on...#Windows_Theme)
what does this do? just change the skin of wine?
is it going to cause me a crapload of problems?

---

### Post by icechen1 on 2007-10-28
> **jordank said:**
> you posted:
a theme to make wine beautiful : [http://editplus.info/wiki/Running_on...#Windows_Theme](http://editplus.info/wiki/Running_on...#Windows_Theme)
what does this do? just change the skin of wine?
is it going to cause me a crapload of problems?

no,it just make wine application looks better but i suggest you do that later when everything is good.

---

### Post by jordank on 2007-10-28
how do i check how much harddrive space i have left in ubuntu?

---

### Post by icechen1 on 2007-10-28
> **jordank said:**
> how do i check how much harddrive space i have left in ubuntu?

Disk usage analyzer in applications.

---

### Post by jordank on 2007-10-28
is there something equivalent to a disk defragmenter tha i should you on occasion?
what is a good cd burning program i should look at?
what is Ekiga Softphone?
under my applications pulldown menu i have a programming tab.in it is PyPe.  Is this just python? someone told me pype wasn't python, but they also said python came installed on ubuntu. where is python if that is not it?

---

### Post by wheredidrealitygo on 2007-10-28
the ext3 filesystem (or ext2 depending on your install, but most likely ext3) doesn't fragment, unlike ntfs and fat32, so no defragmentation is required. You'll notice a program called fsck start up once every 20-30 times you start your computer, but it does the checkdisk automatically and then proceeds to boot as normal.

Ekiga softphone is for VOIP with SIPs.

k3b is an excellent burning program, but you need the KDE libraries to run it, if you're sticking solely to gnome then Brasero, and Gnomebaker are both good.

---

### Post by frank002 on 2007-10-28
I also had the same problem with slow Internet browsing. Thankfully, someone here who knows much more than I do suggested I disable IPv6 (Internet Protocol version 6). My problem was solved. To disable IPv6 open a terminal window and type:
 gksudo gedit /etc/modprobe.d/aliases
Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off. Save and you are set. Hope it works for you.

---

### Post by strabes on 2007-10-28
Regarding the sudo apt-get update question: Are you connected to the internet? Are you behind a proxy?

> **jordank said:**
> Another question, what can i do with wine?  I still need to get apex running, but i'm not sure how to go about doing that.  Does wine emulate windows? if so, would i, in that case, just install wine (i'm assuming that's just done by the synaptics package manager and selecting wine), then continueing to go download apex from the site? would i download the windows version and install it using wine? (if that's even possible?) or what would be my procedure?    any help appreciated :) thanks

Wine can get a little complicated, but you can simply install it:```
sudo aptitude install wine wine-utils
```

Then, in a file browser, right click on a .exe file, Click "Open with Other Application," and select "Wine." **If you're lucky **it will work correctly.

---

### Post by jordank on 2007-10-29
what's the difference between
sudo apt-get 
and
sudo aptitude
commands in the terminal?

gnomebaker and brasero? i'll look in to those, but what do you mean when you ask if i'm sticking solely to gnome?  How else could i go? i thought gnome was just a gui program? does that mean i can run different programs for different desktop guis on the same box?
explain

---

### Post by The Tronyx on 2007-10-29
> **jordank said:**
> what's the difference between
sudo apt-get 
and
sudo aptitude
commands in the terminal?

gnomebaker and brasero? i'll look in to those, but what do you mean when you ask if i'm sticking solely to gnome?  How else could i go? i thought gnome was just a gui program? does that mean i can run different programs for different desktop guis on the same box?
explain

Gnome is a GUI program or rather a desktop environment.
[http://en.wikipedia.org/wiki/GNOME](http://en.wikipedia.org/wiki/GNOME)

Different environments behave differently and use different amounts of system resources, are organized differently...  For the GUI aspect of Ubuntu there are tons to choose from such as Openbox, Fluxbox, IceWM, XFCE, KDE, Enlightenment, Gnome....a lot.

The cool thing about desktop environments is that you have the freedom to make you desktop look like whatever you like while still retaining the Ubuntu that you like so much.  For example, this doesn't look much like the out of the box ubunut, but it still is.  This is my desktop using openbox. 

[http://i24.photobucket.com/albums/c45/sigplace/Screenshot-1-1.png](http://i24.photobucket.com/albums/c45/sigplace/Screenshot-1-1.png)

And here is the same computer using Gnome

[http://i24.photobucket.com/albums/c45/sigplace/Screenshot-1.png](http://i24.photobucket.com/albums/c45/sigplace/Screenshot-1.png)

You really can make linux look however you want and that is a lot of fun in itself :)

Stop over to the October Desktop thread and check them all out sometime.

---

### Post by SunnyRabbiera on 2007-10-29
apt get and aptitude are two different applications that roundabout do the same thing.
Really though you will most likely never have to use the terminal much in Ubuntu as synaptic will handle packages for you too.
Just make sure to get some extra repositories just in case it doesnt work, dont worry this is easy to manage:
you seem to know where synaptic is so I will instruct you how to use it if needed.
first to change the repositories, just go up to "settings" once synaptic is up and running
then click on "repositories"
then a new windows will pop up saying "software sources"
(you can also do this via, system> administration> software sources, its practically in the same place where you found synaptic)
anyhow once this window pops up in the "ubuntu software" tab just click off pretty much all the boxes (except the source code one) and if you are having issues with the server just select another one, there is a little box here that says "download from" next to it and depending on what nation you are from it will say it
(example if it says united states then your servers in the united states)
just click on it and you can select others too such as the main server and the "other" servers
just make sure to choose a location that is closest to you (the main servers will do just as fine as the main one by default)
in the "others" section you can choose other servers in your country, or nations close to your country, if american you can select a Canadian one if you wish and if you have a higher connection rate such as highspeed some of the european ones will do such as UK)
after you are done selecting a server you are confident with you can close this window and click the "reload" button.
now you asked about RM files, well there is a linux version of realplayer but its not available by default in ubuntu.
to get it you can get instructions on how to install it here:
[http://ubuntuforums.org/showthread.php?t=587953&highlight=realplayer]("http://ubuntuforums.org/showthread.php?t=587953&highlight=realplayer")

---

### Post by jordank on 2007-10-29
Thanks sunny, that really clears some things up.
however, i've taken an interest in customizing my desktop now. 
I want to get a new background, maybe put some gadgets on the side like the above screenshots, and maybe get a new desktop environment.

Are there advantages to different environments than gnome?
how do i get those gadgets on the side?

---

### Post by jordank on 2007-10-29
also, can i switch freely between desktop environments?

---

### Post by 3rdalbum on 2007-10-29
Some people like Gnome, some people like KDE. I'm not sure that there are really *advantages* to either of those.

You can switch between DEs. Once they are both installed, you can choose them in the "Sessions..." menu item from the login screen. What's really cool is that you can log into one DE, then do a "Switch User" and log into the other DE with the same username, then switch between them with Control-Alt-F7 and Control-Alt-F8.

---

### Post by wheredidrealitygo on 2007-10-29
Most desktop environments have different things going for them. I like Gnome for it's ease of customization, KDE is flashy and colourful, XFCE is very easy on system resources (for older systems), etc. There are more than just these but I don't know much about the rest of them (Fluxbox, Openbox, IceWM, Enlightenment, I'm sure more exist).

If you're looking for customization options, a really good place to start is [Gnome-look]("http://www.gnome-look.org"). AWN provides an amazing dock (if you have a composited desktop, using Compiz for example), there are "desklets" and "screenlets", lots of different things you can do to make your Linux install truly yours.

I would suggest maybe taking a gander at some of the posts in the [Gallery]("http://ubuntuforums.org/g/") on these forums for some ideas as to what you may want to do, and then asking in the "desktop effects and customization" sub-forum category.

---

### Post by jordank on 2007-10-29
how would i go about installing KDE on my computer?
i'm assuming the controls (ctrl alt f8, or whatever you said) are defaults to switch between users?
also, what do most people set their Super buttons to? I've got one set to open a terminal, and i was hoping to set the other to switch between deskspaces, is there a way to toggle between deskspaces?

---

### Post by wheredidrealitygo on 2007-10-29
Download the "Kubuntu-desktop" package from synaptic to install KDE, you'll get the default KDE packages (programs) too.

---

### Post by jordank on 2007-10-29
after downloading the kubuntu desktop package, how do i access the new environment?

---

### Post by jordank on 2007-10-29
also, i noticed that after installing kde, yet i still don't know how to access it, while in gnome i can see a bunch of things that were added.
for example, in the applications drop down, i now have an other tab, and also a system tools tab.  Is there a way to keep all the kde stuff out of gnome, and restrict it only to the kde?

---

### Post by Incense on 2007-10-29
Log out (System - Quit) Then click on Session, select KDE, then log in. It will ask if you want to make it default. Say no, and you're in. Have fun.

---

### Post by jordank on 2007-10-29
> **3rdalbum said:**
> Some people like Gnome, some people like KDE. I'm not sure that there are really *advantages* to either of those.

You can switch between DEs. Once they are both installed, you can choose them in the "Sessions..." menu item from the login screen. What's really cool is that you can log into one DE, then do a "Switch User" and log into the other DE with the same username, then switch between them with Control-Alt-F7 and Control-Alt-F8.

for some reason when i try to switch to kde, it doesn't actually boot up.
while in gnome, i click switch user
then log in using the same user name, but with kde as my session
it stops at a black screen, the boot up screen, and doesn't progress from there. i can
ctrl alt f7/f8 between the two DEs but the kde one never boots.
what's up?

---

### Post by jordank on 2007-10-29
quick question, when i open a terminal, my default line is:
jordan@jordan-laptop:~$:
where exactly is this?
I cant find any directory called jordan-laptop, 
I want to be able to CD my way through to other directories (in hopes of using my compiler) but i dont know where exactly this
jordan@jordan-laptop:~$
location is.
Anyone?

---

### Post by jordank on 2007-10-29
nevermind. found it :)

---

### Post by jordank on 2007-10-29
While trying to run pype, at the bottom it just says:
 Loading menus from /home/jordan/.pype/menus.u.txt
from there it doesnt move, and i'm not allowed to enter any text into the workspace.
Anyone know what the problem here is? Also, is this python? how do i access python if not?
i'm trying to write c++, should pype work for this?
Or, is this something i should look at getting rid of and replacing with a program like jEdit?

---

### Post by SunnyRabbiera on 2007-10-29
> **jordank said:**
> for some reason when i try to switch to kde, it doesn't actually boot up.
while in gnome, i click switch user
then log in using the same user name, but with kde as my session
it stops at a black screen, the boot up screen, and doesn't progress from there. i can
ctrl alt f7/f8 between the two DEs but the kde one never boots.
what's up?

you might not want to do the kubuntu desktop, as in some cases it can mess up.
regular KDE will do you fine.

---

### Post by jordank on 2007-10-29
does that mean i have to uninstall kubuntu-desktop?

---

### Post by SunnyRabbiera on 2007-10-29
its up to you, if you feel its hindering KDE then you can remove it safely.

---

### Post by jordank on 2007-10-29
Here's something i found odd about ubuntu:
When i plug in my external hard drive, nothing happens.
UNLESS
i take my harddrive, plug it in to a windows box, then click "safely remove hardware"
stop the harddrive, then unplug it,
then plug it in to ubuntu, and it registers it as being there.
But if i just unplug it, without clicking unmount volume first, then i can't see it when i plug it back in, and i have to repeat the process with the windows box.
Any way to make my computer see that it is there?

Another question:
Is there a command to force quit applications? in the terminal?

---

### Post by SunnyRabbiera on 2007-10-29
what brand is your external hard drive?

---

### Post by jordank on 2007-10-29
simpletech

---

### Post by SunnyRabbiera on 2007-10-29
ah I see, well that might be an issue with that particular HD manufacturer.
I know external hard drives can work with linux but I know of a few brands that might not work with it.
for an external it might be good for you if you exchanged your current external for a seagate that are very good with linux...
did your external hard drive have to use an installer of some sort?
what is your model?

---

### Post by bhold on 2007-10-29
post deleted wrong thread

---

### Post by jordank on 2007-10-29
no idea of the model, i would guess simpledrive 500gb.
however, i can get it to work, it's just a matter of removing the hardware properly before unplugging it.

---

### Post by Incense on 2007-10-30
> **jordank said:**
> 
Another question:
Is there a command to force quit applications? in the terminal?

You can type 

> xkill

in the terminal, and then just click on the app you want to kill, or you can type 

> killall appname

as well.

---

### Post by jordank on 2007-10-30
still cant see the harddrive,
but does anyone know anything about pype/python?

---

### Post by Incense on 2007-10-30
Plug the hard drive in, and try and reboot your system. That seems to work for me.

---

### Post by 3rdalbum on 2007-10-30
> **jordank said:**
> 
But if i just unplug it, without clicking unmount volume first, then i can't see it when i plug it back in, and i have to repeat the process with the windows box.
Any way to make my computer see that it is there?

So, to clarify: You're not "safely removing" or "unmounting" the hard disk before disconnecting it? If so, then mate, that's a bad idea. Always unmount the disk first, especially on Linux. It gives the operating system a chance to write out any remaining data to the disk. Otherwise, you get an inconsistent state on the disk and this can lead to data corruption.

> Another question:
Is there a command to force quit applications? in the terminal?

I haven't been following the thread, so I don't know if you're using Gnome or KDE. But if you're using Gnome, you can right-click the panel and "Add to Panel...". Then choose the "Force Quit" applet. You will have a little button you can click whenever you need to, to force-quit programs.

Alternatively, you can use the System Monitor in System > Administration > System Monitor.

---

### Post by meanburrito920 on 2007-10-30
about your c++ question, Im pretty sure PyPy is only for Python. I generally use vim or gedit when i work with C or C++. it really is personal preference though. And to get Python to show up in your menu (it is installed by default) right click on the Applications tab on your menu bar, then click 'edit menus'. scroll down to where it says programming and check the box next to python 2.5 and the debugger. it should show up in your menu afterwards.

---

### Post by jordank on 2007-10-30
hrmm, i enabled python 2.5 but it is not what i had in mind for a c++ editor.
It just opens up a terminal.
Is there a default program used in ubuntu that is more like a text editor, but built for writing c or c++ in?
I dont want the terminal type of editor.

---

### Post by wheredidrealitygo on 2007-10-30
the program Gedit (also known as "text editor") if you're in the Applications>Accessories menu, can recognize bash commands (and colour them to differentiate them), I know that, I'm not sure if if it will do the same for C++.

You may want to do just a generic search in Synaptic (for C++ for example) to see if there are any notepad-like programs that would be geared specifically towards it.

---

### Post by Incense on 2007-10-30
> **jordank said:**
> hrmm, i enabled python 2.5 but it is not what i had in mind for a c++ editor.
It just opens up a terminal.
Is there a default program used in ubuntu that is more like a text editor, but built for writing c or c++ in?
I dont want the terminal type of editor.

If you still have kubuntu installed, then I know kate will do C++ syntax highlighting.

---

### Post by meanburrito920 on 2007-10-30
gedit does syntax highlighting as long as the file is already saved in a .c or .cpp format. however, i know a lot of people like to use kdevelop or code::blocks

---

### Post by wheredidrealitygo on 2007-10-30
**To be taken in a friendly manner**: Maybe when you consider yourself only "very new" and not "very, very new", you could mark the thread as solved, and post more issue-specific threads?

It would probably assist in getting a broader range of people that would be able to help you, as opposed to what seems to be the same few people that have stuck with you for 9 pages lol. Our knowledge (well, at least mine) is limited hehe. ;)

Your questioning is very intelligent and I think you're going to be an excellent addition to our community and forums. :KS

---

