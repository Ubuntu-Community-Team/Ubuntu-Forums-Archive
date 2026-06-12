---
title: "Sigmatel Audio Card Driver"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by vesse on 2007-11-16
Does anyone know where I can find the driver for the STAC 92XX C-Major HD Audio card? I can't find it anywhere. Also, the whole reason I'm switching to Linux is because I'm sick of all the problems I have with windows. Every time I get a computer with windows it seems to eventually crash. My question is, since my laptop just died (I had to reinstall everything with Windows unfortunately), will my NVIDIA 7900 work with Linux? I'll explain. Right now, when I install the XP Driver for the card, I'll restart the computer after installing it, it'll work for a while, and then the screen will go back and when I turn it off and on again the driver isn't installed anymore. Is this a problem with the card, my computer, windows? And will I have this problem with linux?

---

### Post by tyggna1 on 2007-11-17
> **vesse said:**
> Does anyone know where I can find the driver for the STAC 92XX C-Major HD Audio card? I can't find it anywhere. Also, the whole reason I'm switching to Linux is because I'm sick of all the problems I have with windows. Every time I get a computer with windows it seems to eventually crash. My question is, since my laptop just died (I had to reinstall everything with Windows unfortunately), will my NVIDIA 7900 work with Linux? I'll explain. Right now, when I install the XP Driver for the card, I'll restart the computer after installing it, it'll work for a while, and then the screen will go back and when I turn it off and on again the driver isn't installed anymore. Is this a problem with the card, my computer, windows? And will I have this problem with linux?

You won't have that problem in Linux unless you edit the driver options or change something manually (xorg.conf).   The driver isn't modular--so it is only loaded on boot-up and then stays in RAM the whole time the computer is running (unlike in windows where it keeps bouncing it on and off the hard drive).   If there is a problem--it'll just freeze before it boots up.


As for the Sigmatel drivers--try support.dell.com, I know they post the windows drivers for it there, and that they have computers that can do surround sound.   If you can't find it, then the ALSA drivers that come with Linux should do the trick (provided you only have one sound card, and you install the right version of Ubuntu).

---

### Post by MyR on 2007-11-17
it looks like someone here found a solution:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/134351](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/134351)
> I finally got my sound working after a month of searching various posts!

I have the NVidia MCP51 High Definition Audio with the Sigmatel STAC 9200 chip on it. It came with my Gateway MT3421 laptop.

I had given up on sound because everyone on forums had given up, but there's a patch for fixing this sound card on the alsa-bugs site!

Just go here and look for the post with the patch and follow the instructions:
[http://forums.fedoraforum.org/showthread.php?p=868053](http://forums.fedoraforum.org/showthread.php?p=868053)

A couple things:
1...you don't have to remove all alsa packages like he said in step 1. All I did was remove alsa-lib and alsa-utils.
2...the patch file is at the bottom of the post as an attachment.

I hope this works for some of you!

Mike
good luck!
peace

---

### Post by Paradoxfox93 on 2007-11-19
I need the same solution on my mt3422...unfortunately I don't undMT3421ererstand the dfference between fedora code and ubuntu or hwo to do that stuff in ubuntu anyway. Not like I understand how to do much in Ubuntu besides follow directions LOL! Fortunately I have no sensitive data I'm protecting, so  can jack around to my heart's (Or Boredom's) delight and just reinstall.

---

### Post by MyR on 2007-11-19
> **Paradoxfox93 said:**
> ...unfortunately I don't understand the difference between fedora code and ubuntu or how to do that stuff in ubuntu anyway.
let's see if i can give this a shot....

1. in a terminal type
```
sudo aptitude remove alsa-base alsa-utils
```

2. go to [www.alsa-project.org](www.alsa-project.org) and download these files (to your home folder):
alsa-driver-1.0.15rc1.tar.bz2
alsa-lib-1.0.15rc1.tar.bz2
alsa-utils-1.0.15rc1.tar.bz2

..then do
```
sudo mkdir /usr/local/src/alsa/
sudo cp alsa-driver-1.0.15rc1.tar.bz2 /usr/local/src/alsa/alsa-driver-1.0.15rc1.tar.bz2
sudo cp alsa-lib-1.0.15rc1.tar.bz2 /usr/local/src/alsa/alsa-lib-1.0.15rc1.tar.bz2
sudo cp alsa-utils-1.0.15rc1.tar.bz2 /usr/local/src/alsa/alsa-utils-1.0.15rc1.tar.bz2
cd /usr/local/src/alsa/
sudo tar -jxfv alsa-driver-1.0.15rc1.tar.bz2
sudo tar -jxfv alsa-lib-1.0.15rc1.tar.bz2
sudo tar -jxfv alsa-utils-1.0.15rc1.tar.bz2
```

3. go to [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036) and download the file patch_sigmatel.c.patch-1.0.15rc1-simple. Copy the patch to /usr/local/src/alsa using:
```
cd ~
sudo cp patch_sigmatel.c.patch-1.0.15rc1-simple /usr/local/src/alsa/patch_sigmatel.c.patch-1.0.15rc1-simple
```

4. type this :
```
cd /usr/local/src/alsa/
patch alsa-driver-1.0.15rc1/alsa-kernel/pci/hda/patch_sigmatel.c < patch_sigmatel.c.patch-1.0.15rc1-simple.
```

5. do this:
```
cd /usr/local/src/alsa/alsa-lib-1.0.15rc1/
./configure && make && make install
cd ../alsa-utils-1.0.15rc1/
./configure && make && make install
cd ../alsa-driver-1.0.15rc1/
./configure && make && make install
```
If the configure script complains about missing some libraries use synaptic to install them and try again.

6. reboot

7. after rebooting volume may be muted, so use volume controls to enable it

hope this works, good luck!

peace

---

### Post by Paradoxfox93 on 2007-11-21
Okay, I get a few errors.  When I tried to make the utils.  Sudo ./config runs fine but when I sudo make I get:


config.status: WARNING:  alsaconf/po/Makefile.in seems to ignore the --datarootdir setting

more config.status and some other stuff that looks normal then:

make[1]: Leaving directory `/usr/local/src/alsa/alsa-utils-1.0.15/alsactl'
Making all in alsaconf
make[1]: Entering directory `/usr/local/src/alsa/alsa-utils-1.0.15/alsaconf'
Making all in po
make[2]: Entering directory `/usr/local/src/alsa/alsa-utils-1.0.15/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/usr/local/src/alsa/alsa-utils-1.0.15/alsaconf/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/alsa/alsa-utils-1.0.15/alsaconf'
make: *** [all-recursive] Error 1


it remers to 't-ja.gmo'.  There of course, is none in the utils folder.  But there IS a 'ja.gmo'  Any advice on how to move past this?

---

### Post by Paradoxfox93 on 2007-11-21
However, with a few modifications to your instructions, I did get the drivers (hence the patch) and the libraries....and....I HAVE SOUND!!!!!!!!!!!!!!! OMFG!!!! I'M SOOOOO ECSTATIC!!!

That...along with a sucessfull wireless connection!  The Great Milenko & I are doin' the dance of death!!!  The death of my microcrack addiction that is...

Anyway,  I will compile a list of instructions to follow that got me the results I have with my MT3422. In the meantime I'm off to brag to the IT I work with that reccomended Ubuntu.

THANKS TO:

MyR - For translating the patch instructions for a noob like me!

Kevdog - For a great guide on how to manually install ndiswrapper.

Every other Gateway, Sigmatel (Sound), and Realtek (wireless), owner out there who pushed for these solutions!

---

### Post by MyR on 2007-11-21
glad i could help ;]

---

### Post by sirdork on 2007-11-21
I'm getting stuck on this too

> make[1]: Leaving directory `/usr/local/src/alsa/alsa-utils-1.0.15rc1/alsactl'
Making all in alsaconf
make[1]: Entering directory `/usr/local/src/alsa/alsa-utils-1.0.15rc1/alsaconf'
Making all in po
make[2]: Entering directory `/usr/local/src/alsa/alsa-utils-1.0.15rc1/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/usr/local/src/alsa/alsa-utils-1.0.15rc1/alsaconf/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/alsa/alsa-utils-1.0.15rc1/alsaconf'
make: *** [all-recursive] Error 1

---

### Post by MyR on 2007-11-22
i dont have this audio card so i don't think i can be of further help, sorry :/

hopefully Paradoxfox93 will post his/her solution

---

### Post by Paradoxfox93 on 2007-11-29
Update

Patching is not necessary with the alsa-1.0.15 as it is included.  I can confirm this as I can not use the patch and update the driver & library and get sound.

I still get errors with the utils and have absolutely no freakin' clue how to go about resolving it.  Perhaps we should file bug reports on alsa

---

### Post by simono on 2007-12-07
The errors with utils and the message about ja.gmo can be resolved with:
# sudo apt-get install gettext ja-trans


Simon

---

### Post by nikoPSK on 2007-12-07
I think the driver would be there by default... Try this 

asoundconf list

that'll list all the audio devices

asoundconf set-default-card XXX

where xxx is you card. In my case it was "Audigy"

---

### Post by Apotheosis323 on 2007-12-18
I have an MT3422 laptop, gonna give this a shot. hopefully wont be beating my skull against a wall before the days done

---

### Post by finchx6 on 2007-12-20
I've been working on this problem with my MT3421 and I can't get ANY of the things you guys are explaining to work... i got the packages unpackaged in the alsa folder, and thats about as far as I could get.  When I tried compiling, it told me it couldn't create the executables, or something along those lines, and NOW, if I type in the command to list my audio devices available... it lists only, NVIDIA...  which, of course, doesn't work.

There has GOT to be some easy way of fixing this....  this is ridiculous.  I refuse to put Vista back on this laptop, so now I've got a laptop that I can't even listen to music or watch movies on.  yay for gateway...

---

### Post by lvleph on 2007-12-20
> **finchx6 said:**
> I've been working on this problem with my MT3421 and I can't get ANY of the things you guys are explaining to work... i got the packages unpackaged in the alsa folder, and thats about as far as I could get.  When I tried compiling, it told me it couldn't create the executables, or something along those lines, and NOW, if I type in the command to list my audio devices available... it lists only, NVIDIA...  which, of course, doesn't work.

There has GOT to be some easy way of fixing this....  this is ridiculous.  I refuse to put Vista back on this laptop, so now I've got a laptop that I can't even listen to music or watch movies on.  yay for gateway...
If you are using Gutsy, none of the solutions will work anymore. You have to install the backport for the 2.6.22.-14 kernel. That will solve everything, even without installing a new alsa. I have posted this several times, so just look through my posts.

---

### Post by finchx6 on 2007-12-20
I followed your instructions and installed the backport.... still no sound though...

Its strange, I ran the sudo alsamixer command from the terminal, and it tells my exact sound card, and shows it at full volume

I went to the Sound manager and everything was changed from Nvidia to my actual sound card, the STAC9200 Sigmatel..

BUT, when I type asoundconf list in the terminal, it still only lists Nvidia..     any ideas?


Would installing Feisty solve this??? I'm just curious, because I've also noticed I can't even get a working flash player in gutsy.  I was running Edgy back when it was the newest distro, and I didn't run into any problems like this at all.  Of course, I wasn't trying to run it on a laptop either though.

---

