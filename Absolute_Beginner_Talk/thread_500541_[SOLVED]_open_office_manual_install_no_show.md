---
title: "[SOLVED] open office manual install no show"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2007-07-14
Hi. After problems with OO following latest upgrade, I decided to try downloading from their site.
Got everything in and installed as per their instructions (I think). Synaptic shows their (open office's) latest version ie 2.2.1 ,   but I can't find it in 'Applications' and running > oowriter in terminal gets me this;:(
> ozymandias@ramses:~$ oowriter
The program 'oowriter' is currently not installed.  You can install it by typing:
sudo apt-get install openoffice.org-writer
so I followed the suggestion - > sudo apt-get install openoffice.org-writer
which gives me the result
> openoffice.org-writer is already the newest version.:confused:
of course.
So.....the question....what haven't I done? I tried rebooting to kick-start the menus,     but no change.
There was a whole range of setup files that go installed but there weren't any errors except for a file called 'jre-6-linux-i586.rpm' which had some trouble running a script;
> ozymandias@ramses:~/Computer/Applications/openoffice/OOF680_m18_native_packed-1_en-US.9161/RPMS$ sudo alien -i --scripts jre-6-linux-i586.rpm[: 912: ==: unexpected operator
[: 912: ==: unexpected operator:(

I tried this because I use OO everyday and I don't like not having it going.
[COLOR="Blue"]My next step will be reinstall, which I'm getting quite good at, but it'd be nice to be able to fix this.[/COLOR]
Thanks
Carlos.

---

### Post by forestpixie on 2007-07-14
When I did the same thing there was a directory within the RPMs directory (I think) which had desktop-integration - directory. In there was another RPM to convert to deb - ran that and everything was hunky dory.

---

### Post by carloslosgrande on 2007-07-14
Hi forestpixie,
Thanks ..... that was it exactly!:guitar:
So I got it all installed.........and now I'm back to square 1 as its doing the same as before I went thru all this.:(
I think I'll try getting rid of the extra language setup and see if that makes any difference.

---

### Post by mmartiste on 2007-07-14
I am having the same problem, but as the *absolute beginner* I do not understand the solution given by forestpixie.  Could someone please restate it in even simpler terms?

---

### Post by forestpixie on 2007-07-14
mmartiste -  are you saying that you've installed the open office package from the open office website and have lost the open office menu?

carlolosgrande - not really sure what problem you've got?

---

### Post by carloslosgrande on 2007-07-14
[FONT="Comic Sans MS"][COLOR="DarkRed"]Hi forestpixie.
I've thinking over what previously happened with this problem and I'm of the opinion that its related to my video card setup. A few days before this trouble, I had (once again) tried to setup some desktop effects, then along came the update and pow! dead as.

I've got an ATI Radeon X600 and I've 'trouble' with effects, for instance Edgy wouldn't run on my machine at all.

Anyway, upshot is that I've reinstalled again and given myself a good hard slap.

Thanks for your help.:guitar:[/COLOR][/FONT]

---

### Post by Hagar Delest on 2007-07-16
Here is a simple tutorial for manual installation : [[Ubuntu] Installing OOo on Debian and Co.](http://www.8daysaweek.co.uk/forums/viewtopic.php?t=759)

---

### Post by forestpixie on 2007-07-16
that's useful I shall bookmark for next time - bound to have forgotten where the little scrap of paper I've got's gone - or the kids will have decided it's the only bit  of paper left in the house

:roll:

---

### Post by carloslosgrande on 2007-09-16
[FONT="Comic Sans MS"]Ok, I did a definitive test.

Its the 'restricted drivers' option that kills 'openoffice'. I enabled it, restarted and zap, no OO. Disabled, restarted and ....er...unzap, OO works fine.

It seems my ATI Radeon X600 is rather unfriendly.[/FONT]

---

