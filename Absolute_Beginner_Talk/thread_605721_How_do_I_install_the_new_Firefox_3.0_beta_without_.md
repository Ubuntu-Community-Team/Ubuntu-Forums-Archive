---
title: "How do I install the new Firefox 3.0 beta without losing my stable version of firefox"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by slymi2005 on 2007-11-07
I was wondering how I would go about installing the Firefox 3.0 beta 1 while still keeping my stable 2.00x? I don't want to lose anything that I have on the stable version, I just want to try out the beta. I downloaded the tar.bz2 from here < [http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/2007-11-06-18-firefox3.0b1/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/2007-11-06-18-firefox3.0b1/) > but I don't know what to next. Any thoughts?

---

### Post by taurus on 2007-11-07
Download it and unpack it somewhere in your $HOME directory, something like ~/bin.  Then, run it from there.

---

### Post by philinux on 2007-11-07
Put the deb file or whatever in /opt thats what this directory is for. You'll find /opt is empty.

---

### Post by carlosjuero on 2007-11-07
I installed it through Synaptic Package Manager, it kept Firefox 2 intact and installed 3 on its own. Have  you tried doing it that way?

---

### Post by janfsd on 2007-11-07
> **carlosjuero said:**
> I installed it through Synaptic Package Manager, it kept Firefox 2 intact and installed 3 on its own. Have  you tried doing it that way?
The one on the repos is outdatedt (alpha 8). They just released beta 1 today.

---

### Post by carlosjuero on 2007-11-07
> **janfsd said:**
> The one on the repos is outdatedt (alpha 8). They just released beta 1 today.
Ahhhh. Didn't know that - I would hope that it would do the same thing (keeping 2 versions) but if it is a DL package/build then I don't know.

---

### Post by Rippie on 2007-11-20
Hello guys..

I found a way here:

[http://phorolinux.com/installing-firefox-30-beta-1-on-ubuntu-710-gutsy-gibbon.html#more-72](http://phorolinux.com/installing-firefox-30-beta-1-on-ubuntu-710-gutsy-gibbon.html#more-72)

---

### Post by Koybe on 2007-11-20
> **Rippie said:**
> Hello guys..

I found a way here:

[http://phorolinux.com/installing-firefox-30-beta-1-on-ubuntu-710-gutsy-gibbon.html#more-72](http://phorolinux.com/installing-firefox-30-beta-1-on-ubuntu-710-gutsy-gibbon.html#more-72)

That's exactly what i've done for a try.... but it just shows up version 2 again :o

---

### Post by philinux on 2007-11-20
The system seems to hijack the launcher and launches version2 .

---

### Post by Rippie on 2007-11-21
Just tried it, and it seems and me also get Firefox 2 up..

Any idea anyone ?

---

### Post by Protagonistics on 2007-11-23
I too followed those steps referred to in the outlink before. Naturally, it didn't help.

Also, I tried copying and pasting my .mozilla folder to my desktop for safe keeping in preparation for downloading/installing FFox3 alpha from Synaptic-- but when I tried to do that NO FILES landed on my desktop. I opened the Desktop as a folder to just check- but no .Mozilla folder was present. HOWEVER, when I tried to copy/paste again, I got a message stating that .Mozilla already existed on the Desktop. Thinking I was crazy, I opened Terminal and cd'ed to Desktop and typed "ls". No .Mozilla. What in the world is going on?
I tried to move the whole folder there out of desperation: message stating "skip or replace" appeared, hit replace, no .Mozilla. I Pasted the folder back into my /home/NAME directory and thankfully it reappared- but now I lost all my plugins. What in the world??

ANY help on any issue is appreciated.

---

### Post by Sunflower1970 on 2007-11-23
Make sure you close all instances of FF2. If after closing everything FF 2 still opens up, check under System-->Administration-->System Monitor to see if FF is still running. Kill them if there is, then start up FF 3 Beta. 

I've been using FF 3 alpha & beta for months along with FF 2 and never had a problem with one or the other opening up.

---

### Post by enchance on 2007-11-23
I got it to work! What I did was after extracting the file,since I already had a firefox folder in /opt, the first thing I did was to rename the extracted folder into something else like **FF3beta1**. You can rename it anything you want, of course.

Then I moved the folder to /opt like so
```
$ sudo mv -vf ~/Desktop/FF3beta1/ /opt
```

Then I applied the ff
```
$ sudo chown -R root:root /opt/FF3beta1/
$ sudo chmod -R 755 /opt/FF3beta1/
```

Finally I closed my existing Firefox2 window, waited a few seconds, then I did a test by manually going to the FF3beta1 folder in /opt using nautilus and clicking on **firefox**. It worked and boy is it fast!

Now all that's left to do is create a launcher and that's it. I haven't tried running it alongside Firefox2 though but why would anyone want to do that? :KS

---

### Post by philinux on 2007-11-23
Whats causing the speed increase. And how significant is it.

---

### Post by enchance on 2007-11-23
Apparently, FF3 is set to use the latest version of Gecko. I don't know what Gecko is but right now it's the best thing since sliced bread. :)

---

### Post by rungss on 2007-11-24
I tried the instructions provide by enhance and the one provided by Rippie both of them worked but I loose all my cookies, history etc which I prefer to keep. I don't want to having to login in all the sites which I use .

fortunately I had kept a backup of my home/rungss/.mozilla folder prior to starting FF3 so I reverted back and now using FF2 again.

Previously I had installed FF3 alpha and I have no Problem using it I can run both FF2 and FF3 alpha at the same time. FF3 alpha stores all the user specific information in ~/.mozilla/firefox-3.0 so no conflict issue there.

---

### Post by enchance on 2007-11-24
> **rungss said:**
> I tried the instructions provide by enhance and the one provided by Rippie both of them worked but I loose all my cookies, history etc which I prefer to keep. I don't want to having to login in all the sites which I use.

That's odd. I still have all my cookies intact.

---

