---
title: "DVD player"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-02-16
I am new to Ubuntu and can't get ANY of my DVD's to play on my ubuntu computer. 
I have tried VLC media player, Movie Player, Xine Movie Player, Totem player and a few others. but none of them work. I would greatly appreciate if you could recommend a program for me and explain all the steps about how to get it and install it etc. Also, if there is any other information you can tell me like about codecs or anything else I need to play DVDs in Ubuntu, please tell me. Thank you.

:popcorn:

---

### Post by Bachstelze on 2007-02-16
Install libdvdcss, libdvdplay, libdvdread and libdvdnav. At least that's what I do and Xine handles DVDs very nicely.

---

### Post by ardchoille42 on 2007-02-16
After you install libdvdread3, run this command:

```

sudo sh /usr/share/doc/libdvdread3/examples/install-css.sh

```

That should install libdvdcss2 for you, you need libdvdcss2 to be able to view encrypted DVD's (most movies).

---

### Post by gigaferz on 2007-02-16
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

also try easy ubuntu
Automatix2

then install grease monkey add on to firefox 2, 

flash  and java are a must

Im basically giving you keywords to do a search , those helped me, im not a linux/ubuntu pro anyway.

Remember VLC

---

### Post by Perfect Storm on 2007-02-16
Ubuntu Restricted tells you howto - [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by forestwalkerjoe on 2007-02-22
i have been trying to figure out how to post a new thread.. some how cant figure that out either.. new to ubuntu.. but has had some smart folks helping me from the FOS forum. 
my issue is odd i think.. i can play dvds now.. but.. the issue is the screens will not show unless you chose a setting that causes the screen to be about 3 by 8 in size.. i have a very large screen and the DVDs play  right in Freespire os.. aka Freedows or FOS.. plays just fine.. in the right size. i cant seem to be able to chose any other video preference that doesnt either.. give me sound and no vid.. vid withsound but sound is behind by 10 or more seconds in the ritht size.. or vid with NO sounds at all. not sure why all this is such a hard deal.. 
I have a Dell 8300 3ghtz chip Intel 4 duel threading.. with half gig ram.. 250 gig drive parttioned with XP , Ubuntu LTS 6, FOS 1.0.13 and my DVD player is a Pioneer DVD BURN RW. 
i havint the first clue how to solve this.. and even some of my friends in FOSF who are very experienced in either OS.. have thrown up their hands and told me to come here. 
any ideas folks? i know maybe you might need more info.. let me know what that is. 
My Yahoo is Alaskaman33
thanks 
FWJ

---

### Post by Steve S. on 2007-02-27
> **forestwalkerjoe said:**
> i have been trying to figure out how to post a new thread.. some how cant figure that out either.. new to ubuntu.. but has had some smart folks helping me from the FOS forum. 
my issue is odd i think.. i can play dvds now.. but.. the issue is the screens will not show unless you chose a setting that causes the screen to be about 3 by 8 in size.. i have a very large screen and the DVDs play  right in Freespire os.. aka Freedows or FOS.. plays just fine.. in the right size. i cant seem to be able to chose any other video preference that doesnt either.. give me sound and no vid.. vid withsound but sound is behind by 10 or more seconds in the ritht size.. or vid with NO sounds at all. not sure why all this is such a hard deal.. 
I have a Dell 8300 3ghtz chip Intel 4 duel threading.. with half gig ram.. 250 gig drive parttioned with XP , Ubuntu LTS 6, FOS 1.0.13 and my DVD player is a Pioneer DVD BURN RW. 
i havint the first clue how to solve this.. and even some of my friends in FOSF who are very experienced in either OS.. have thrown up their hands and told me to come here. 
any ideas folks? i know maybe you might need more info.. let me know what that is. 
My Yahoo is Alaskaman33
thanks 
FWJ

Get this solved yet?  You might try installing Kaffeine...it is a KDE app. but it should run great and I have it be very successful (read "maintenance free") on other non-Ubuntu computers, so may be just what you are looking for.  Install it from Synaptic Package Manager.  Once installed, you run it to play a cd and it will take care of loading other dependancies as well.  Post back if that helps at all...:)

---

### Post by forestwalkerjoe on 2007-02-27
NO i have not gotten this fixed.. no one yet has even tried to help me out.. it has taken intirely too long for answers in here. TO make matters worse.. i DO have Kaffeine.

---

### Post by Steve S. on 2007-02-27
> **forestwalkerjoe said:**
> NO i have not gotten this fixed.. no one yet has even tried to help me out.. it has taken intirely too long for answers in here. TO make matters worse.. i DO have Kaffeine.

Sorry, Joe, just got a DVD player myself to try out...that's why I saw your thread.  Be patient...this forum is rather full these days, but they get the job done.  Good luck!:) 

PS I'll try mine in the next few days and post results if you haven't got it figured out by then...perhaps we can get it figured out.

Anyone else have an answer for forestwalker?

---

### Post by forestwalkerjoe on 2007-02-27
just to be clear.. as said before.. i CAN use the DVD player.. finnaly.. we had to do some improvising on what it needed.. but.. the only trouble seems to be.. if i use the basic defualts.. i get video and sound in correct size.. but with sounds off by nearly 10 seconds. or if i play with the settings.. i get NO sounds correct size.. with good video.. or .. ALL sounds.. correct size as far as i can see but corrupted video.. scrambled. 
or video and sounds.. in the right sync.. but with ONLY a very tiny screen. 
i Must have it with correct size.. speed sync and so forth.. or its useless. in other things.. in FOS.. i have had more troubles.. but most are solved after experienced persons work with me a bit. Ubuntu seems more stable.. easier to interface with.. but with that ONE large flaw.. as i watch movies from NET FLIX near Daily. 
i also have major issues with Video NO sounds on web page video feeds. 
hope you all can help.. ubuntu was one of the first i recieved.. FOS the first installed.. i have not tried but own.. Red hat , Suse , fedora 6 core, Madriva , Puppy.. Damn small and is searching for the ONE that fits me best. ONE that works with all my hardware... is easy to maintain.. and allows me to do what i need and want with out a fight. 
thanks 
FWJ

---

### Post by forestwalkerjoe on 2007-03-09
Ok.. i am frustrated to hell.. i have been asking arround in here for over 3 weeks.. posted and reposted.. questioned and so forth.. Does this FORUM actually DO any thing to answer questions? I wanted UBUNTU to be my primary OS.. but i have some needs.. and the only "TECH support" i get is here.. if this is any indication.. about how well that will be done.. then i guess i should look some place else. not to just kvetch here.. but.. Can SOME ONE please give me a repsonse? my issue is listed above.. as it has been.. and with little or no ACTUAL response other than to say HI.. and WHA? 
I am still hoping some one will SUPPORT my choice.. 
I had Freespire as my Primary.. it still is.. i have UBUNTU LTS as my secondary.. and if som eone would be kind enough to help me with a few glitchy issues... then i would be glad to put that ONE UP.. and NOT just errase it. I also have Distros of Puppy , Damn Small, Mandriva, Redhat , Fedora core 6 , SUSE 10.2 and Slackware 11.
Looking into Dream Linux, PClinux and GNU stuff. I ordered quite a few extra ubuntu disks from your main site thinking i had found the one i wanted to distribute to my workers.. helping me out.. will add others to the Forum and more friends to learn with.. 
NOT helping me will just cuase me to applogize to my crew and staff and Go looking for other OS. 
Thanks
FWJ

---

### Post by arijarot on 2007-07-01
> **ardchoille42 said:**
> After you install libdvdread3, run this command:

```

sudo sh /usr/share/doc/libdvdread3/examples/install-css.sh

```

That should install libdvdcss2 for you, you need libdvdcss2 to be able to view encrypted DVD's (most movies).

I tried this and got this message:

```
sudo sh /usr/share/doc/libdvdread3/examples/install-css.sh
Password:
sh: Can't open /usr/share/doc/libdvdread3/examples/install-css.sh

```

I also couldn't install libdvdcss as it wasn't available / found in synaptics.

DVDs play but they are all scrambled...''==

EDIT:```
sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

```

---

### Post by RomeReactor on 2007-07-01
Hi. You will need the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories and libdvdcss2. From the terminal:
```
gksudo gedit /etc/apt/sources.list
```
and look for this entry:
```
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
```
if it's not there, add it to the end of the file; save it, close Gedit, and enter this:
```
sudo apt-get update
```
now, to install the necessary packages:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs libxine1-ffmpeg libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3 w32codecs mplayer gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```
and finally:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```
**arijarot**, the reason that the **install-css** line failed is because that particular command is intended for Edgy (6.10) and earlier versions; the current version uses the command above (note that it is missing the "examples" folder compared to the one you posted.
Note that this will install **totem-xine**, and if you have totem-gstreamer, it will remove it; the reason for this change is because totem-gstreamer (as far as I know) doesn't play the menus and can't show subtitles on DVDs, while totem-xine can. The addition of w32codecs and mplayer is to ensure that in the event that you come across a file you can't properly play in totem, you can do so in mplayer, and the gstreamer libraries are for MP3 playback on Rhythmbox.

---

### Post by arijarot on 2007-07-01
> **RomeReactor said:**
> Hi. You will need the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories and libdvdcss2. From the terminal:
```
gksudo gedit /etc/apt/sources.list
```
and look for this entry:
```
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
```
if it's not there, add it to the end of the file; save it, close Gedit, and enter this:
```
sudo apt-get update
```
now, to install the necessary packages:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs libxine1-ffmpeg libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3 w32codecs mplayer gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```
and finally:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```
**arijarot**, the reason that the **install-css** line failed is because that particular command is intended for Edgy (6.10) and earlier versions; the current version uses the command above (note that it is missing the "examples" folder compared to the one you posted.
Note that this will install **totem-xine**, and if you have totem-gstreamer, it will remove it; the reason for this change is because totem-gstreamer (as far as I know) doesn't play the menus and can't show subtitles on DVDs, while totem-xine can. The addition of w32codecs and mplayer is to ensure that in the event that you come across a file you can't properly play in totem, you can do so in mplayer, and the gstreamer libraries are for MP3 playback on Rhythmbox.

Thank you, RomeReactor! I'm currently watching my superbit crouching tiger hidden dragon :)

---

