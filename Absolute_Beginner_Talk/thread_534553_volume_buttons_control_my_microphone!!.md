---
title: "volume buttons control my microphone!!"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by rickycodie on 2007-08-25
so i just installed the newest version of alsa and now mygnome volume control only controls my microphone! i right clicked it and went to preferences and there is no master! does anyone have any ideas?

---

### Post by forestpixie on 2007-08-25
try double clicking instead and edit - preferences and seeing if you can add the needed controls

---

### Post by rickycodie on 2007-08-25
nope no master in there either

---

### Post by Majorix on 2007-08-25
```
alsamixer
```

will do I guess. If not post back.

---

### Post by rickycodie on 2007-08-25
i can control it from there but i would really like to use my buttons.  is there a .conf that i can edit to add that option?

---

### Post by jordanmthomas on 2007-08-25
This is just a temporary solution, but you could always bind your multimedia keys to run:
```
"amixer -q set Master 2+ unmute"
```  (change the + to a - for lowering volume)

Also, in volume control preferences did you look to see if you have more than one device you can control?  Mine has two to choose from.

---

### Post by rickycodie on 2007-08-27
yes i have oss and alsa-neither have a master setting.

---

### Post by jordanmthomas on 2007-08-27
hmm...have you tried:
```
sudo alsaconfig
```
to see if maybe it has your card recognized incorrectly?

---

### Post by rickycodie on 2007-08-29
i have not but i will

---

### Post by rickycodie on 2007-08-29
no dice

---

### Post by Wiebelhaus on 2007-08-29
having the same issue..

---

### Post by jordanmthomas on 2007-08-30
If you guys have the same sound card, maybe you should file a bug somewhere or check to see if a bug is already filed.

---

### Post by Wiebelhaus on 2007-08-30
is it the same card? , Nforce4 here , onboard.

Seems to correlate with some program installation , in my case skype.

---

### Post by rickycodie on 2007-08-30
no i have a intel card on a thinkpad. 

btw, no such command as ```
sudo alsaconfig
```

---

### Post by jordanmthomas on 2007-08-30
> **rickycodie said:**
> btw, no such command as ```
sudo alsaconfig
```

oops, that should be
```
sudo alsaconf
```

---

### Post by Wiebelhaus on 2007-08-30
> **jordanmthomas said:**
> oops, that should be
```
sudo alsaconf
```

neither work for me... lol

---

### Post by jordanmthomas on 2007-08-30
My bad again...it seems as though Ubuntu doesn't even have any packages that reference alsaconf in its repos.  To prove I'm not crazy I've attached a screenshot of mine.  :)

I guess the Debian way of doing this would be:
```
sudo dpkg-reconfigure alsa-base
```
and maybe do these too:
```
sudo dpkg-reconfigure alsa-firmware-loaders
```
```
sudo dpkg-reconfigure alsa-tools
```

---

### Post by rickycodie on 2007-08-31
ricky@ricky-laptop:~$ sudo dpkg-reconfigure alsa-base
Password:
Sorry, try again.
Password:
ricky@ricky-laptop:~$ sudo dpkg-reconfigure alsa-firmware-loaders
Package `alsa-firmware-loaders' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: alsa-firmware-loaders is not installed
ricky@ricky-laptop:~$ sudo dpkg-reconfigure alsa-tools
Package `alsa-tools' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: alsa-tools is not installed
ricky@ricky-laptop:~$ 
 no dice

---

### Post by jordanmthomas on 2007-08-31
Since those packages aren't installed, maybe you could install them?  (Of the most interest I'd say is alsa-tools)

---

### Post by rickycodie on 2007-08-31
ok now it's my bad i did just install them and still

no dice

---

### Post by rickycodie on 2007-08-31
hey so the pcm setting is what we're looking for right? 
for some reason it won't control the volume when playing media.
i have the buttons set to control the pcm volume.

---

### Post by rickycodie on 2007-08-31
i just found out that i can control the volume with my scrollwheel. but the buttons still don't controll the volume settings.

---

### Post by rickycodie on 2007-09-04
bump

---

### Post by jordanmthomas on 2007-09-04
What does 
```
amixer scontrols
```
give you?  Any reference to Master in there?

---

### Post by rickycodie on 2007-09-04
no i tried to gedit those files and add a master in there and no help there either.

---

### Post by jordanmthomas on 2007-09-04
gedit?  What is output when you type
```
amixer scontrols
```
into a terminal?

If I know it *might* make it more obvious what exactly is wrong so a solution can be found.

---

### Post by Sensenseppl on 2007-09-04
It's definitely not a good solution for the problem, but I "solved" the problem by unplugging the microphone, switching to OSS and back to ALSA (System->Preferences->Sound) with some rebooting in between. It was a while ago, so I can't be more specific. Sorry.

---

### Post by rickycodie on 2007-09-04
i'm on a laptop so no way to unpug the mic.
as for code:

Simple mixer control 'Headphone',0
Simple mixer control 'PCM',0
Simple mixer control 'Mic',0
Simple mixer control 'Mic Boost',0
Simple mixer control 'Capture',0
Simple mixer control 'Capture',1
Simple mixer control 'Beep',0
Simple mixer control 'Docking Mic',0
Simple mixer control 'Docking Mic Boost',0
Simple mixer control 'Input Source',0
Simple mixer control 'Input Source',1
Simple mixer control 'Internal Mic',0
Simple mixer control 'Internal Mic Boost',0
Simple mixer control 'Speaker',0
ricky@ricky-laptop:~$ 
 there it is!!

---

### Post by jordanmthomas on 2007-09-04
Ok, it looks like alsa is only properly detecting about half of what it should be.

I looked up "no master channel" +alsa  on Google and it seems like it's an issue with your kernel in some way. 

Here's something to try:
Look up your specific sound chip online and see if there are any modules that need to be loaded for it to work properly.  If so, load the modules with lsmod and restart alsa.
Also, I'm sure you've already done it, but make sure you're all the way up to date.  There could have been a goofy kernel update or something.

Other than that, this has got me bested.  :(

---

### Post by rickycodie on 2007-09-05
alright i'll give it a try. thanks for all your help!

---

### Post by Chang An on 2007-09-10
My Media buttons control the int mic instead of the master volume as well.  I remember that they used to work ok awhile ago.  I don't know what happened.

---

### Post by rickycodie on 2007-09-11
neither do we, if you find out post it.

---

### Post by CalvinK on 2007-09-11
> **rickycodie said:**
> nope no master in there either
Goto to gnome-control-center, gksudo gnome-control-center
then to Sound. At the bottom of the page select PCM. That's all.

---

### Post by rickycodie on 2007-09-12
thank you, i have gotten it set to pcm but i would like for the buttons on mt keyboard to control the volume too. as of now i can control it by mousing over and using the scroll wheel. but i would like for my buttons to control the volume.

---

### Post by jordanmthomas on 2007-09-12
I surely hope I wasn't misunderstanding your problem the whole time (feel free to ignore this if it's not what you're looking for).  

If you're satisfied controlling PCM instead of Master (I wouldn't be, but I am confused and tired right now, so I am understanding you're cool with that.  :)  )

Here's exactly what I do to make my multimedia keys do what I want (information robbed from [http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys](http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys)).

First, you'll want to set up a .Xmodmap.  Here's mine (yours will probably be a little different)
```
keycode 160 = XF86AudioMute
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 162 = XF86AudioPause
keycode 144 = XF86AudioPrev
keycode 153 = XF86AudioNext
keycode 164 = XF86AudioStop
```
Now, you're probably wondering how to get these "keycodes", right?

Stolen from the Gentoo wiki, use this command in a terminal:
```
xev | sed -n s/"^.*keycode *\([0-9]\+\).*$"/"keycode \1 = "/p | uniq
```
It looks like voodoo magic or something, but you can trust it (it's really only like three commands piped together).  Anyway, move your mouse into the newly spawned windows and hit each of your multimedia keys you want to bind to an action once.  Remeber the order you pressed them in.  Then, close the window.  Leave your terminal open (you'll want that output in a second).

Open up gedit with an Alt + F2 followed by:
```
gedit ~/.Xmodmap
```

Copy the keycodes from your terminal in here
```
keycode 160 = 
keycode 174 = 
keycode 176 = 
keycode 162 = 
keycode 144 = 
keycode 153 = 
keycode 164 = 

```

Now, on each line put one of these that corresponds to the key (technically, you can call your volume lower button mute if you want, but there's no reason to confuse yourself).  Here's a short list of things to choose from (should be sufficient for what you're wanting):
```
XF86AudioMute, XF86AudioLowerVolume, XF86AudioRaiseVolume, XF86AudioPause, XF86AudioPrev, XF86AudioNext, and my personal favorite XF86AudioStop
```

After you're done, you should have something like this:
```
keycode 160 = XF86AudioMute
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 162 = XF86AudioPause
keycode 144 = XF86AudioPrev
keycode 153 = XF86AudioNext
keycode 164 = XF86AudioStop
```

Hooray!  You're still with me.

Now, after you load this modmap (xmodmap $HOME/.Xmodmap), X will recognize your keys.  It may have already done this, but after this it will for sure.

Next up, making these keys actually do something.  I like to use xbindkeys because it is window-manager independent and I switch window managers all the freakin' time.  I don't use Ubuntu and I'm not sure if it's installed by default, so as a precaution go ahead and do this:
```
sudo apt-get install xbindkeys
```
Now, we have to create a configuration file for xbindkeys.  Fire up your gnome-run command thing.  (Alt + F2)
```
gedit ~/.xbindkeysrc
```
The general form of a rule here is this:
```
"commandtorun"
     keyToUse

```

So, now to put our multimedia keys to use:
```
"amixer -q set PCM toggle"
   XF86AudioMute
   
"amixer -q set PCM 2+ unmute"
    XF86AudioRaiseVolume

"amixer -q set PCM 2- unmute"
    XF86AudioLowerVolume

```

See how it works?  Now, you can continue to add some more bindings or save and quit.  Here's some of the rest of my bindings so you can see how it works some more:
```
"gmrun"
   Mod1 + F2

"firefox"
   Mod4 + f

"eclipse"
   Mod4 + e

"opera"
  Mod4 + o

"sonata"
   Mod4 + s

```

List of modifiers should you need it:
```

Control, Shift, Mod1 (Alt), Mod2 (NumLock),
Mod3 (CapsLock), Mod4 (Windows key), Mod5 (Scroll)
```

Anyway, you're basically done here.  All's that's left is to make xmodmap and xbindkeys start up at login.

System --> Preferences --> Sessions
Add an entry to startup that is like this (replacing /home/rickiecodie with your actual home directory):
```
xmodmap /home/rickiecodie/.Xmodmap
```
Add another entry that simply runs
```
xbindkeys
```

In practice you'd want to make sure that xmodmap is run first, but I've never had issues in gnome with it as long as I added it to the list of startup programs BEFORE I add xbindkeys.

Hopefully this helps.  If you ever get your master volume control back, it's just a simple matter of going back to your .xbindkeysrc and changing PCM back to Master.

If this isn't what you were looking for, I apologize for the boring read I made you do.

---

### Post by rickycodie on 2007-09-13
i hope this works, i'm gonna try it.  only one question, where do i put the .Xmodmap? in the home folder?

---

### Post by jordanmthomas on 2007-09-13
Yes, same for .xbindkeysrc

This should work...or at least there's no obvious reason it wouldn't work since you said PCM does work for you and I've successfully been using this method for about two years (read:  about 30 different linux installations).
If it doesn't, there's loads of info about getting your keys set up at that gentoo wiki link.

---

### Post by Sain on 2007-11-18
I have the same issue, but it worked couple days ago... I was messing with some hotkey service (turned it off), so that could be it.

---

### Post by fergus on 2008-02-09
any progress on this issue?  I just got a new thinkpad T61 and am having the same problem.  Volume buttons only work the mic but the mouse wheel will work the PCM.  

fergus

---

### Post by fergus on 2008-02-09
Just figured it out from another post.

Goto System->Preferences->Sound and select PCM under Default Mixer Tracks.  

fergus

---

