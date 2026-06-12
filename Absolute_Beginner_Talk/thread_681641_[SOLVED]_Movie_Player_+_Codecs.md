---
title: "[SOLVED] Movie Player + Codecs"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by lemon_duck on 2008-01-29
I'm still trying to get this working.

I found a package of codecs and the read me file enclosed suggested the folder to copy them into so that they could be read by Mplayer. I did that and they are not being seen, and I'm still being referred to the Gstreamer codecs??????

I tried installing VLC and thought that I had done so but now cannot find it?????

---

### Post by Nano Geek on 2008-01-29
All you need to do to install nearly any codec you need is to run this.```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by billgoldberg on 2008-01-29
If you installed vlc using synaptic or add/remove or apt-get it should be under:

"applications -> sound & video".

Try pressing "alt + f2" and enter "vlc" (without " ") 

If that works but it somehow didn't get into the menu, you can add it manually by right-clicking the panel above the "applications" menu and choose "edit menu", then add a new entry under sound & video. The command should bd "vlc" (without vlc).

---

### Post by aphirst on 2008-01-29
You need to make sure you have all the repositories enabled that you need. Make sure multiverse, universe, free and non-free are checked in synaptic repositories, and follow the guide at medibuntu.org to add their repositoryin order to download other restricted codecs.

There are countless guides on the internet. Just google it. There's an ubuntu wiki (i think it's something like ubuntuguide.org) that details everything you'll need to know, and step-by-step instructions on how to do it.

Like I say, this sort of thing has been posted by newbies galore literally thousands of times, so there will be respectively thousands of hits for answers on google. Just do a bit of research.

P.S. The VLC in the ubuntu repositories I don't think supports all codecs (it might not even be in the default repos any more), so get the one from the medibuntu repos. WHichever way, it'll be accessible through Applications > Sound and Video > VLC Media Player, or typing "vlc" into a terminal or an Alt-F2 dialog.

Good luck.

~ aphirst ~

---

### Post by AndyCooll on 2008-01-29
> **asjdfwejqrfjcvm msz34rq33 said:**
> All you need to do to install nearly any codec you need is to run this.```
sudo apt-get install ubuntu-restricted-extras
```

As this post says. For movies (DVD's) you may also need libdvdcss2. To get these codecs you'll need to add the Medibuntu repository. There's  full multimedia howto [here]("http://ubuntuforums.org/showthread.php?t=661833").

:cool:

---

### Post by AlanR8 on 2008-01-29
Must confess that I use Automatix ([www.getautomatix.com](www.getautomatix.com)) to install all the multimedia issues on my machine.

Quick, simple, works every time and to date has never broken anything

---

### Post by billgoldberg on 2008-01-29
Don't use automatix.

---

### Post by CJ56 on 2008-01-29
Just to agree with the above posts:

- Get the restricted extras package from Synaptic; make sure universe and multiverse repositories are enabled and reloaded before you do so

- Add medibuntu to the repositories, search for libdvdcss and then install it

- Once you've done all that (it takes a few minutes) get VLC off Synaptic. I find that it plays movie files of all flavours and DVDs pretty well

Hope this works for you...

---

### Post by philinux on 2008-01-29
To add medibuntu click the link below and follow the procedure.

---

### Post by AlanR8 on 2008-01-29
> Don't use automatix

Why?

> 
A reasoned argument is always better than an unexplained statement

---

### Post by Nano Geek on 2008-01-29
> **AndyCooll said:**
> As this post says. For movies (DVD's) you may also need libdvdcss2. To get these codecs you'll need to add the Medibuntu repository. There's  full multimedia howto [here]("http://ubuntuforums.org/showthread.php?t=661833").

:cool:I don't think that's necessary. I've been able to get full DVD support by using this guide from the wiki.
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

> **AlanR8 said:**
> Why?From what I've heard, Automatix has been known to cause problems on some computers, so it's best that you don't use it for now.

---

### Post by AndyCooll on 2008-01-29
> **asjdfwejqrfjcvm msz34rq33 said:**
> I don't think that's necessary. I've been able to get full DVD support by using this guide from the wiki.
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

In giving the OP the link, I was giving them the option to decide what steps they wished to take (though perhaps I should have made that clearer in my response). I took this step since the OP doesn't actually clarify exactly what they want the codecs for, even if they do mention movie player.

:cool:

---

### Post by aphirst on 2008-01-30
In fairness, Automatix hasn't caused any day-to day problems on my parent's machine (and they suck big time :P); and I only got it to hiccup once. BUT, I was actually TRYING to make it fail (shiting about with sudo sessions and repository lists etc etc etc).

There are reports of dependency errors, but the general concencus is that it's rather good.

asjdf* : How on earth did you get full DVD support without libdvdcss2? I mean, were you only watching unprotected DVDs, or does your DVD hardware have a build in decryption system? It doesn't always work for me with libdvdcss2 (that is, without hacking about :P).

---

