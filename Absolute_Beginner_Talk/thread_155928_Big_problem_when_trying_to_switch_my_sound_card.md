---
title: "Big problem when trying to switch my sound card"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by mfuqua on 2006-04-06
Hello everybody,

I have a problem that I couldn't seem to find much about (or I wasn't sure how to search for it, one or the other).

I figure I'll try and give the basics:
Software - I have installed 5.10 (intially I had downloaded from when it was 5.10 preview, though I didn't get around to installing it until a couple of weeks ago, but I have updated using apt-get to the latest)
Hardware - IBM Thinkpad R51, and an external sound card, a Sound Blaster Live! 24 bit external USB

And my problem is as follows:
I was not getting sound out from the speakers hooked up to the sound card, so I went to System->Preferences->Sound, and under the General tab, I changed my default sound card from Intel 82801DB-ICH4 (which I guess is my laptop's interal sound card) to the SB Live! 24 bit external one.

However, when I did this, the window with the sound prefences kinda froze, as did the taskbar with Applications, Places, and System.  This in turn left me unable to open things, and I was forced to shut down by turning the power off (I know, not a good thing to do).  When I restarted, everything went fine and I got to the login in screen.  But upon putting my screenname in and entering my password, things stopped working.  It acts as if it is beginning to load gnome, but the splash screen never comes up nor does gnome.  All I'm left with is a cursor, which won't let me right or left click (at least doing so does nothing), and a lightest brown screen (not my background color).

I can do the safe boot at grub and get into the root terminal, and from there I typed in startx and got me to gnome on root (again, I realize this is very unsafe and bad practice, but right now I don't have anything else to boot into) .

What I'm left wondering is two fold.  One, is there any way I can recover from this and get back my normal gnome account and all my settings as I had them without reinstalling, and two, is there some way I can get my sound card working either without having to worry about this happening again?  I know that this is a long post, but I just feel right now that I'm against a brick wall and have no idea what to do.  Up until this point I was really enjoying my linux experience and found myself very happy that I switched over from windows, but this has left a bad taste in my mouth (which I'm not holding against linux or ubuntu neccesarily, just with my own willingness to deal with these kind of problems right now when I could be using some of my time and resources in other ways).

Thank you for anyone who even reads through this and possibly tries to help.  I'm very appreciative, and hopefully I've given you a good amount of detail about what my problem is and it'll be fairly simple to fix.

---

### Post by Mustard on 2006-04-06
I've been sitting staring at this trying to wrap my head around the problem, so this is more thinking out loud than offering a solution....

I'm wondering firstly whether disabling onboard sound (using BIOS settings) would do something towards avoiding the lockup you got first time around.

Secondly I'm wondering whether you could create a new user account and use that temporarily while you fiddle around with the problem.

Thirdly, I am wondering if saw a thread just recently that was talking about issues with 24 bit soundblaster cards and what they ended up doing to resolve it.

I haven't come up with any concrete solutions as I say, as I'm just trying to think it all through atm.

---

### Post by trent dillman on 2006-04-06
First, let's get Gnome back.

Log in recovery mode, then 

```
rm -r /tmp/gconf-*
```

then

```
sudo init 2
```

---

### Post by mfuqua on 2006-04-06
[QUOTE=trent dillman]First, let's get Gnome back.

Log in recovery mode, then 

```
rm -r /tmp/gconf-*
```

then

```
sudo init 2
```[/QUOTE]


I'm assuming that the * at the end of the first code is supposed to be my username that I normally login with, and not root.  If that is the case, then I don't seem to have one, and the closest thing I have in the /tmp directory is 'gconfd-root'.  If it is this you want me to remove, then I will, but before I did something like that (since I know I shouldn't normally be messing around in root) I wanted to make sure.

I'm going to head to bed tonight, but I'll check back tomorrow and see where I am.

Thanks for the help so far.

---

### Post by trent dillman on 2006-04-06
Well...if you don't have one for your username, don't bother.

Check your home dir for .Xauthority and .ICEauthority and their permissions:

```
ls -l ~/.*authority
```

Mine show up as:

```
jeff@ubuntu:~$ ls -l .*authority
-rw------- 1 jeff jeff 10943 2006-04-06 01:20 .ICEauthority
-rw------- 1 jeff jeff   117 2006-04-06 01:20 .Xauthority
```

---

### Post by dvarsam on 2006-04-06
I believe that you started ALL this the wrong way...

When I had a similar problem, I thought I had to install drivers...

The first thing you have to check on an Ubuntu PC is IF the Sound coming from your machine is "MUTED" or NOT...

To do this, launch a Terminal window & type"

> alsamixer

See if there is a "Front Speaker" in there & if there is an "MM" under it...
Move around with the "arrow" left&right keys of your keyboard & up&down "arrow" keys to increase/decrease sound level...

Seeing an "MM" means that it is "Muted" out - NO Sound man....

Unmute it by pressing the "M" key on your keyboard to turn "MM" to "OO".

That means, that your "Front Speaker" sound is "unmuted"...

Make sure, volume is up, on that "Front Speaker" - increase it if needed by using the keyboard's "arrow" up&down keys...

Exit the "alsamixer" window by pressing the "ESC" key TWICE!!!

Test your sound, by typing the following on a Terminal window:

> ls /dev > /dev/dsp

Alternatively, you could also type:

> aplay /usr/share/sounds/phone.wav

If you hear NO sound, check whether you plugged the speaker wire in the right hole....

OR: try to put an CD-ROM playing music with your "Applications\Sound & Video\Soundjuicer" player...

Then check whether you plugged the speaker wire in the right hole....

If NOTHING works, then try to see how to install drivers man....

This is the correct approach....

Have Fun!!!

P.S.> Now with ALL the settings you have been playing around with, you have probably destroyed an already "setup" audio system... you might have to re-install....
I hope NOT, if you are lucky...

---

### Post by mfuqua on 2006-04-10
Ok, sorry to have taken so long to get back to this, but I've been busy and was in need of my computer for the windows partition and didn't have a chance to get back to playing around on the ubuntu side.

So I ended up breaking down and reinstalling ubuntu, and spent the time to clean up everything and make it feel comfortable to me again.

I'm afraid to do System->Preferences->Sound and change the default sound card again because I don't want to have to reinstall once again.  I tried doing as dvarsam said, but when I checked, it defaults to my intel chip, which does work and I can get sound out of.  However, I still can't figure out how to get the USB sound card to work.

Again, I appreciate any help that you guys and gals can lend me, for I am liking how comfortable and easy linux is to get settled with, except for this issue with my sound card :-).

---

