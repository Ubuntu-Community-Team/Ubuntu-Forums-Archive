---
title: "Kubuntu startup freeze, help!!"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by rhcp2go on 2007-07-11
I am a new linux user and have recently installed Kubuntu the newest desktop version. However after doing something in the command line and restarting the screen keeps flashing black with garbled graphics that you can't even make out what they are. By the way I'm using an intel mac, the newest beta version of VMWare Fusion. I can't get past this screen! Can some kind soul please help me out? Much thanks in advance to the person who does! =D

---

### Post by gunksta on 2007-07-12
> **rhcp2go said:**
> I am a new linux user and have recently installed Kubuntu the newest desktop version. However after doing something in the command line and restarting the screen keeps flashing black with garbled graphics that you can't even make out what they are. By the way I'm using an intel mac, the newest beta version of VMWare Fusion. I can't get past this screen! Can some kind soul please help me out? Much thanks in advance to the person who does! =D

I assume then that you are using Feisty?

Could you be more specific about what you did on the CLI?

I don't have any experience with VMWare, but there are people here who do, but it would help if you told us what you did on the CLI.

---

### Post by rhcp2go on 2007-07-12
Yep, I'm using Feisty Fawn. What's CLI? And then I can tell you what I did in CLI, so you guys can hopefully, pray to g*d, help me. Thanks for your reply in advance! :)

---

### Post by rhcp2go on 2007-07-12
Sorry for my utter lack of knowledge! :)

---

### Post by rhcp2go on 2007-07-13
**Somebody**, please help me! How do you unstick a stuck Kubuntu?

---

### Post by mendingo84 on 2007-07-13
CLI stands for Command Line Interface (the Konsole thing :) ). so, what did you do there? :). also, what are your graphics card specifications?

---

### Post by rhcp2go on 2007-07-14
I deleted a lock file in the terminal as recommended by a web site i found from a search i did on google. I did this because, when doing something previous to that it gave me this error, taken out of context:

"some possible causes are that you need to enable TCP/IP for ORBit,or your have NFS locks due to a system crash.(Details-/:IOR file'/tmp/gcofd-cheetahman/tock/ior' not opened successfully"

cheetahman is not me, this quote of the error it gave me was taken off the website i found that told me to delete the lock file, but it gave me the exact same error on my computer. Just instead of cheetahman as the user, it was telepo.

Graphics card I have in my intel mac is: Intel GMA 950


Hope all this helps, cuz i sure need it.


Much appreciation in advance.   :):):)

---

### Post by rhcp2go on 2007-07-14
I forgot to mention, THANK you sooo much for your help mendingo!

---

### Post by rhcp2go on 2007-07-14
I forgot to mention additional specs. for my graphics card are: 64 MB of shared system memory, and the Bus is built-in. Hope this little extra bit helps.  :):):)

---

### Post by gunksta on 2007-07-15
You got me stumped on this one. Considering that Kubuntu is installed in vmware, could you just wipe the image and reinstall?

---

### Post by byrdmeln on 2007-07-15
I first installed Ubuntu about a year and a half ago and during the first month i had to re-install everything a couple of times a day (not that bad but almost) till I figured out a simple rule.

Only type in console commands you find on these forums or in the wiki!  :)

Messing everything up and having to re-install is pretty common for linux newbies, but now I´m down to having to re-install every other month or so, and I usually take that time to check out other distros before coming back to xunbuntu.  Just make sure you back up all your important files regularily and overtime you´ll figure things out.  It used to take me 3 days to get wireless working each install, now I´m down to a cook 3 minutes!

And before the linux hardcore users jump all over me, yes yes yes, I have to re-install cause i´m fooling around with things I shouldn´t be or don´t really understand, it´s not ubuntu´s fault :)

---

### Post by rhcp2go on 2007-07-15
I could but i'd rather not. I have put  a lot of work into this machine already. Here is a pic of the saved crashed state of Kubuntu in VMWare Fusion. Maybe it'll give you a clue as to what's going on. Much thanks in advance!:)

---

### Post by rhcp2go on 2007-07-15
Any ideas byrdmeln for my problem though? =D

---

### Post by byrdmeln on 2007-07-16
Well, if you remember that whenever I run into a problem, my first 3 solutions usually makes things worse before I figure out how to make it better, and that I have to re-install unbuntu every couple of months cause i mess up so bad I have no other choice, then here is what I´d do.  :)

It almost looks like your vmware and your xorg (the linux generic graphic adapter cause I don´t know what it really stands for) are not getting along very well and somehow xorg is trying to display in a bad resolution/hertz (maybe reset by vmware?).  From command line I´d do   *  sudo dpkg-reconfigure xserver-xorg   *  (no asterixs) to reset xorg to something your monitor/graphics card can handle.  

If that didn´t work I´d then remove vmware, then reconfigure xorg to see if that would get me a normal screen, and then re-install vmware ...one of the slightly buggy thing about linux i´ve found is that there can be a higher rate of bad installs compared to windows (though removing programs with all it´s parts is a lot easier then windows).  Second time almost always does the trick.  

Also, where did you get vmware?  Was it from synaptic or the add-install script in ubuntu or from a webpage?  

Byrdmeln

---

### Post by rhcp2go on 2007-07-16
Dude, thanks for your reply! I can't get into the command line from where I'm at I don't think. This problem started when I restarted Kubuntu (from within Kubuntu not from VMWare)  and it gave me this screen basically immediately upon reboot. How would i get into the command line from where i'm at now to do the command you instructed. And if you end up saying i have to reinstall vmware, would it keep my current installed state of changes i've made to kubuntu as of late, as I downloaded a preinstalled version of kubuntu (not the .iso) which has a .vmx file extention? I got VMWare Fusion (for Mac) from the VMWare Fusion Beta site, if that's' what you mean.:):):) Thanks again for your very informative replys everyone. :)

---

### Post by byrdmeln on 2007-07-16
To be honest I don´t know much about vmware except that your run operating systems from within other operating systems.  I tried it with xp to run linux but quite frankly I never saw the point of it, it´s much faster to just duel booting or using a live cd.

How does kubuntu boot up in vmware on a mac?  Is it a real boot or does it boot up with vmware?  If you get a full boot with grub and a splash screen you should be able to get into a console.  1) you can interupt the grup loadup during the countdown by hitting escape to get bunch of options for safe bootups ....those probably let you get into kubuntu but with crappy graphics.  The other way is at the splashscreen where you type in your password, there is an option there for different window manager loadups and one of the choices is a safe terminal ...from which you can type all console commands.

If you can´t do that I probably can´t help you with vmware, but I would question your need for it.  There are linuxs with mac support for live cds  (i know ubuntu used to, they might still but not sure) and you can always duel boot.

And if you had to re-install vmware it should keep all your changes as long as kubuntu is not saved in the same place.

byrdmeln

---

### Post by rhcp2go on 2007-07-17
Ok, thanks for your help. I'm in safe boot it says "root@ubuntu:~#" without quotes of course, but now nothing I type in there boots the system. What for the life of me do i put in their to boot the system? Your assistance much appreciated! Thanks!
:):)

---

### Post by gunksta on 2007-07-17
This might sound kind of crazy, but you've already booted the system. If you followed the advice I see here, you should be booted into run-level 1. Run-level 1 gives you a command line interface and root access, so you need to be really careful. 

* * * Do _**NOT**_ type * * *

```
rm -rf *
```
Because it will eat your system.  :popcorn:

From here you can do anything you want, with full root privileges. 

First, let's make sure you have everything you need. I have never actually used VMware, I am pulling all this together with the help of Uncle Google, and my existing knowledge of X and Ubuntu. I agree with others here. It sounds like X.org configuration is your problem. First, let's make sure you have everything you need.

```
apt-get install --reinstall xserver-xorg-video-vmware
```

Second, I would let Debian try to reconfigure X.org.

```
# dpkg-reconfigure xserver-xorg
```

This should hook you up. It will ask you some questions. When in doubt go with the defaults. I've never configure X.org to run in a VmWare session. It might be worth your time to google this before proceeding, just to avoid any later problems. After that, give it a spin and see how it works.

--andy

---

### Post by rhcp2go on 2007-07-17
T-H-A-N-K  Y-O-U for your help! I began to do as you said, but ran into an itsy bitsy little problem. It says insert the 'Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417) in the drive '/cdrom/' and press enter'. Where do i get the disk labeled this. I have already ordered the live cd, but have not recieved it yet, and am currently running off an .iso off my hard drive. Is there a place where I can download this disk and burn it, then use it as requested by Kubuntu? Thanks!

--------
Jason

---

### Post by skullmunky on 2007-07-18
maybe you already have it - what's that .iso on your hard drive?  

you can download the livecd / installer from 

[http://www.kubuntu.org/download.php](http://www.kubuntu.org/download.php)

while you're in the safe mode command line, if you have internet access, you can make it just download the xwindows reinstall instead of loading it  from the CD.   how do you know if you have internet?  try this:

```

ping google.com

```

you should get a list of the amount of time it takes to contact google, in milliseconds.  if it says "unreachable" or some such, you have no internet, and disregard the rest of this post for now.  :) 

assuming you have internet:

```

sudo nano /etc/apt/sources.list

```

this is the file that contains addresses of places to look for installation files.

here's the beginning of mine:

```

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

```

the first line is looking for the CD.  second two lines look for the online repositories.  if they have a '#' at the beginning they are disabled ("commented out"); delete the # to enable them.

Ctrl-X saves and exits.

now try 

```

apt-get install --reinstall xserver-xorg-video-vmware

```

---

### Post by rhcp2go on 2007-07-18
It says unknown host google.com does that mean Kubuntu is not connected to the internet? Cuz it was in graphical mode b4. Thanks! :):)

---

### Post by ubanchaos on 2007-07-18
well folk im pretty good with this and i also run kunbuntu,ubuntu,and pclinux os and when you boot up the CD u need to check it for errors and ru tryin to dual boot

---

### Post by rhcp2go on 2007-07-18
However I was able to get that list you said but I don't know how to delete the # sign like you said in front of the files to cntl+X "save" it. How do I do that? Thanks again!! You all are amazing by the way with your knowledge! ;)

---

### Post by rhcp2go on 2007-07-18
Yes, ubanchos, I am dual booting Kubuntu in VMWare Fusion as a virtual machine.

---

### Post by ubanchaos on 2007-07-18
well did u check the live CD for errors and what are the specs of your machine

---

### Post by rhcp2go on 2007-07-18
Ok I don't know if it matters, skullmunky, if I was able to delete the # sign or not because I was able to get to a screen where it shows:
 'File Name to Write:  /etc/apt/sources.list_'

without quotes of course. Does it matter if I was able to delete the # sign or not? And if not, what do I do to get past this screen? Thanks a million times over!:):):)

---

### Post by rhcp2go on 2007-07-18
Ubanchaos, I was recommended to bypass the live cd by a certain command in a previous post by skullmunky. please read. :) My specs are Intel Mac Mini 1.83 Ghz 1 GB RAM, Graphics Chipset: Intel GMA 950 w/64 MB of shared system memory.:)

---

### Post by rhcp2go on 2007-07-18
Didn't mean to offend you ubanchaos on the last post saying to "please read". All I was saying was to read the previous posts I did to save us all time. Hope you didn't misundersand. :):)

---

### Post by ubanchaos on 2007-07-18
lol no problems is all good here my friend and ru still having the problem

---

### Post by rhcp2go on 2007-07-18
LOL yes I am still having the problem.

---

### Post by rhcp2go on 2007-07-18
However, I was able to get further than b4. I was able to get it to read the .iso for the necessary command:

apt-get install --reinstall xserver-xorg-video-vmware

Then I was able to further do the command as instructed by gunksta of letting "Debain try to reconfigure X.org" with the command:

apt-get install --reinstall xserver-xorg-video-vmware

After doing this last step Kubuntu gave me a message on the screen saying 

'xserver-xorg postinst warning:  overwriting possibly-customised configuration
     file:  backup in /etc/X11/xorg.conf .20070718203059

Additionally when i go to do the command 'exit' to restart the system, which i hope was the correct thing to do, it exits and restarts, with the same flashing garbled graphics that began all this. So I don't know what do next? Please help a very disgruntled Kubuntu user!:o

---

### Post by rhcp2go on 2007-07-21
Anybody?

---

### Post by gunksta on 2007-07-24
What all do you have in the folder /etc/X11?

Boot into rescue mode.

cd /etc/X11
ls

and give us the output.

If you could somehow post the file labeled xorg.conf in X11, that might help too. Of course, I am assuming (as we all have been) that the problem is in Kubuntu. Technically it the problem could be with vmware. If it is, I am definitely not the person to help.

--andy

---

