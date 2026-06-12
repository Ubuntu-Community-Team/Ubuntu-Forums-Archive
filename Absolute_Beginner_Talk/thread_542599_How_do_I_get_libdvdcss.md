---
title: "How do I get libdvdcss"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by playme123 on 2007-09-04
Ive copied a film to my hard drive and when I go to play it, it says I need libdvdcss to play it, ive looked in synaptic, and when I click the box its says to remove it.  Sorry for being such a noob on this but please help:(

---

### Post by hyper_ch on 2007-09-04
(1) Google for "medibuntu"
(2) Add the medibuntu repos to your list
(3) Run this:
```

sudo apt-get update && sudo apt-get install libdvdcss2

```

That's it ;)

---

### Post by playme123 on 2007-09-04
im going to do it now and ill let you know how i get on thanks:KS

---

### Post by mikeyphi on 2007-09-04
> **playme123 said:**
> Ive copied a film to my hard drive and when I go to play it, it says I need libdvdcss to play it, ive looked in synaptic, and when I click the box its says to remove it.  Sorry for being such a noob on this but please help:(

Don't know if this is correct but I suspect libdvdcss is used for viewing DVD - and you are trying to play a film off the hard drive! Try opening one of the installed media players and then opening the film through its menu. If no joy - ask the question again mentioning that you've tried to use 'xyz' movie players.

---

### Post by hyper_ch on 2007-09-04
Ok, if it's no dvd then you need other codecs also :) however getting libdvdcss2 isn't bad to begin with ;)

---

### Post by dragomirov on 2007-09-04
Tell me which player you're using (totem, mplayer, etc.), then it could be helpful add medibuntu repository to your sources.list. From a terminal
```
sudo gedit /etc/apt/sources.list
```
Add the following lines
```

deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

```
Then save it and close
From a terminal:
```

wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -

```
Then open synaptic and try to install libdvdcss2

---

### Post by playme123 on 2007-09-04
ive tried i googled medibuntu how do I add it to my repositery, sorry

---

### Post by playme123 on 2007-09-04
im using totem btw

---

### Post by hyper_ch on 2007-09-04
well, there's this menu entry on the medibuntu homepage called "repository howto" --> instructions are there (or do what dragomirov said)

---

### Post by playme123 on 2007-09-04
ive got libdvdcss2 installed and its still not working

---

### Post by hyper_ch on 2007-09-04
then you need other codecs...

---

### Post by abhilash82 on 2007-09-04
I have installed all the libraries reqired for playing DVDs but still I am not able to play. I have already posted this query here [http://ubuntuforums.org/showthread.php?t=540199](http://ubuntuforums.org/showthread.php?t=540199).
:confused:

---

### Post by RomeReactor on 2007-09-04
Hi. **playme123**, try adding the following codecs:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs
```
In case you're using totem-gstreamer (the default), this will change it to totem-xine, so you can play the DVD menus and use subtitles.

gstreamer and xine are backends to totem, sort of like different sets of codecs to power the main program.

**abhilash82**, in your case open mplayer, right-click on it and select "Preferences", go to the Video tab, and change the driver to **xv  X11/Xv**.

---

### Post by playme123 on 2007-09-04
hi will try it abit later cant get access to that pc thanks

---

### Post by hyper_ch on 2007-09-04
if that doesn't help, install "vlc" --> that player plays almost anything out of the box.

---

### Post by abhilash82 on 2007-09-06
> **RomeReactor said:**
> Hi. **playme123**, try adding the following codecs:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs
```
In case you're using totem-gstreamer (the default), this will change it to totem-xine, so you can play the DVD menus and use subtitles.

gstreamer and xine are backends to totem, sort of like different sets of codecs to power the main program.

**abhilash82**, in your case open mplayer, right-click on it and select "Preferences", go to the Video tab, and change the driver to **xv  X11/Xv**.

Thanks for the info. Mplayer is operational now, but my other players like gxine, totem are giving the same errors. How do I configure these x11 settings globally?

---

### Post by RomeReactor on 2007-09-06
**abhilash82**, [this entry]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_fix_black_windows_during_video_playback") in UbuntuGuide may help you.

---

### Post by abhilash82 on 2007-09-07
> **RomeReactor said:**
> Hi. **playme123**, try adding the following codecs:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs
```
In case you're using totem-gstreamer (the default), this will change it to totem-xine, so you can play the DVD menus and use subtitles.

gstreamer and xine are backends to totem, sort of like different sets of codecs to power the main program.

**abhilash82**, in your case open mplayer, right-click on it and select "Preferences", go to the Video tab, and change the driver to **xv  X11/Xv**.

> **abhilash82 said:**
> I have installed all the libraries reqired for playing DVDs but still I am not able to play. I have already posted this query here [http://ubuntuforums.org/showthread.php?t=540199](http://ubuntuforums.org/showthread.php?t=540199).
:confused:

> **RomeReactor said:**
> **abhilash82**, [this entry]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_fix_black_windows_during_video_playback") in UbuntuGuide may help you.

I have configured all the players as per the link you had given ([How to fix black windows during video playback]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_fix_black_windows_during_video_playback")). I will list down the problems that I face with various players that I have.

**MPlayer** - Plays the DVD correctly without any problems on first run only. If I try to play it again the whole application exits and this repeats every time I try playing DVDs.

**gxine** - Gives same error even after the above configuration - The xine engine failed to start

**Totem** - Gives same error even after the above configuration - Totem could not play 'dvd:/'

After all these attempts I installed **vlc player** and my DVD played for the first time on it. It also followed the pattern of Mplayer that I have described above.

What is the cause of this sudden exit of an application (MPlayer and VLC) when I try to play DVDs? I have also tried to play DVD's when my desktop effects are turned off and have the same result.

---

### Post by hyper_ch on 2007-09-07
that is indeed a strange behaviour...

---

### Post by abhilash82 on 2007-09-07
> **hyper_ch said:**
> that is indeed a strange behaviour...

Yeah the behavior seems to be peculiar and is associated only with these media players. Even after reboot and first dvd play the problem repeats.

---

### Post by BrendanM on 2007-09-07
> After all these attempts I installed vlc player and my DVD played for the first time on it.

VLC FTW

---

### Post by RomeReactor on 2007-09-07
> **abhilash82 said:**
> Yeah the behavior seems to be peculiar and is associated only with these media players. Even after reboot and first dvd play the problem repeats.

You have an Intel video card, correct? If you are using the **i810** driver, try opening the video players from the command line and then open a video file; if you get a "BadAlloc" error, your problem might be related to a bug in the i810 driver ([here]("https://bugs.launchpad.net/bugs/+bugs?field.searchtext=badalloc+intel&search=Search+Bug+Reports&field.scope=all&field.scope.target=") are a few bug reports on it). You can add the following line in xorg, in **Section "Device**, just below the driver:
```
Option "LinearAlloc" "16000"
```
then restart the X server (CTRL+ALT+BACKSPACE).

You could also try changing the video driver in Mplayer to **gl   X11/OpenGL**.

Or you could change the video card's driver to **Intel**, but it seems you can't use desktop effects with it.

---

### Post by abhilash82 on 2007-09-10
> **RomeReactor said:**
> You have an Intel video card, correct? If you are using the **i810** driver, try opening the video players from the command line and then open a video file; if you get a "BadAlloc" error, your problem might be related to a bug in the i810 driver ([here]("https://bugs.launchpad.net/bugs/+bugs?field.searchtext=badalloc+intel&search=Search+Bug+Reports&field.scope=all&field.scope.target=") are a few bug reports on it). You can add the following line in xorg, in **Section "Device**, just below the driver:
```
Option "LinearAlloc" "16000"
```
then restart the X server (CTRL+ALT+BACKSPACE).

You could also try changing the video driver in Mplayer to **gl   X11/OpenGL**.

Or you could change the video card's driver to **Intel**, but it seems you can't use desktop effects with it.
I am able to play DVDs throgh the command line of Mplayer but not through the window interface. Is there any other configuration changes to be done to make it play through the interface itself?

---

