---
title: "Dapper Freezes"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by tuskal on 2006-12-03
[I][SIZE="3"]Hello!
[/SIZE][/I]
I recently decided to try out Ubuntu once again, after have tried version 5.10 a while back. But I have run into some troubles.

I belive it's a common problem, but I can't really find something similar with a solution. (therefore i'm starting a new thread :rolleyes: )

**These are my specs:**
Pentium 4 3.2ghz
1024mb ram
200gb segate hd (partitioned)
ATI Radeon 9500pro
Logitech MX510 mouse and some Logitech keyboard

So, this is what I did:

I downloaded ubuntu 6.10 and burn it on a cd (using 48x, dunno if that can cause problems). Put the cd in and reboot the computer, everything starts nice and I began answering questions and all that. And then "BAM!", mousepointer [COLOR="LightBlue"]freezes [/COLOR]and I can't do a thing. I then try a couple of more times restarting and doing it all over with no success.

I then realize that Breezy Bagder 6.10 version could be a bit buggy and I then read that Dapper Drake 6.06 could be/is a more stable version. 
I download this and burn it (48x) and then install it with no problem at all. I partitioned my hd into 4 parts; 1 with ubuntu on 1 with ubuntu swap, 1 with windows and 1 for storage.

Then I reboot again, and choose Ubuntu to start in the menu, it boots to the loginpage and I login. It starts up and everything and works like charm... For approx 9 min, and then "BAM!" it [COLOR="LightBlue"]freezes[/COLOR].(no commands work, such as CTRL+ALT+F7 and whatever) I reboot and  starts to run some updates that Ubuntu automatically offered me (such as new kernel and stuff). I then reboot myself (after going strong for 14 min), and after booting 9 min after startup it [COLOR="LightBlue"]freezes [/COLOR]once more. This time I got as far as starting gaim and installing some more (installing programs is dangerously easy in ubuntu! 8) ). 

I used automatix and easyubuntu, and I belive that easyubuntu installed some drivers for my gfx card (atleast that is what I chose). I then reboot once more, and I was very happy when I passed the 9 min mark without any [COLOR="LightBlue"]freezing[/COLOR], doing some regular sufing on the web with FF and downloading some RPS packages while trying to understand how to install them. Then after 25 min more the bastard [COLOR="LightBlue"]freezes [/COLOR]once more making me furious and then I'm back in windows.

This was yesterday, and today I had another go, I played around a little not making anything too serious since it could [COLOR="LightBlue"]freeze [/COLOR]any minute.... (which it did) :-k

I have also done a memtest which proved to be good, I checked the cd's hash-stuff which proved to be alright...

Also, the screensavers dosn't work very well either. They hang themselves forcing me to restart. Being 3D and all, maby this also has something to do with my gfx card or the drivers?
[B]
So, my question is,[/B] ***what could cause the problem?***

To me it's obviously the gfxcard or it's drivers but it might be something else and I don't know what to do about it... It could be possible that I have installed 2 diffrent drivers, one from easyubuntu and one from ati's homepage, but I am unsure if I succeeded ](*,)

Would upgrading to 6.10 solve it? I've heard that many ppl have problem but even more ppl that it works very well for..

btw, sorry for the überlong post, but now all cards are on the table atleast ;) :) 

[SIZE="4"]Please, help me with this, I REALLY want this to work...[/SIZE]

---

### Post by Shatrat on 2006-12-03
Have you tried ctrl alt backspace?  That restarts the x server.
Also you can check your log for errors by typing dmesg | grep error and maybe you'll find something useful there.

As for suspicions, I'm with you for suspecting ATI.  When in doubt, it's ATIs fault.

---

### Post by ReaderRat on 2006-12-03
Take a look at this....
[url][b]

EDIT:  %@#&*%# Problem here...

---

### Post by ReaderRat on 2006-12-03
Okay, I'll try again....take a look....
ATI - Post the way you got ATI to work.
          **[http://www.ubuntuforums.org/showthread.php?t=221320](http://www.ubuntuforums.org/showthread.php?t=221320)**

See post #2.

---

### Post by Stephen47 on 2006-12-03
this has nothing to do with the problem here but I have seen a few commands suggested that have a single vertical line in the message string. I don't have that character on my keyboard. How do I  get it?

---

### Post by Mimsy on 2006-12-03
If you have a US keyboard, it's on the key just above the Enter key, the one with the \ on it. Hold shift, press the \-key, and you get |.

If you don't have a US keyboard, it might be a bit trickier though.

/Mimsy

---

### Post by Stephen47 on 2006-12-03
Thank you

---

### Post by tuskal on 2006-12-04
Cool, thanx! I'll try that when I get home later today..

Awsome that it exsists a guide just for my gfx card! Never thought that... :)

But is it certain that it is the gfx card?

I've tried the ctrl alt backspace command but nothing happens, It's totally freezed...

---

