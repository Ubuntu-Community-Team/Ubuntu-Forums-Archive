---
title: "[SOLVED] I munged Gnome - Can I reload it off a CD?"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by jrlii on 2007-10-08
I screwed up.

I was working on trying to get JACKD to be able to see my Layla audio card (following instructions in [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) ) and forgot to rebuild Gnome before re-booting.

So Gnome is munged.

I tried to run "sudo apt-get install gdm ubuntu-desktop" (which I should have done before rebooting) from the command line, and it failed due to a problem with one of the sound packages (sorry I didn't get a screen shot of the exact text.) Should I try it with Aptitude instead?

I'm on dial up, so while I can get wvdial to dial up the ISP and connect (that was a bit of an adventure in and of itself)  I can't seem to do anything with it.

Is there a way to get the packages to load off the CD? It looks like there has to be a way to point apt-get to the CD, but I haven't found it yet.

Please help me get out of the purgatory of this single thread text interface! 

Thanks in Advance!

(PS- I'm writing from work.)

---

### Post by Dr Small on 2007-10-08
[quote=jrlii]Please help me get out of the purgatory of this single thread text interface![/quote]

Being stuck in CLI is quite fun, but just as you say... Since you still have Xorg, you should be able to get some lightweight window manager such as fluxbox to aid you into getting back gnome (it would really benefit to have some GUI if you have no idea what you are doing).

Fluxbox ought to be small, so try:
```
sudo apt-get install fluxbox
```
Then initiate X on Virtual Terminal 12 at Display #1:
```
xinit -- :1 vt12
```
Then start fluxbox:
```
fluxbox
```

Now you should have some GUI, rest your eyes, and then we can find some way to get Gnome back.

Dr Small

---

### Post by jrlii on 2007-10-08
Thanks for the suggestion.

Will the apt-get for fluxbox work without a live internet connection?

could I use the "xinit --:1 vt12" - maybe with a different vt number - to run wvdial to connect to the internet?

Thanks again.

---

### Post by jrlii on 2007-10-10
Well, I have yet to figure out how to reload Gnome off of the CD, but I did get my computer fixed.

I found that the key combination control-Z would force wvdial into the background, after which I could download and reinstall problematic packages. "fg" brings it back, and control-C would terminate it.

It went something like:

sudo wvdial
. . .

[Control-Z]

sudo aptitude install ubuntu-sound
. . .

sudo aptitude install ubuntu-desktop
. . .

fg
[Control-C]
exit

reboot

---

