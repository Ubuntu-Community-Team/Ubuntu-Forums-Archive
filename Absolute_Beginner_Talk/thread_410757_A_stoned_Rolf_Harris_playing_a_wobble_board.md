---
title: "A stoned Rolf Harris playing a wobble board"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Bias on 2007-04-16
Hi,

Been struggling with this one for some time now. I've searched the web and the forum but so far have found nothing :(

When I play any music using Totem or Rhythmbox it's badly accompanied by an out of time Rolf on the wobble board.

I have adjusted Alsamixer to no effect other than making it quieter but it's still noticable and the music is obviously quieter as well.

Yesterday I tried playing music with realplayer and it sounds fine, installed VLC and this also sounds fine.

I'm guessing this is down to a Totem/Rhythmbox shared plugin but which one(s)?

I'm using a soundblaster card, Device Manager tells me it's an SB Live! EMU10k1, I found a patch for alsamixer which referenced this in Synaptic and have installed that (ld10k1 and liblo10k1-0) to no avail.

If any of you kind people have any suggestions as to how to fix this or could point me in the right direction it would be appeciated.

Thanks for reading my waffle.

Nick.

---

### Post by ComplexNumber on 2007-04-16
i have exactly the same sound card as you, but i don't use either totem or rhythmbox. i use vlc instead of totem because totem still seems to have issues, especially when used with gstreamer(ie totem-gstreamer) instead of xine(ie totem-xine), and exaile is better than rhythmbox (IMO).
i kow what you mean about the "wobble baord" sound, but i've never experienced it (or at least, i can't remember if i have).

---

### Post by ubukool on 2007-04-16
Hi Nick,

Have you tried the Listen Music player for GNOME?  It's just great, as full featured as Amarok but with that wonderful GNOME simplicity and straightforwardness.

I hope you get rid of Rolf soon.

Check it out!

Kev

---

### Post by Bias on 2007-04-16
Hi ComplexNumber and ubukool,

Thanks for the replies, decided to try both of your suggestions and failed with both :)

ComplexNumber,

I found the dapper release of exaile exaile_0.2.8_i386dapper.deb, doesn't seem to be a 2.9 version for dapper, Ran the install and it all reported as ok. ran it from the menu and nothing happened so tried in terminal and got the following:-

bias@Number6:~$ exaile
Traceback (most recent call last):
  File "/usr/bin/exaile", line 61, in ?
    from xl import *
  File "/usr/share/exaile/xl/tracks.py", line 18, in ?
    import common, media, db, config, trackslist
  File "/usr/share/exaile/xl/media.py", line 19, in ?
    import mutagen, mutagen.id3, mutagen.flac, mutagen.oggvorbis
ImportError: No module named oggvorbis


Unfortunately I have no idea where to go from here. Any ideas? Any one!

----------------------------------------------------------------------------------------------------------

ubukool,

Found this package listen-0.5.tar.bz2 and extracted to a directory on my desktop. Tried the instructions in the install file but on step one i just get:-

bias@Number6:~$ make clean
make: *** No rule to make target `clean'.  Stop.

I suspect i am just doing something stupid here but have no idea what. Any suggestions would be appreciated.

Thanks,

Nick.

---

### Post by ComplexNumber on 2007-04-16
**Bias**
this bit isn't a solution or anything, but can you fire up a package called alsamixer(its in the repos), and if the bass and treble controls aren't shown, go into File then Properties in the menu and tick bass and treble. do you find that bass and treble have no effect? mine was like that at onetime. 
i then did something(which i can't remember) and the problem was rectified.

the ogg vorbis error is probably because  you haven't got the libvorbis library installed.

---

### Post by Bias on 2007-04-16
Hi ComplexNumber, thanks for getting back to me.

Running alsamixer I do not have base and treble controls, used to have them before installing lib10k1 and liblo10k1-0 for the sound card. I do not have a File menu (I do not have any menus) In alsamixer.

Checked in Synaptic and there is not an entry that is just libvorbis library. I do have and have reinstalled just this minute :-

libvorbis0a
libvorbisenc2
libvorbisfile3
python-pyvorbis

This has not made a difference

There are some Ruby and ocaml libraries that are not installed but I'm not sure if these are the ones you are refering to?

Thanks,

Nick.

---

### Post by ComplexNumber on 2007-04-16
> **Bias said:**
> Hi ComplexNumber, thanks for getting back to me.

Running alsamixer I do not have base and treble controls, used to have them before installing lib10k1 and liblo10k1-0 for the sound card. I do not have a File menu (I do not have any menus) In alsamixer.

Checked in Synaptic and there is not an entry that is just libvorbis library. I do have and have reinstalled just this minute :-

libvorbis0a
libvorbisenc2
libvorbisfile3
python-pyvorbis

This has not made a difference

There are some Ruby and ocaml libraries that are not installed but I'm not sure if these are the ones you are refering to?

Thanks,

Nick.
you should have the bass and treble controls for the sb live sound card. that was part of the problem(as it was with me at one time), and thats one of the symptom as to why the sound was is depreciated in quality.
my haunch is that your onboard sound card (ie the one thats built into the motherboard) is somehow conflicting with the sb live. 
-go to your BIOS and disable the inbuilt sound card. 
-then go to alsa mixer and turn the AC97 volume(it should be at the very far end of the controls in alsamixer. if it isn't, go into preferences and tick the switch so that it shows up) right down
-in alsamixer, go to Preferences, and tell me which devices are ticked?
-right click on the volume applet on the panel, select 'open volume control'. then go to File then Preferences in the menu. then select the sb live card in 'change device'.
-you may need to do a reboot.

just install all those packages. it won't do any harm. you only probably need the 1 of the first 3 anyway and perhaps the python-vorbis package.

---

### Post by Bias on 2007-04-16
Hi again,

Installed the Gnome-Alsamixer, this does have a file menu but there are no options for base or treble in preferances or properties, rather oddly it does not show the SB card but eMicro 28028 the other alasamixergui shows the SB and the eMicro. Something's not right.

Nick,

---

### Post by ComplexNumber on 2007-04-16
> **Bias said:**
> Hi again,

Installed the Gnome-Alsamixer, this does have a file menu but there are no options for base or treble in preferances or properties, rather oddly it does not show the SB card but eMicro 28028 the other alasamixergui shows the SB and the eMicro. Something's not right.

Nick,
do you disable the onboard sound card? i dont really think its a good idea to have more than 1 active at any time. 
when you open voluem control from your apple on the panel, you should have should have something thats similar to the screenshot when you click on change device.


also, have a look in syanaptic and install the following (see 2nd screenshot):
alsatools
awefx
ld10k1
liblo10k1

---

### Post by Bias on 2007-04-16
> **ComplexNumber said:**
> you should have the bass and treble controls for the sb live sound card. that was part of the problem(as it was with me at one time), and thats one of the symptom as to why the sound was is depreciated in quality.
my haunch is that your onboard sound card (ie the one thats built into the motherboard) is somehow conflicting with the sb live. 
-go to your BIOS and disable the inbuilt sound card. 
-then go to alsa mixer and turn the AC97 volume(it should be at the very far end of the controls in alsamixer. if it isn't, go into preferences and tick the switch so that it shows up) right down
-in alsamixer, go to Preferences, and tell me which devices are ticked?
-right click on the volume applet on the panel, select 'open volume control'. then go to File then Preferences in the menu. then select the sb live card in 'change device'.
-you may need to do a reboot.

just install all those packages. it won't do any harm. you only probably need the 1 of the first 3 anyway and perhaps the python-vorbis package.


Hello again,

Weirder and weirder :)

The inbuilt soundcard is disabled in BIOS and always has been!

Using Gnome-alsamixer, the only one with any menus.

There is no AC97 Volume, in preferences there is not a way to make this show up.

In Preferences there is only eMicro 28028, there is no other choice.
I have no Volume applet to right click on so can not follow your instructions any further.

Sorry,

Nick.

---

### Post by Bias on 2007-04-16
Looks like we are overlapping a bit :)

Thanks for the pics, my alsamixer looks noting like it at all, I'll try installing the other items and see what happens.

Thanks,

Nick,

---

### Post by ComplexNumber on 2007-04-16
ok, install those drivers and packages that are shown in the 2nd screenshot above. emu10k is the driver for your sb live sound card, and thats what you want.

---

### Post by Bias on 2007-04-16
Hi,

Can't find anything that looks like your version of alsamixer :( do you know what command line opens it? Might give me a clue, not probable but you never can tell :)

I already have emu10k installed, it was after installing that that I lost all the bass and treble controls from my version of alsamixer, The install did not resolve the Rolf problem.

Thanks,

Nick.

---

### Post by ComplexNumber on 2007-04-16
its just called 'gnome-alsamixer'.

EDIT: i forget to mention. that wasn't alsamixer in the 1st screenshot. that was the applet volume control. my alsa mixer looks like this:

---

### Post by Bias on 2007-04-16
Ahh, thanks for that, I also have gnome alsamixer + a few others :) mine looks like this.

Still can't see how to get into that other screen though. Still at least we are on the same page :)

Nick.

---

### Post by ComplexNumber on 2007-04-16
thats really weird that your sound card isn't showing up.....at all. you've got the right drivers, you've disabled the onboard sound card.....but its still not showing :confused:. sound problems can sometimes be a nightmare to solve.
i wonder if its something to do with alsa. 

1) just having a look through synaptic here. install the ones out of the following that you haven't already got installed:
alsa-base
alsa-source
alsa-ultils
gstreamer0.10-alsa
libesd-alsa0
mpg123-alsa
alsa-oss

2) go to main menu -> system -> preferences -> sound. does your 1st and 2nd tab look like the following in the screenshot.

3) in the devices tab in the sound applications (see 2), above), have a look through the combo box thingy and see what devices it shows.

4) in the sounds tab, at the bottom it allows you to select your default card. what options does it give you?

---

### Post by Bias on 2007-04-16
Thanks again, you are very patient :)

1) installed/reinstalled all the packages except mpg123-alsa which I could not find. I instaled mpg123-esd instead (assuming a typo, let me know if I'm wrong there).

2) Looks vaguely like it except i have no devices tab.

3) Could not do this as no devices tab.

4) The only option here is the one shown.


I have checked in system/device manager and this calls the soundcard SBLive! 5.1 eMicro 28028, so it looks like Gnome alsa mixer is showing the correct card it just calles it eMicro28028 instead.

---

### Post by ComplexNumber on 2007-04-16
the fact that it says "unknown" whereas mine says "CT4830" must mean something significant. i've just googled CT4830 and it claims that its the driver. i thought that emu10k was.

i don't know why its calling it emicro. i guess  that its not calling it emicro at all, but that its just simply not recognising sb live.

no, the mp3123-alsa isn't a typo. theres an mp3123-alsa and an mp3123-esd. maybe because you're using dapper.


just done some searching. [this]("http://ubuntuforums.org/showthread.php?t=2251") thread may give a slight clue.

have you considered upgrading to edgy? that may help to solve the problem.

---

### Post by Bias on 2007-04-16
I suspect it's calling it emicro because it can't fit the full name in, :)

I cant' find an mpg123-alsa or an mp3123-alsa in synaptic, i have removed mpg123-esd though.

Thanks for all your help, I'm going to check the suggested thread then walk away from it till tomorrow evening, feel like I've been going round in circles for too long so time to step back.

Thanks again.

Nick.

---

### Post by ComplexNumber on 2007-04-16
actually, i think the emicro thing is the OSS mixer version of sb live. the one that should be being used is the alsa mixer. why, i don't i've jsut had a look through synaptic. these packages may help:
libasound2
linux-sound-base

---

### Post by Bias on 2007-04-16
Know what you mean there. Thanks for all the ideas so far.

---

### Post by ComplexNumber on 2007-04-16
> **Bias said:**
> Know what you mean there. Thanks for all the ideas so far.
i've edited my last post and added some packages to install. try a reboot after you've installed them (just in case).

solving sound problems can sometimes be longwinded.

EDIT: i now think thats its using OSS(the old outdated sound server) instead of alsa, and thats the problem.

---

### Post by ubukool on 2007-04-17
Hi Nick,

Hopefully you can find the 'listen' music player in synaptic.  It's in my repositories, but I'm not sure what version of Ubuntu you're using. (I've got Feisty Beta) so it may not be available for edgy, etc, I'm not sure.   Check it out and see because it sure beats untaring and all that configure/install stuff.

Best wishes,

Kev

---

### Post by ComplexNumber on 2007-04-17
> **ubukool said:**
> Hi Nick,

Hopefully you can find the 'listen' music player in synaptic.  It's in my repositories, but I'm not sure what version of Ubuntu you're using. (I've got Feisty Beta) so it may not be available for edgy, etc, I'm not sure.   Check it out and see because it sure beats untaring and all that configure/install stuff.

Best wishes,

Kev
Listen is the repos, but the music player is not the problem ;)

---

### Post by Bias on 2007-04-17
> **ComplexNumber said:**
> i've edited my last post and added some packages to install. try a reboot after you've installed them (just in case).

solving sound problems can sometimes be longwinded.

EDIT: i now think thats its using OSS(the old outdated sound server) instead of alsa, and thats the problem.

Hi ComplexNumber,

Thanks for sticking with this :) I have checked those packages and they are already installed, I re-installed and rebooted, it's still the same.

I'm not sure the issue is with the soundcard, as I said in the original post both Realplayer and VLC media player work fine. It's only Totem and Rhythmbox that have the problem. I'm not to bothered about totem but i like the functionality of Rhythmbox and would like to be able to use it.

Thanks again,

Nick.

---

### Post by Bias on 2007-04-17
> **ubukool said:**
> Hi Nick,

Hopefully you can find the 'listen' music player in synaptic.  It's in my repositories, but I'm not sure what version of Ubuntu you're using. (I've got Feisty Beta) so it may not be available for edgy, etc, I'm not sure.   Check it out and see because it sure beats untaring and all that configure/install stuff.

Best wishes,

Kev

Hi ubukool,

I'm on Dapper, searching synaptic does not show anything called listen, would you know which repository it is in and/or what command line calls it? If it works and has the functionality I am looking for then I'm happy to dump rhythmbox but from what I've seen so far it looks the most useable package, just a shame listening to it makes me wanna grow a beard and call everyone cobber :)

Thanks,

Nick.

---

### Post by jvc26 on 2007-04-17
```

sudo apt-get install listen

```
Should install listen for you (presuming you have all the repos which are standard with ubuntu enabled)
Ill

---

### Post by Bias on 2007-04-17
> **Illuvator said:**
> ```

sudo apt-get install listen

```
Should install listen for you (presuming you have all the repos which are standard with ubuntu enabled)
Ill


Thanks for that but it didn't work, can't find the package, as far as I know I have all the standard repositories avbailable, have even added a couple. Would you know which repositoriy it is in?

Thanks,

Nick.

---

### Post by ComplexNumber on 2007-04-17
> **Bias said:**
> Hi ComplexNumber,

Thanks for sticking with this :) I have checked those packages and they are already installed, I re-installed and rebooted, it's still the same.

I'm not sure the issue is with the soundcard, as I said in the original post both Realplayer and VLC media player work fine. It's only Totem and Rhythmbox that have the problem. I'm not to bothered about totem but i like the functionality of Rhythmbox and would like to be able to use it.

Thanks again,

Nick.
the strange thing is is that you and i have the same sound card, yet i have the facility to have bass and treble, whilst you dont. that means that something is not right. 
 i think the underlying problem is its something to do with your soundcard using OSS sound interface instead of alsa mixer.....most probably. i think that when the underlying problem is rectified, then it will work equally as well on all applications. 

btw do you have totem-xine and libxine installed?

---

### Post by Bias on 2007-04-17
Hi,

I checked those packages (totem-xine and libxine), I don't have totem-xine and couldn't find libxine so I probably don't have it either :)

I do now have the base, treble and AC97 controls, as I lost base and treble when I installed ld10k1 and liblo10k1-0 I uninstalled these packages, following a reboot I now have then, re-installing them gets rid of the extra controls (had to check) those two packages are currently uninstalled. However the AC97 control moves but does not seem to do anything, haven't been able to determine if base or treble effect the sound so probably not. Rolf is stil off his head however :(

Is this a step forward or a step back? :)

Nick

---

### Post by ComplexNumber on 2007-04-17
> **Bias said:**
> Hi,

I checked those packages (totem-xine and libxine), I don't have totem-xine and couldn't find libxine so I probably don't have it either :)

I do now have the base, treble and AC97 controls, as I lost base and treble when I installed ld10k1 and liblo10k1-0 I uninstalled these packages, following a reboot I now have then, re-installing them gets rid of the extra controls (had to check) those two packages are currently uninstalled. However the AC97 control moves but does not seem to do anything, haven't been able to determine if base or treble effect the sound so probably not. Rolf is stil off his head however :(

Is this a step forward or a step back? :)

Nick
i had some problem where i could get no sound apart from apainful monotone. i switched the AC97 control down, and the noise went away. whats more, i could hear my applications as normal.
i'm surprised that you lost the bass and treble when you installed liblo10k1 because i have those installed plus my bass and treble controls working perfectly.
did you try the bass and treble in the apps that seem to be working well (ie realplayer and vlc)?

---

### Post by Bias on 2007-04-18
> **ComplexNumber said:**
> did you try the bass and treble in the apps that seem to be working well (ie realplayer and vlc)?

Hi again,

I did try this and they do not seem to have an effect. I'm thinking it may be time to do a complete removal of everything alsa and then after a reboot reinstall it? Just a long shot but it may redetect the hardware. Unfortunately I will not have time for that today.

Nick.

---

### Post by Bias on 2007-04-29
Hi,

Finally got round to uninstalling all things ALSA, restarted and reinstalled from the list of uninstalled things, with no improvement :( Think I'm just gonna live with it for the time being unless anyone has any suggestions.

thanks for all your help.

Nick.

---

