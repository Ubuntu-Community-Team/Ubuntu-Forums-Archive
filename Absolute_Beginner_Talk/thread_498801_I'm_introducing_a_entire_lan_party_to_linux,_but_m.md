---
title: "I'm introducing a entire lan party to linux, but my sound just quit."
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by DeadSuperHero on 2007-07-11
ok so as stated before im showing everyone at about a 50 person lan party linux and its wonders and hopefully pulling more to the linux nation and such. i just got this linux system and i love it and everything has been going well, untill i installed hl2 and played it. it worked fine till i played the game, then it had no sound so i quit, but to my horror i had no sound at all. I dont even get the startup jingle. Ive searched though alsamixer and made sure nothign is muted or such, so please help. I need this fixed by friday , because lets not kid ourselfs , no matter how cool linux looks, who wants a OS with no sound ?

---

### Post by DeadSuperHero on 2007-07-11
---UPDATE---
I plugged my ipod into the input and i can hear it though my headphones in the sound jack but only in the right ear, thought id put this up, if it helped

---

### Post by endlessurf on 2007-07-11
double click on the speaker icon at the top of the screen.  Then go to edit preference and make sure pcm and pcm-2 are checked.  Then make sure that pcm and pcm-2 are not muted and are turned up.

---

### Post by DeadSuperHero on 2007-07-12
thanks i tried that just now, but sadly nothing has changed. I still have no sound. any other ideas?

---

### Post by smoker on 2007-07-12
maybe a silly suggestion, but have you got 'onboard sound' and also a pci sound card fitted, check that the game you installed hasn't changed the soundcard from pci to onboard, you can also sometimes turn off 'onboard' sound in the bios to avoid confusion.

of course, if you don't, well...

---

### Post by Skidpad on 2007-07-12
Which version (of Ubuntu) are you using?  

I know your sound problem occurred while playing HL2, but there are many threads on here with sound problems after doing an upgrade (from Edgy to Feisty).  Perhaps trying one of those solutions may help your situation?   

Sorry I can't be of more help.

edit:*  Good idea Smoker...^^^^*

---

### Post by DeadSuperHero on 2007-07-12
skiddy , i havnt done an update recently so i didnt think that was it, but im using

oh and i thoguht i would throw this out there, i noticed somthing else when the sound stopped
the icons in the top right of my screen switched like deamon,internet,pidgin,and beryl icons went to the far right and the off button and the time and date when to the left of them.

and smoker, how can i change the sound im using? ive tried messing with the device in the sound prefs.

---

### Post by DeadSuperHero on 2007-07-12
oops , im using ubuntu  7.0.4 (sorry forgot to type it in there)

---

### Post by expatCM on 2007-07-12
at the command line type

asoundconf list

and this will show you which sound cards are recognized by your system.


type just asoundconf and you will get a list of options .....

To set one card as the default card type 

asoundconf set-default-card CARD

CARD is the name of the card you found in the list.

---

### Post by smoker on 2007-07-12
>  and smoker, how can i change the sound im using? ive tried messing with the device in the sound prefs.

do you have two sound cards, onboard & PCI card? (if you have duplicate speaker ports at the back that will tell you)

---

### Post by Skidpad on 2007-07-12
I don't think your moving icon problem is related to your sound issue - just coincidental.  You should be able to move them back, and then lock them into place.  (Right click)

---

### Post by DeadSuperHero on 2007-07-12
I do not have duplicate i dont think i have a pci one. 
Oh and i typed soundinfo in the console if Hl2 and it said this > 
Sound Device: Direct Sound
    1 stereo
32768 samples
   16 samplebits
44100 speed
   28 total_channels

---

### Post by DeadSuperHero on 2007-07-12
> at the command line type

asoundconf list

and this will show you which sound cards are recognized by your system.


type just asoundconf and you will get a list of options .....

To set one card as the default card type

asoundconf set-default-card CARD

CARD is the name of the card you found in the list.
__________________ 
I have done this before, it came up with only one ICH5 and still i have no sound.

---

### Post by expatCM on 2007-07-12
Just wondering .... did asoundconf give you any information?

---

### Post by deadgobby on 2007-07-12
[http://ubuntuforums.org/showthread.php?t=418360](http://ubuntuforums.org/showthread.php?t=418360)
 
Gobby

---

### Post by expatCM on 2007-07-12
Ok so it is on-board sound.

If you type 

alsamixer 

at the command line, is the sound card identified in the top left corner?

---

### Post by DeadSuperHero on 2007-07-12
> Just wondering .... did asoundconf give you any information?
when i did that i got this > azac@Axiom:~$ asoundconf
Usage:
asoundconf is-active
asoundconf get|delete PARAMETER
asoundconf set PARAMETER VALUE
asoundconf list

Convenience macro functions:
asoundconf set-default-card CARD
asoundconf reset-default-card
asoundconf set-pulseaudio
asoundconf unset-pulseaudio
and when i type alsamixer
here is the top corner >  Card: Intel ICH5                                                             &#9474;
&#9474; Chip: C-Media Electronics CMI9739 

---

### Post by DeadSuperHero on 2007-07-12
> [http://ubuntuforums.org/showthread.php?t=418360](http://ubuntuforums.org/showthread.php?t=418360)

Gobby
I folowed this but it did nothing =[ thanks anyway

---

### Post by expatCM on 2007-07-12
Ok ... so the system recognizes the sound card and so does alsamixer.  I assume that you have looked at the slider controls in the mixer?

Perhaps you could have a quick look in two places.

First, System / Preferences / Sound.  Look at Sound Events / Sound Playback.  Click Test.  If nothing is heard then click on the rectangle drop down which I assume says Autodetect and select the sound card from the options which appear.

Second, do you have System / Preferences / Multimedia Selector on your menu?  If not you can enable it from the menu manager.  There you will find a test for Default Audio.  Try and see what happens.  When you press test for audio you should hear a continuous tone.

---

### Post by deadgobby on 2007-07-12
open up the terminal and type in this command

xkill esd

and then try the sound again. Are you using ALSA or OSS for sound default?

Gobby

---

### Post by DeadSuperHero on 2007-07-12
I ran the xkill esd gobby and i got this > usage:  xkill [-option ...]
where options include:
    -display displayname    X server to contact
    -id resource            resource whose client is to be killed
    -frame                  don't ignore window manager frames
    -button number          specific button to be pressed to select window
    -all                    kill all clients with top level windows

 Im using Alsa as my default. (im 95% sure)
and i heard no tone in sound in either of the menus.

---

### Post by deadgobby on 2007-07-12
Me bad.. try

killall esd

---

### Post by DeadSuperHero on 2007-07-12
> try killall esd ok i ran it and it just accepted it i guess because nothign came up, but still no sound. i shut down and booted up banshee and played a song to check. but still nothing

---

### Post by Inxsible on 2007-07-12
Try 
```
kill alsamixer
```then to start it up again```
alsamixer
```

---

### Post by deadgobby on 2007-07-12
leave out the try in killall esd.
 Then again you may have done some thing really bad to do what you did.
Gobby

---

### Post by DeadSuperHero on 2007-07-12
> 
Try
Code:

kill alsamixer

then to start it up again
Code:

alsamixer

i cant do the "kill alsamixer" i get this when i try:
> zac@Axiom:~$ kill alsamixer
bash: kill: alsamixer: arguments must be process or job IDs
zac@Axiom:~$ 



---

### Post by DeadSuperHero on 2007-07-12
no haha, i didnt put "try killall esd" i just did killall esd and it does this :
> leave out the try in killall esd.
Then again you may have done some thing really bad to do what you did.
Gobby
which is waht i was trying to say

---

### Post by Inxsible on 2007-07-12
> **Mr. Psychopath said:**
> i cant do the "kill alsamixer" i get this when i try:

You might have to look up the process id of alsamixer. You can do this by```
top
``` Search for alsamixer and see what its process Id is.

then do ```
kill PID
```where PID = the process id for alsamixer

---

### Post by expatCM on 2007-07-12
You may find this interesting

[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

---

### Post by deadgobby on 2007-07-12
Go and double click on the speaker Icon and go to switches and see if the IEC958 is not checked mark.

---

### Post by BobLand on 2007-07-14
Mr Psycopath,
Have you resolved your sound problems?
Here's what worked for me.

[http://ubuntuforums.org/showthread.php?p=3019276#post3019276](http://ubuntuforums.org/showthread.php?p=3019276#post3019276)

bobland

---

