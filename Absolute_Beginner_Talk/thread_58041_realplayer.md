---
title: "realplayer"
date: 2005-08-18
forum: Absolute Beginner Talk
---

### Post by sunrex on 2005-08-18
how do i get it, iv tryed sudo apt-get install realplayer ...it didint work

---

### Post by krusbjorn on 2005-08-18
[QUOTE=sunrex]how do i get it, iv tryed sudo apt-get install realplayer ...it didint work[/QUOTE]

[http://ubuntuguide.org/#realplayer](http://ubuntuguide.org/#realplayer)

---

### Post by sunrex on 2005-08-18
> thezombiehunter@thezombiehunter:~$ sudo apt-get install realplayer
Reading package lists... Done
Building dependency tree... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate
thezombiehunter@thezombiehunter:~$

btw i said i did sudo apt-get install realplayer and it didint work

---

### Post by krusbjorn on 2005-08-18
Yeah, I supposed you hadnt activated the extra repositories. Have you?

---

### Post by sunrex on 2005-08-18
also

> thezombiehunter@thezombiehunter:~$ sudo apt-get install gstreamer0.8-plugins
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-artsd gstreamer0.8-caca
  gstreamer0.8-festival gstreamer0.8-jack gstreamer0.8-mad gstreamer0.8-mikmod
  gstreamer0.8-mpeg2dec gstreamer0.8-sid gstreamer0.8-swfdec jackd
  liba52-0.7.4 libjack0.80.0-0 libmikmod2 libmpeg2-4 libsidplay1-c102
  libsndfile1 libswfdec0.3
Suggested packages:
  qjackctl jack-tools meterbridge libjackasyn0 sidplay-base xsidplay
The following NEW packages will be installed:
  gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-artsd gstreamer0.8-caca
  gstreamer0.8-festival gstreamer0.8-jack gstreamer0.8-mad gstreamer0.8-mikmod
  gstreamer0.8-mpeg2dec gstreamer0.8-plugins gstreamer0.8-sid
  gstreamer0.8-swfdec jackd liba52-0.7.4 libjack0.80.0-0 libmikmod2 libmpeg2-4
  libsidplay1-c102 libsndfile1 libswfdec0.3
0 upgraded, 20 newly installed, 0 to remove and 0 not upgraded.
Need to get 1067kB of archives.
After unpacking 3207kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.
thezombiehunter@thezombiehunter:~$

---

### Post by sunrex on 2005-08-18
and

> thezombiehunter@thezombiehunter:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
thezombiehunter@thezombiehunter:~$ 

can somone plz tell me wtf is wrong..plz..

---

### Post by krusbjorn on 2005-08-18
Did you activate the extra repositories and "apt-get update"?

---

### Post by Solomon on 2005-08-18
You know I meant to post a topic regarding RealPlayer so I suppose I'll simply add my question to this topic.

I have installed RealPlayer completely following the directions supplied to me in other area's of the board. It appears under Applications / Sound & Video / Real Player.

However, when I try to open it... well, it never opens. For example, I downloaded an audio book that was in REAL MEDIA format but was unable to open RP. Its there, just doesn't load. Any thoughts?

---

### Post by sunrex on 2005-08-18
..

> thezombiehunter@thezombiehunter:~$ sudo apt-get install nessus
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libgd-gif1 libnessus2
Suggested packages:
  nessusd
The following NEW packages will be installed:
  libgd-gif1 libnessus2 nessus
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 400kB of archives.
After unpacking 1233kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.
thezombiehunter@thezombiehunter:~$
 

GETTING ANNOYED

am i missing some sort of file?

---

### Post by sunrex on 2005-08-18
Did you activate the extra repositories and "apt-get update"?

yes

---

### Post by krusbjorn on 2005-08-18
[QUOTE=Solomon]You know I meant to post a topic regarding RealPlayer so I suppose I'll simply add my question to this topic.

I have installed RealPlayer completely following the directions supplied to me in other area's of the board. It appears under Applications / Sound & Video / Real Player.

However, when I try to open it... well, it never opens. For example, I downloaded an audio book that was in REAL MEDIA format but was unable to open RP. Its there, just doesn't load. Any thoughts?[/QUOTE]

Run realplayer from terminal and tell us if there are any error messages, and what the y say.

---

### Post by sunrex on 2005-08-18
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

---

### Post by krusbjorn on 2005-08-18
[QUOTE=sunrex]deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe[/QUOTE]


When i apt-get realplayer, it downloads it from the backports repository. Activate them too, maybe?

---

### Post by sunrex on 2005-08-18
im running kubuntu btw, do i need to do somthing else?

---

### Post by sunrex on 2005-08-18
> When i apt-get realplayer, it downloads it from the backports repository. Activate them too, maybe? 


em how?

---

### Post by krusbjorn on 2005-08-18
[QUOTE=sunrex]em how?[/QUOTE]

Add these lines to your sources.list file:

```
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

If you had read the "How do I add extra repositories" on the ubuntu guide, you would have had them enabled.

---

### Post by sunrex on 2005-08-18
ill be damned it worked..

thks

right now im running apt-get update couse it said to....but i did before anyway =/

---

### Post by krusbjorn on 2005-08-18
[QUOTE=sunrex]ill be damned it worked..

thks

right now im running apt-get update couse it said to....but i did before anyway =/[/QUOTE]

Yeah, of course it worked ;)

In my first post i said "http://ubuntuguide.org/#realplayer". You know, all the information you needed were there. Just read stuff carefully and things get easier ;)

Good luck in the future.

---

### Post by sunrex on 2005-08-18
> thezombiehunter@thezombiehunter:~$ sudo apt-get install gstreamer0.8-plugins
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-artsd gstreamer0.8-caca
  gstreamer0.8-festival gstreamer0.8-jack gstreamer0.8-mad gstreamer0.8-mikmod
  gstreamer0.8-mpeg2dec gstreamer0.8-sid gstreamer0.8-swfdec jackd
  liba52-0.7.4 libjack0.80.0-0 libmikmod2 libmpeg2-4 libsidplay1-c102
  libsndfile1 libswfdec0.3
Suggested packages:
  qjackctl jack-tools meterbridge libjackasyn0 sidplay-base xsidplay
The following NEW packages will be installed:
  gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-artsd gstreamer0.8-caca
  gstreamer0.8-festival gstreamer0.8-jack gstreamer0.8-mad gstreamer0.8-mikmod
  gstreamer0.8-mpeg2dec gstreamer0.8-plugins gstreamer0.8-sid
  gstreamer0.8-swfdec jackd liba52-0.7.4 libjack0.80.0-0 libmikmod2 libmpeg2-4
  libsidplay1-c102 libsndfile1 libswfdec0.3
0 upgraded, 20 newly installed, 0 to remove and 34 not upgraded.
Need to get 1067kB of archives.
After unpacking 3207kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort. 

its still doing that thou

---

### Post by krusbjorn on 2005-08-18
[QUOTE=sunrex]its still doing that thou[/QUOTE]

I've no idea on that one. Try running synaptic and install the packages from there. Perhaps synaptic will give you a more understandable error message.

---

### Post by sunrex on 2005-08-18
> thezombiehunter@thezombiehunter:~$ sudo apt-get install nessus
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libgd-gif1 libnessus2
Suggested packages:
  nessusd
The following NEW packages will be installed:
  libgd-gif1 libnessus2 nessus
0 upgraded, 3 newly installed, 0 to remove and 34 not upgraded.
Need to get 400kB of archives.
After unpacking 1233kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.
thezombiehunter@thezombiehunter:~$ 

and that

---

### Post by sunrex on 2005-08-18
> thezombiehunter@thezombiehunter:~$ sudo apt-get install flashplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla
thezombiehunter@thezombiehunter:~$ 

...somone plz help me out here =/

---

### Post by krusbjorn on 2005-08-18
[QUOTE=sunrex]...somone plz help me out here =/[/QUOTE]

Try doing [THIS](http://ubuntuguide.org/#extrarepositories) if you STILL havent done it.

---

### Post by sunrex on 2005-08-18
i HAVE done that OK

> deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by krusbjorn on 2005-08-18
You're still missing these lines

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

---

### Post by sunrex on 2005-08-18
thks that installed flash

but now this still wont work

> thezombiehunter@thezombiehunter:~$ sudo apt-get install gstreamer0.8-plugins
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-artsd gstreamer0.8-caca
  gstreamer0.8-festival gstreamer0.8-jack gstreamer0.8-mad gstreamer0.8-mikmod
  gstreamer0.8-mpeg2dec gstreamer0.8-sid gstreamer0.8-swfdec jackd
  liba52-0.7.4 libjack0.80.0-0 libmikmod2 libmpeg2-4 libsidplay1-c102
  libsndfile1 libswfdec0.3
Suggested packages:
  qjackctl jack-tools meterbridge libjackasyn0 sidplay-base xsidplay
The following NEW packages will be installed:
  gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-artsd gstreamer0.8-caca
  gstreamer0.8-festival gstreamer0.8-jack gstreamer0.8-mad gstreamer0.8-mikmod
  gstreamer0.8-mpeg2dec gstreamer0.8-plugins gstreamer0.8-sid
  gstreamer0.8-swfdec jackd liba52-0.7.4 libjack0.80.0-0 libmikmod2 libmpeg2-4
  libsidplay1-c102 libsndfile1 libswfdec0.3
0 upgraded, 20 newly installed, 0 to remove and 34 not upgraded.
Need to get 1067kB of archives.
After unpacking 3207kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort. 

anyway i have a onboard sound card and then soundblaster 24bit live how do i disable the on board sound card?

---

### Post by krusbjorn on 2005-08-18
Now, if you had taken a good look at the link in my first post, both of us would have saved a lot of time.

If you need help on the sound, start another thread. Try to keep your threads on topic. And use the search function. I think there are a couple of threads on the soundblaster around.

---

### Post by sunrex on 2005-08-18
i did, no one is replying on it, its getting annoying

---

### Post by Solomon on 2005-08-18
[QUOTE=krusbjorn]Run realplayer from terminal and tell us if there are any error messages, and what the y say.[/QUOTE]

What do I enter in the terminal to do this?

---

### Post by krusbjorn on 2005-08-18
[QUOTE=Solomon]What do I enter in the terminal to do this?[/QUOTE]

try opening a terminal and type "realplay"

---

### Post by Solomon on 2005-08-18
Ok I opened a terminal and typed "realplay" and then hit enter. I recieved no response in return. Nothing loaded nor did any error message (or ANY message for that matter) appear. Absolutely nothing happend.

---

### Post by sunrex on 2005-08-18
first off to install it type sudo apt-get install realplayer

then go to your menu..in my case KDE menu, then click on the button that says Multimedia and bam u sould see real player

---

### Post by Solomon on 2005-08-18
I've done that. RealPlay is in fact, installed. It appears on my menu. RM files show the RealMedia logo. It should be installed. The fact is, it just isn't working.

---

### Post by krusbjorn on 2005-08-18
If nothing happens when you run it from terminal, my guess is that it is running, but it just doesnt appear in X. Check Applications->System Tools->System Monitor and look for realplay-bin. 

Not that I would know how to solve it if this is the case ;)

---

### Post by Solomon on 2005-08-18
It was running 28 times because of all my attempts to make it run. So, I restarted. Now I go to terminal (I haven't attempted to launch realplayer yet) and type in "realplay" and nothing shows up in terminal. RealPlay does not launch. No messages in terminal. This was the FIRST time I tried to launch it since the restart.

---

### Post by sunrex on 2005-08-18
what are you typing in the terminal?

oh btw how do i get firefox/anything to show advanced html...all the time its all blocked...well alot of times (its not clear its blocks)

---

### Post by krusbjorn on 2005-08-18
Just to let you know, if you start an app from the terminal and nothing happens, everything usually is fine.

And you didnt have to restart. "killall realplay.bin" would have slaughtered those 28 realplayers running ;)

I'm sorry, but I'm a newbie myself...dunno how to help you anymore.

---

### Post by Solomon on 2005-08-18
Can ANYONE help?

---

### Post by Solomon on 2005-08-18
Anyone?

---

### Post by sparkee_boy on 2005-08-18
Take a look at the sound setup forum.  There is an issue with the Elightened Sound system not allowing connections (i.e. Realplayer).  Follow those directions and I think it will get you closer to working.  I'm in the process of getting Realplayer working myself.

---

### Post by sparkee_boy on 2005-08-18
You also have to uncheck "enable sound server startup" in the Sound Preferences (under System menu).  

The sound howto is located at [http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)

After I did those two things, Realplayer worked just fine.

---

### Post by sparkee_boy on 2005-08-19
Okay, after much reading and playing, I used a combination of the above posts, plus info from the following forum: [http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063) 

I was able to leave the "enable sound server startup" enabled, so that I still have all the ubuntu sounds.  Yet Realplayer will still start up.  However, it will not work if there is some other application using sound.  Probably has to do with the OSS usage.  Anyway, so I have success!  Good enough for me at least!

---

