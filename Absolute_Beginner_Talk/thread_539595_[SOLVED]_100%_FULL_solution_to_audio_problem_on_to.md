---
title: "[SOLVED] 100% FULL solution to audio problem on toshiba satellite A135 (My model A135"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by lnxmomo on 2007-08-31
Now, for those of you who are looking at this post, you either:

1. Cant hear any sound on your laptop
2. You hear sound but inserting headphone does not mute main speakers

Here is how I solved the situation. It is nothing new however using this method I managed to get sound AND headphone jack to work. Here goes

First download the latest ALSA [driver]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2"), [libs]("ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14a.tar.bz2") and [utils]("ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.14.tar.bz2")

Secondly, we will be compiling the ALSA drivers using the directions from the [wiki]("https://help.ubuntu.com/community/HdaIntelSoundHowto"): 

I will assume that you downloaded the files to the /home/your_username/downloads directory. Please amend if applicable. Also, we will be creating a /usr/src/alsa directory to install the drivers

Install required tools:

```
sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install linux-headers-`uname -r`
```

Creating the directory for installation and copying the downloaded files

```

sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver-1.0.14.tar.bz2
sudo tar xjf alsa-lib-1.0.14a.tar.bz2
sudo tar xjf alsa-utils-1.0.14.tar.bz2
```

Compile and install alsa-driver

```
cd alsa-driver-1.0.14
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
```

Compile and install alsa-lib

```
cd ../alsa-lib-1.0.14a
sudo ./configure
sudo make
sudo make install

```
Compile and install alsa-utils

```
cd ../alsa-utils-1.0.14
sudo ./configure
sudo make
sudo make install

```

After that, I edited my /etc/modprobe.d/alsa-base

```
sudo gedit /etc/modprobe.d/alsa-base
```

Then add this option at the very bottom

```
options snd-hda-intel model=lenovo 
```

Then Reboot your system.

Like I mentioned at the beginning, alot of you would have seen most of this however this is what I did step-by-step to get ny audio AND headphone to work.

NOTICE: Other websites posts and website ask for you to use options snd-hda-intel model=3stack, however, that will get you audio but headphone jack won't work or it will work without muting speaker. However searching online and in bugzilla's I noticed that there was the same problem for  IBM/Lenovo Thinkpads and that someone used it on a Toshiba Satellite and it worked. I hope this is helpfull, I have now got ridden of my vista partition and using 100% Linux :D

Please leave some feedback and tell me if this helped or not.

UPDATE: ALSA 1.0.15 release candidates are out and they are amazing. A lot of work has gone into hda-intel and is working vey well for me. Download it, follow this guide (replace 1.0.14 with whatever version you download) and DONT edit your alsa-base file (/etc/modprobe.d/alsa-base)

UPDATE2: PLEASE, PLEASE, PLEASE use the new ALSA drivers (1.0.15) as they are very stable and you do not need to edit your alsa-base conf file.

UPDATE3: I have tried Hardy Heron and i found that you do not need to do any of this as it has the alsa drivers installed. However, I am willing to help if there are problems with the new OS. Also, the new drivers are 1.0.16, try that.

---

### Post by ubuntukerala1980 on 2007-09-01
nice :guitar:

---

### Post by mrbungle on 2007-09-01
went step by step and got nothing still :(

im using xubuntu and my mixer settings are now empty?  

i can't believe you have to do this much stuff just to get the sound to work :mad:


does it matter what Toshiba satellite a135 model you have?  i have a a135-s2246

any help would be great.

---

### Post by lnxmomo on 2007-09-01
Hmm mrbungle, i tried it on xubuntu and it worked for me.

First, make sure you have rebooted, as that is essential. If that didnt work, try the following

If options snd-hda-intel doesnt work for you try either
```

options snd-hda-intel model=auto
```

OR

```
options snd-hda-intel model=3stack
```

---

### Post by MenZa on 2007-09-01
Which chipset is this? Realtek? SiS?

---

### Post by srt4play on 2007-09-02
Thank you very much for this!  We just picked up a A135-s4666 and this worked good for getting the sound working. I used ndiswrapper for the Atheros wireless and that works beautifully. Suspend/resume works perfect too.

---

### Post by Dr. Nick on 2007-09-05
> **srt4play said:**
> Thank you very much for this!  We just picked up a A135-s4666 and this worked good for getting the sound working. I used ndiswrapper for the Atheros wireless and that works beautifully. Suspend/resume works perfect too.


Just got that exact model, atheros worked out of the box with 7.04, What benefit do you gain from ndiswrapper?

I dont feel like compiling the drivers, so I am jumping to gutsy and see if the newer versions of alsa have the new drivers worked in, if not Ill do it by hand.

thanks for the guide, nice to know it can work.

---

### Post by Dr. Nick on 2007-09-06
Just FYI. The new kernel/alsa version is gutsy(7.10) support the sound card without any workarounds. Almost every feature of this laptop now works out of the box, exception being the media controls.

---

### Post by Hobo Joe on 2007-09-06
I find the best solution is this:
```

sudo asoundconf list
sudo asoundconf set-default-card <cardname>

```

---

### Post by stchman on 2007-09-06
> **mrbungle said:**
> went step by step and got nothing still :(

im using xubuntu and my mixer settings are now empty?  

i can't believe you have to do this much stuff just to get the sound to work :mad:


does it matter what Toshiba satellite a135 model you have?  i have a a135-s2246

any help would be great.

I have the same laptop as you do and the soundcard on that one is not an Intel ICH7, it is an ATI SB450 sound card.

I get my sound to work using this:

[http://www.stchman.com/feisty_tips.html](http://www.stchman.com/feisty_tips.html)

It was relatively easy.  I downloaded the Tribe 4 of Gutsy and everything works out of the box.

---

### Post by stchman on 2007-09-06
> **srt4play said:**
> Thank you very much for this!  We just picked up a A135-s4666 and this worked good for getting the sound working. I used ndiswrapper for the Atheros wireless and that works beautifully. Suspend/resume works perfect too.

The Atheros wireless card is supported by Feisty with just enabling the Restricted driver.  Quite painless.

---

### Post by srt4play on 2007-09-06
> **Dr. Nick said:**
> Just got that exact model, atheros worked out of the box with 7.04, What benefit do you gain from ndiswrapper?

I dont feel like compiling the drivers, so I am jumping to gutsy and see if the newer versions of alsa have the new drivers worked in, if not Ill do it by hand.

thanks for the guide, nice to know it can work.

Wireless was recognized and did work out of the box, but not very reliably.  We had frequent disconnects and poor transfer speeds.  Ndiswrapper solved both of these issues.  Maybe it's specific to our environment but it's nothing fancy just 128-bit WEP. 

[QUOTE=stchman]The Atheros wireless card is supported by Feisty with just enabling the Restricted driver. Quite painless.[/QUOTE]

See above.

---

### Post by stchman on 2007-09-06
> **srt4play said:**
> Wireless was recognized and did work out of the box, but not very reliably.  We had frequent disconnects and poor transfer speeds.  Ndiswrapper solved both of these issues.  Maybe it's specific to our environment but it's nothing fancy just 128-bit WEP. 



See above.

My Atheros 5006EG works perfectly.  I get great transfer rates.  Did you use the restricted drivers for Atheros?

---

### Post by srt4play on 2007-09-06
> **stchman said:**
> Did you use the restricted drivers for Atheros?

They were used by default, the card worked out of the box.

---

### Post by pavan_kuamr00 on 2007-09-07
Thank you very much my laptops sound problem was resolved thank u very much once again

---

### Post by lnxmomo on 2007-09-07
Hey, its good to see people discussing this.

To stchman, when u say your sound works, does that mean speakers AND headphone jack. You see, i tried the resolution that was present in the guide that you linked which got me sound but  when i plug my headphone in, i get sound out of that and the speakers. Does this work with you?

---

### Post by Dr. Nick on 2007-09-07
A gutsy update a few days back knocked my sound out again :( It picked up the card with modprobe, etc but said "no suitable devices" I went to your first post and skipped to the end since i have the newest alsa stuff with gutsy, I simply added the lines to my alsa modprobe file that you show and it works beautifully upon reboot.

Headphones work and when in use disables the built in speakers like it should. Thanks for the guide again

---

### Post by Vic! on 2007-09-11
I have the same problem as lnxmomo i thought my sound was perfect untill i tried to plug in earphones ...the speakers were not muted. i tried the first ibm edit and it didnt work atal then the 3stack and that is what im currently using. my sound card is this Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller if anyone could help me id greatly appreciate it

thanx,
V

---

### Post by sockerbit on 2007-09-12
this works for me all the way up until I get to the alsa-utils part. for some reason i get 

configure: error: this packages requires a curses library

when trying to sudo ./configure
i tried with three different versions of the utils package and get the same error everytime.

---

### Post by Dr. Nick on 2007-09-12
> **sockerbit said:**
> this works for me all the way up until I get to the alsa-utils part. for some reason i get 

configure: error: this packages requires a curses library

when trying to sudo ./configure
i tried with three different versions of the utils package and get the same error everytime.

Do you have build-essentials installed? It looks like your missing a few development packages.

---

### Post by stchman on 2007-09-12
> **lnxmomo said:**
> Hey, its good to see people discussing this.

To stchman, when u say your sound works, does that mean speakers AND headphone jack. You see, i tried the resolution that was present in the guide that you linked which got me sound but  when i plug my headphone in, i get sound out of that and the speakers. Does this work with you?

No, when I plug the headphones in the sound still comes out of the speakers.  When I first installed Feisty the sound did not work at all.  I very rarely use headphones so it is a non issue.

I have read that if you re-compile the ALSA drivers then the headphones thing will work.

---

### Post by Ferosh Jacob on 2007-09-15
I couldnt find a folder for the "lib "  in extracted to the driver folder only. there was no need to install there . I got already installed with the driver , i got it working with the rest of the steps

---

### Post by azadazadi on 2007-09-20
Inxmomo said :
"After that, I edited my /etc/modprobe.d/alsa-base

Code:

sudo gedit /etc/modprobe.d/alsa-base"

Hi Inxmomo, I have tried all the commands you have mentioned but when i came to the last  one that you have edit, that I have put above, it said
" sudo: gedit: command not found" so will you please let me know what should I do. I also have a stallite a135.

Thanks in advance

---

### Post by Dr. Nick on 2007-09-20
> **azadazadi said:**
> Inxmomo said :
"After that, I edited my /etc/modprobe.d/alsa-base

Code:

sudo gedit /etc/modprobe.d/alsa-base"

Hi Inxmomo, I have tried all the commands you have mentioned but when i came to the last  one that you have edit, that I have put above, it said
" sudo: gedit: command not found" so will you please let me know what should I do. I also have a stallite a135.

Thanks in advance

If you are not running gnome you dont have gedit. If you ahve kde subsitute "kate" instead. Or use "sudo nano ...."

---

### Post by azadazadi on 2007-09-21
Thx Dr. Nick.
The music cd is working now however there is no sound for the websites like youtube or any others that I can watch or listen to things. Do you have any suggestions?

I really appreciate your help

---

### Post by JunCTionS on 2007-09-21
:KS I have headphone functionality now :)

thing is, I'm not sure if these instructions are the ones that fixed it :confused: since after doing all the steps it still didn't work but I had to enter Kmix and activate de Headphones in Switches (didn't do it before).
But I guess the steps in this topic must have erased any fixes done previously to get audio in the first place, so they must work from scratch.

Thought you'd like to know that it works on a Toshiba Satellite A135-S4677 

but the headphones don't mute the speakers... tried the three options (lenovo, 3stack and auto). But the volume in the headphones is larger (and if not there's the boost) so I can set the speakers to a low volume.

oh yeah, the headphone's sound control in kmix is listed as the Front Mic.

Also for the n00bs (like me a couple days ago) is good to remark that Kubuntu doesn't have gedit, so use kate instead. the console gives a lot of error messages but it still edits the file.

thanks :)

---

### Post by azadazadi on 2007-09-22
Does anyone know why I cant hear the sound on internet  (in youtube or music websites) but I can when I play a music cd.How can I fix this problem? Anyone?

---

### Post by Dr. Nick on 2007-09-23
> **azadazadi said:**
> Does anyone know why I cant hear the sound on internet  (in youtube or music websites) but I can when I play a music cd.How can I fix this problem? Anyone?


If you can play music cds then your sound card is working and you dont need to follow the steps in this thread. If youtube sound doesnt work then search the forums for "no sound in flash" or similar.

---

### Post by MMosley on 2007-09-25
Just wanted to say thanks.  I followed the instructions in the original post and fixed my headphone problem.  I need to use my headphones all the time so this is a huge help.  Now I can stop using Vista!   =D>

---

### Post by linuxforrealpeople on 2007-09-25
Hi

I get as far as ./configure for the utils and get the following error:

checking for libasound headers version >= 1.0.12... not present.
configure: error: Sufficiently new version of libasound not found.

I would appreciate any help. Thanks.

---

### Post by barmaley on 2007-09-26
Thanks a lot.
I got the same problem with sound ufter linux-headers update on a PC not notebook.
Now it is solved.
The only difference is I did not specify anything for the alsa-driver configure, since it is not intel, but amd and a usual comp.

---

### Post by lnxmomo on 2007-09-26
Hi

Nice to see this works for people. Sorry to those who use KDE as i did not mention to use kate instead of gedit. Maybe next time i will use something universal like nano.

Please note: after using this guide i did a fresh install and decided to use the newer alsa base (1.0.15) release candidates. A lot f work has been put in into HDA-Intel, the soundcard we use in our laptop and it fixed alot of things. Bugs even you have not noticed. I did not even neede to edit my /etc/modprobe.d/alsa-base file.

Hopefully the newer alsa will be available in gutsy.

---

### Post by Badjaccur on 2007-09-29
Confirmed here from behind a noisy Toshiba A200-1CJ, model PSAE0E. No need to compile the drivers when running Gutsy Gibbon. \\:D/

---

### Post by azadazadi on 2007-09-30
I have sound when i play music CDs but when I open youtube there is no sound. I searched  as "no sound in flash" and tried almost every codes I could find but still I dont have sound in youtube or any other websites that have videos or broadcasting radios. Will you please help me with this problem. I use Kubuntu 7.04 Since I am very very new to Linux I dont know if that will make any difference. 
thanks in advance for your help

---

### Post by xircius on 2007-10-02
I followed these instructions and substituted the 1.0.15rc3 files... it seemed to have complied and installed properly, but now alsamixer gives an error message:
alsamixer: function snd_ctl_open failed for default: No such device

and I get a non-existent listing for sound cards using "asoundconf list"

I have a Toshiba U305 laptop with:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

I guess I still need some help. I am updated from 7.04 Feisty to Gutsy. My sound has never worked since clean install of Feisty. I am not going back to MicroShaft, so please... Help???

The speaker/volume icon now has a red circle with a line through it. I have no sound for CDs or .ogg or web-based sound. I have tried these instructions on Feisty, updated Feisty, Gutsy beta, and now the newly released Gutsy. The sound preferences app (gui) used to list HDA device, and now lists absolutely nothing. I guess change in the wrong direction is better than no change :)

Anyway,
Any ideas?

Thanks in advance!

Namaste,
Matt

---

### Post by jtcrew88 on 2007-10-04
i had tried forever to get sound to work under linux on my toshiba satellite a105-s2141 finally did it using this walk through, all i had to change was lenovo to auto on the last step.

---

### Post by shakerlxxv on 2007-10-09
Thanks for a great post. I've got a Toshiba Satellite A135-S4487 and now have the sound and headphones working. After building the latest ALSA version 1.0.15rc3 following the instructions above, I did still need to add 

```
      options snd-hda-intel model=lenovo
```

to /etc/modprobe.d/alsa-base.

The headphones are working, with the front speakers muted; however, its a bit fragile. I can't have the front volume all the way down, it must be partway up and muted. Also if I adjust the volume wheel, the front speakers unmute. Anybody know if this is typical behaviour ?

---

### Post by spsmyth on 2007-10-10
This is great. I have an A135-S4656 and this worked first time out. Also managed to install the mplayer and its plugin in Firefox, and I am listening to my fave radio station.

S.

---

### Post by lazyrussian on 2007-10-15
I got my SB450 card working using this guide and the 1.014 drivers :)

Thank you!

Gutsy is no longer broken :)

---

### Post by drfox on 2007-10-15
> **jtcrew88 said:**
> i had tried forever to get sound to work under linux on my toshiba satellite a105-s2141 finally did it using this walk through, all i had to change was lenovo to auto on the last step.

I was in the same boat! I've installed Gutsy from scratch 2 times. This FINALLY did the trick.

sudo gedit /etc/modprobe.d/alsa-base

Then add this to the bottom of the file

options snd-hda-intel model=auto

Thanks, JT

Larry

---

### Post by RandyNose on 2007-10-20
Dude, you rock.   I recall looking at this back when I installed Feisty, and of course, when I installed Gutsy I had the same problem.  - Your solution I'll bookmark and do the dead.  I did use the "Quick Fix" but found that while I had sound, it was just that, a quick fix. 

Dude, (or dudett)  I'll be happy to bring you a coffee....

---

### Post by mimagabooks on 2007-11-06
Gutsy Seems to have broken this fix for Toshiba a135-s4727. I have worked on two of this model and two of the 4527 as well as a 2234. But so far only the models ending in 27 have broken. 

But after allot of searching I finally found a solution download and install the realtek High Def Driver for linux.


[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

However the only way I and several others have made this work is as follows.

1. Start with a fresh install of Gutsy (k,u,x which ever you like)

2. Run the first update with your package manager do not install other software. (except a compiler if needed)

3. install the Realtek High Def Driver (or as realtek calls it "codec")

This will install the alsa drivers (1.0.14), your sound wheel will seem to work (1-100%).
Each program will control its own volume level.

Note: If you have already done the driver install steps above and it didn't work in gutsy I will say the only way this realtek driver has work for us is a fresh install. 

If there is another way that makes every thing work in gutsy please let me know.

---

### Post by flakblaster on 2007-11-07
This worked great on my A135-S4427. Thanks.

---

### Post by JunCTionS on 2007-11-17
No good :(
the Gutsy *** has ***broken this fix for my A135-S4677.
It didn't work on an "unfresh" install so I went through the process of reinstalling it. but still no good.
Followed the steps posted here (did need to install ncurses and uname to compile, and in the first upgrade couldn't add samba)

please help if you find another fix

P.S.: went through the whole thread again and read some of you say that it's not broken for gutsy anymore, just that it still needed the line at the end of /etc/modprobe/alsa-base . tried this (and the whole fix with the .15 drivers) and it still doesn't work...

---

### Post by JunCTionS on 2007-11-17
oh well... gave on ALSA (didn't even know it was an option before) and welcomed the OSS.
worked for my Satellite A135-S4677 with Gutsy
here's the walkthrough
[http://ubuntuforums.org/showthread.php?p=3768914#post3768914](http://ubuntuforums.org/showthread.php?p=3768914#post3768914)
good luck :)
btw, I need a way to get kmix (or an alternative) to respond to the volume wheel.

---

### Post by jasex on 2007-11-19
Thanks man, I looked around and couldn't find an answer, then it suddenly dawned on me, that re doing the alsa install worked last time... then I found this... Just thought I'd say thanks because in all consideration, this should work in most, if not all HDA Realtek Intel based toshiba's and similar laptops.

For the record, I am running an A105 S4034

 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) By Realtek of course...

---

### Post by Gouz on 2007-11-21
ok I dont know if someone one else have posted it here before me.
but when I red the thread I felt like letting you know
There is one more way to mute the speakers when you plug in the headphones but you will need to do EVERY TIME AND UNDO IT :P

Terminal

aslamixer

then you go to external and press m for mute and the sound of the speakers is off
when you take off your headphones you have to undo it.

Well it is not the best thing to do but it work if you dont have to mess up alot in updates ect :P


PS. my speakers and mic where working just fine until tonight when I did something the alsamixer (I don;t recall what I did so I think that if you put in the correct setting in alsa it will work just fine)

---

### Post by huckem on 2007-11-27
@ Lnxmomo--

YOU ROCK--

I have a Toshiba Satellite A135-S4427 and I have tried all the other howto's I could find... This is the only one that worked!! Thanks!!

-Huckem

P.S.--This is using Gutsy (knl 2.6.22-14-generic)

---

### Post by mercuccio on 2007-11-29
Thanks for your post!

I have a A135-4637 here, with Intel 82801G (ICH7 Family). 

I have installed the 1.0.15 Alsa version, and preserved the original configuration file. The sound is working (as it did before with the Lenovo configuration suggested), but the speakers_ do not_ mute if I plug the headphones. 
I haven't tried to plug a mic yet. 

Any suggestions?

---

### Post by koolkan on 2007-12-09
hi there,
            THANKS A LOT!
            I have 'Toshiba Satellite A135-S4499 laptop' with 
soundcard : 
Vendor  : Intel Corporation
Device  : 82801G (ICH7 Family) High Definition Audio Controller

            This is the only way my sound card came to life on ubuntu gutsy!

---

### Post by wingy on 2007-12-18
Thank you so much, I tried numerous other ways to get this fixed I have an A135-S4487 and your solution was the only one to work. Thank you very very much.

---

### Post by Autumn_Glitch on 2007-12-24
> **lnxmomo said:**
> Now, for those of you who are looking at this post, you either:

1. Cant hear any sound on your laptop
2. You hear sound but inserting headphone does not mute main speakers

Here is how I solved the situation. It is nothing new however using this method I managed to get sound AND headphone jack to work. Here goes

First download the latest ALSA [driver]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2"), [libs]("ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14a.tar.bz2") and [utils]("ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.14.tar.bz2")

Secondly, we will be compiling the ALSA drivers using the directions from the [wiki]("https://help.ubuntu.com/community/HdaIntelSoundHowto"): 

I will assume that you downloaded the files to the /home/your_username/downloads directory. Please amend if applicable. Also, we will be creating a /usr/src/alsa directory to install the drivers

Install required tools:

```
sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install linux-headers-`uname -r`
```

Creating the directory for installation and copying the downloaded files

```

sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver-1.0.14.tar.bz2
sudo tar xjf alsa-lib-1.0.14a.tar.bz2
sudo tar xjf alsa-utils-1.0.14.tar.bz2
```

Compile and install alsa-driver

```
cd alsa-driver-1.0.14
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
```

Compile and install alsa-lib

```
cd ../alsa-lib-1.0.14a
sudo ./configure
sudo make
sudo make install

```
Compile and install alsa-utils

```
cd ../alsa-utils-1.0.14
sudo ./configure
sudo make
sudo make install

```

After that, I edited my /etc/modprobe.d/alsa-base

```
sudo gedit /etc/modprobe.d/alsa-base
```

Then add this option at the very bottom

```
options snd-hda-intel model=lenovo 
```

Then Reboot your system.

Like I mentioned at the beginning, alot of you would have seen most of this however this is what I did step-by-step to get ny audio AND headphone to work.

NOTICE: Other websites posts and website ask for you to use options snd-hda-intel model=3stack, however, that will get you audio but headphone jack won't work or it will work without muting speaker. However searching online and in bugzilla's I noticed that there was the same problem for  IBM/Lenovo Thinkpads and that someone used it on a Toshiba Satellite and it worked. I hope this is helpfull, I have now got ridden of my vista partition and using 100% Linux :D

Please leave some feedback and tell me if this helped or not.

UPDATE: ALSA 1.0.15 release candidates are out and they are amazing. A lot of work has gone into hda-intel and is working vey well for me. Download it, follow this guide (replace 1.0.14 with whatever version you download) and DONT edit your alsa-base file (/etc/modprobe.d/alsa-base)

UPDATE2: PLEASE, PLEASE, PLEASE use the new ALSA drivers (1.0.15) as they are very stable and you do not need to edit your alsa-base conf file.

Everything works fine for me until i get to the step
**"sudo ./configure --with-cards=hda-intel"**
the output I get from the terminal is
[B]"checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/alsa/alsa-driver-1.0.15
checking cross compile... 
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build... 
checking for kernel linux/version.h... yes[/B]
[I][B]checking for kernel linux/autoconf.h... no
The file /usr/src/linux/include/linux/autoconf.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel[/B][/I]
sources (default is /usr/src/linux)."
Before i was getting the error 
[B]checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.[/B]
and had to generate it using this code
**cd /usr/src/linux; make include/linux/version.h**
but that code will not work for** autoconf.h** it gives me the error
**mn@ubuntunavi3:/usr/src/linux$ make include/linux/autoconf.h**
***make: *** No rule to make target `include/linux/autoconf.h'.  Stop.***
Am i just being stupid and missing something here?
I would appreciate any help with this that i can get. thanks.

---

### Post by High Camp on 2007-12-24
> **mimagabooks said:**
> Gutsy Seems to have broken this fix for Toshiba a135-s4727. I have worked on two of this model and two of the 4527 as well as a 2234. But so far only the models ending in 27 have broken. 

But after allot of searching I finally found a solution download and install the realtek High Def Driver for linux.


[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

However the only way I and several others have made this work is as follows.

1. Start with a fresh install of Gutsy (k,u,x which ever you like)

2. Run the first update with your package manager do not install other software. (except a compiler if needed)

3. install the Realtek High Def Driver (or as realtek calls it "codec")

This will install the alsa drivers (1.0.14), your sound wheel will seem to work (1-100%).
Each program will control its own volume level.

Note: If you have already done the driver install steps above and it didn't work in gutsy I will say the only way this realtek driver has work for us is a fresh install. 

If there is another way that makes every thing work in gutsy please let me know.

Ban this user. He's giving out false links. If I erase everything from that link he gave except the actual website it turns out to be a spoof. I'm not dumb enough to download the actual "codec" but I'm sure it's nothing anyone wants on their computers.

People like that really piss me off. Spoofing and phishing websites are such a waste of time, money, and effort.

Bah-humbug!

---

### Post by High Camp on 2007-12-24
> **mrbungle said:**
> went step by step and got nothing still :(

im using xubuntu and my mixer settings are now empty?  

i can't believe you have to do this much stuff just to get the sound to work :mad:


does it matter what Toshiba satellite a135 model you have?  i have a a135-s2246

any help would be great.

Did anyone find a solution for this? The same thing happened to me. I went through and found that in mixer settings there's no slider bar for volume, mic, etc.

Any help would be appreciated.

P.S. Ban users that post fake websites!

---

### Post by bturnip on 2008-01-16
Hello Ubuntu folks!

I've got a Toshiba Satellite A135-S7403.  I tried the above method with 1.0.15 and could not get it to work.  I then started from scratch and tried using the 1.0.14 version referenced in the original post and edited my alsa-base file and the sound works.

---

### Post by psg6801 on 2008-01-27
lnxmomo you are the BOMB!!!! Worked perfectly on my wife's A135  It took me forever to convince her to try dual booting Ubuntu and when the sound didn't work I was in the dawg house. But now she loves it!!! THANKS!!!!

---

### Post by ctcreel on 2008-02-07
This worked for me, but only after downloading the latest [alsa 1.0.16]("http://www.alsa-project.org/main/index.php/Download") driver, lib, and utils.  Follow the directions as specified, but replace the version number with 1.0.16 instead of 1.0.14, or 1.0.14a.

---

### Post by quejaleo on 2008-02-20
Hi all!

I have an ASUS laptop, model A6VC, with Ubuntu 7.1, and I had the same problem: Audio in the laptop speakers, but nothing in the headphones. This is what I did and this worked fine for me:

 I followed the instructions, but with the following changes:

a) I downloaded the version 1.0.16 of these three files (the last I found at this time)
b) At the end, I edited the line 

options snd-hda-intel **model=auto**

Note that I used "auto". "lenovo" did not work for me. :guitar:I restarted and... everything fine!!

Hope it helps somebody!

Gruss,

---

### Post by venkateshk on 2008-03-15
Thanks a lott!!

worked perfectly for me, got Toshiba A135 and I was having the problem with my headphone jack not muting before following this tutorial. Thanks a lot.

---

### Post by omarabdelhaleem on 2008-03-20
Thanks, lnxmomo!:)

---

### Post by jmadero on 2008-04-09
I have used these instructions three times, the first two times worked like a charm (and I forgot to say than you!) but now it's not working. It's the same computer (had to format it a couple times because of other issues...just realized today that I forgot to get sound back on it...it's my girlfriend's computer).

I have no idea what is going wrong since I don't get any errors...the only thing I get is this at the beginning:

Note, selecting libncurses5-dev instead of ncurses-dev


I'm not sure if that would cause a problem or not. Otherwise I am using the newest ALSA drivers (.16), followed your instruction to a T and still nothing :( any advice would be GREATLY appreciated. Thanks again!

---

### Post by Tews on 2008-04-10
Code:

gksudo gedit /etc/modprobe.d/alsa-base

And in the last line of the file, add this line:
Code:

options snd-hda-intel model=vaio position_fix=0

Be sure to replace "model=" to your specific machine ... the "position_fix=0" seemed to be what helped.  Hope it works out for you!

PS.  I have used this fix in both 7.10 and 8.04 Beta LTS without any problems ... also fixed the headphone problem.

---

### Post by jmadero on 2008-04-10
No luck...any other suggestions. I added this to the end of the text file:

options snd-hda-intel model=satellite position_fix=0

Any other help would be appreciated, she's threatening to start using Vista more :(

---

### Post by Tews on 2008-04-10
> **jmadero said:**
> No luck...any other suggestions. I added this to the end of the text file:

options snd-hda-intel model=satellite position_fix=0

Any other help would be appreciated, she's threatening to start using Vista more :(

This is what you want to add ...

> options snd-hda-intel model=3stack position_fix=0

---

### Post by jmadero on 2008-04-10
Same error:

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured."

Any other suggestions? Thanks for helping me along the way

---

### Post by JunCTionS on 2008-05-02
I upgraded to Gutsy then gave the new alsa drivers a try and they work :D
well, except for the headphone jack, which doesn't work at all now.
If anyone has a clue, please reply :)

---

