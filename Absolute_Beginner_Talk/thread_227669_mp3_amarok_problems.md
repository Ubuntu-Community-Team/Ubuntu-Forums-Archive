---
title: "mp3 amarok problems"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by BananaCakes471 on 2006-08-02
i can't play mp3's through amarok so i got automatix and i installed the codecs and everything....but the mp3's still don't work in amarok...do i have to somehow plug them into amarok? i'm lost..

---

### Post by fourchannel on 2006-08-02
most likely, your problem is you don't have an engine to decode the files for you. Go into synaptic and search for "amarok"  find a package called "amarok-gstreamer" and "amarok-xine" and install them both.

open up amarok and go to "Settings" > "configure amarok" and on the left go to "Engines"

select either gstreamer or xine (I personally like gstreamer, but xine works fine) and below that for the output select either "alsasink" or "esdsink" and restart amarok and see if that doesn't fix your problem.

---

### Post by BananaCakes471 on 2006-08-02
where do i find output..when i click engine there is only the choice of the engine and an "about" button

---

### Post by fourchannel on 2006-08-02
hrm.. it should be there. This is what my setup looks like.

EDIT:

Oh, did you restart amarok after you installed gstreamer? It won't show up unless you do.

---

### Post by fair06 on 2006-08-02
thanks.... this and some other posts helped me get my MP3 support in kubuntu... thanks a billion!

---

### Post by Roasted on 2006-08-02
> **fourchannel said:**
> most likely, your problem is you don't have an engine to decode the files for you. Go into synaptic and search for "amarok"  find a package called "amarok-gstreamer" and "amarok-xine" and install them both.

open up amarok and go to "Settings" > "configure amarok" and on the left go to "Engines"

select either gstreamer or xine (I personally like gstreamer, but xine works fine) and below that for the output select either "alsasink" or "esdsink" and restart amarok and see if that doesn't fix your problem.

Not to jack the thread, but I'm having the same issues. I got Amarok to work again following your instructions, but I'm confused. When I went into sy naptic I did not see amarok-gstreamer. Only amarok-xine. I went to configure amarok and choose the engine, and only xine was there. I'm running xine now. What is preventing gstreamer from showing up?

---

### Post by fourchannel on 2006-08-07
I'm not sure, it could be a repository issue. Do you have universe enabled?

---

### Post by Roasted on 2006-08-09
How would I tell? I still don't fully understand repositories...

---

### Post by davebgimp on 2006-08-09
> **Roasted said:**
> How would I tell? I still don't fully understand repositories...

[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

Here's a source list generator you might find handy.
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by Sweet Spot on 2006-08-09
Out of curiosity, I checked to see which engine I was using, and there's only one, which is Xine. I wanted to check out your recommendation of gstreamer, but when entering my repository list, it doesn't even show up when I search for it. I do get amarok-engines though, but attempting to request an install, makes it say (in red) Break Install. So of course I didn't install it. 

Also, my output is set to auto detect, but does have options, which I probably wouldn't need to set anyway. Does getting the amarok-gstreamer option available on the repository's depend on which versions I'm using ? I've allowed Automatix to use its repository litsings, rather than the default ones. But doesn't Automatix take advantage of all possible categories ? Bit confusing.

---

### Post by McSnickered on 2006-08-09
1. You need to add the Multiverse repository to /etc/apt/sources.list. Add the line deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) dapper multiverse. Apparently you modify the nl part to the country you’re in, so mine was "us".
   2. sudo apt-get update
   3. sudo apt-get install libxine-extracodecs (This will install your mp3 support).
   4. Shut down Amarok, then run AmaroK. You might need to restart the sound server with killall artsd, or reboot, but I found the mp3 support took effect straight away.

---

### Post by Sweet Spot on 2006-08-10
Thanks McSnickered, I tried adding that line, and replaced nl with us, as I"m in the US as well. But after that, I got this message after trying to restart adept: 

> "The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem."


I've tried a few sudo apt get commands to no avail, and now I"m stuck. Seems I keep digging my hole deeper, and deeeeeper. :-( This is not my only problem with Kubuntu at the moment, so I may wind up doing a clean re-install after all this, and going back to standard Ubuntu, though it would be really good to learn as much as possible this time around, so I don't run into the same problems next time. 

I actually wound up uninstalling Amarok before the adept move, and reinstalled it, but my entire database was still there, and it didn't install the way it did the first time, so I guess a bunch of config files were left over. I wanted it totally out of the system, and didn't know where to look for left over stuff. Amarok then acted strangly when it ran, as it kept on displaying a screen on the left asking to build its database, even after I did so several times, and restarted it. 

Oh the joys of frustration. :-({|=

Doug

---

### Post by Sweet Spot on 2006-08-10
Bump. I'm not able to fix this problem ^^^

---

