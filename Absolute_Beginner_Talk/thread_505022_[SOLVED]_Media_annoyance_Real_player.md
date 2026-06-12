---
title: "[SOLVED] Media annoyance: Real player"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by Paulmd on 2007-07-19
What a headache: installed realplayer 10: kinda, sorta. It works if i open up the directory and run it.  But It neither integrated itself into the startup menu, nor can I to make it integrate into Firefox. Any ideas as to what I did wrong? Or better, how to fix it. At linux, I'm a novice. 


I would like to be able to get Real Audio from 

[http://www.npr.org/programs/waitwait/](http://www.npr.org/programs/waitwait/)

The podcast version works, but it's updated a day or two late.

If you click in the "this weeks show" link, and then click on the link that says "listen to the whole show", I get a popup that SHOULD play the media. Only it doesn't.

Clicking the "launch standalone player" link, doesn't. But it will download a WAX file, which I can't play with anything. I've tried totem, Mplayer, VLC, and XMMS, and even tried it in realplayer.  VLC got as far as playing part of the ad then chocking. 

The site has some nearly undecipherable JavaScript code that is supposed to detect what media player you've got, and if none, reverts to windows media player. Which of course linux doesn't have... 

The code is so convoluted that I can't even point realplayer at a direct link to the right file, it uses 10 digit random numbers to defeat that (AARGH). 

Feisty Fawn
Firefox 2.0.0.4

I think i could solve this problem IF i could get realplayer to be properly installed and recognized as a proper mozilla plugin.

Also, if anyone could point me to a way to get these WAX files to actually work, that would be great.

---

### Post by wolfen69 on 2007-07-19
i got it! (i went to the site) go to synaptic, download "gstreamer codecs-bad", download vlc player. when you click an audio link, the little window opens up. click standalone player. save the(.wax) file to your desktop. right click and open with vlc.(be patient for a few seconds) it worked for me.

---

### Post by p_quarles on 2007-07-19
> **wolfen69 said:**
> i got it! (i went to the site) go to synaptic, download "gstreamer codecs-bad", download vlc player. when you click an audio link, the little window opens up. click standalone player. save the(.wax) file to your desktop. right click and open with vlc.(be patient for a few seconds) it worked for me.
Well, that didn't work for me. Apt found no package by that name, and I already had gstreamer-plugins-bad installed.

Here's what did work for me, though: [http://www.debianhelp.co.uk/realplayer.htm](http://www.debianhelp.co.uk/realplayer.htm)

If you don't know how to use vi/vim, you can edit the source list this way: ```
gksudo gedit /etc/apt/sources.list
```
Add the line specified in the tutorial, and then use apt or Synaptic to get the correct Realplayer package. 

Also: I had to open Realplayer from the menu, and then accept the license, before it would work.

---

### Post by wolfen69 on 2007-07-19
i tried several web pages that use realplayer and nothing worked using your method. why is it so hard to get streaming stuff to work in linux?

---

### Post by Paulmd on 2007-07-19
<quote> 
I got it! (i went to the site) go to synaptic, download "gstreamer codecs-bad", download vlc player. when you click an audio link, the little window opens up. click standalone player. save the(.wax) file to your desktop. right click and open with vlc.(be patient for a few seconds) it worked for me.
__________________

</quote>

Not seeing gstreamer codecs-bad.

However, i have installed (previously)

gstreamer0.10-plugins-bad (0.10.4-1ubuntu1) the latest. (is this what you meant?)
I also have the good and ugly set
VLC media player 0.8.6 (not a,b, or c) (those are security updates, not functionality)

I don't have the bad-multiverse set. Should I install those too?


Anyway, I did try again just to be sure.

It got as far as 'cds for Car Talk and other npr programs are available at...." then it looped once. 
And then nothing. It didn't move to the next segment. Did you get it to play the next segment? There's nothing wrong with the files themselves, I know they work just fine under win2k and XP.


This has been bugging me for days...

Thanks for the help.

---

### Post by wolfen69 on 2007-07-19
if you can figure out streaming content in linux,  your a better person than me. ive given up. (dont worry, not going back to windows) ive just learned to live with it.

---

### Post by Paulmd on 2007-07-19
> **p_quarles said:**
> Well, that didn't work for me. Apt found no package by that name, and I already had gstreamer-plugins-bad installed.

Here's what did work for me, though: [http://www.debianhelp.co.uk/realplayer.htm](http://www.debianhelp.co.uk/realplayer.htm)

If you don't know how to use vi/vim, you can edit the source list this way: ```
gksudo gedit /etc/apt/sources.list
```
Add the line specified in the tutorial, and then use apt or Synaptic to get the correct Realplayer package. 

Also: I had to open Realplayer from the menu, and then accept the license, before it would work.

Mixed results: I did, after some finagling get realplayer to install using the software sources menu instead of editing the sources file manually. Then it needed to UPDATE the sources, and THEN realplayer was available thru the package manager.

So Realplayer at least now shows up in the menu, but still no firefox plugin.

Still working on it...

---

### Post by cookies on 2007-07-19
Realplayer can be a REAL HORRID to get the plugin to work, trust me. And even if you DO get it set up, it is NO guarantee it will work.

Anyway, you must edit your /home/USERNAME/.bashrc file to where realplayer is like this
export PATH=/path/to/where/real/is/bin:$PATH

so like

export PATH=/usr/bin:$PATH

For the plugin download realplayer from the site:
Set it to install to some temp folder on your desktop

Copy these files into your /home/USERNAME/.mozilla/plugins folder from the mozilla folder in the realplayer directory.
nphelix.so
nphelix.xpt

And put nphelix.xpt in /home/USERNAME/.mozilla

Okay, annoying, yes, will not always work. 

I'd say use MPlayer instead. :|

---

### Post by Paulmd on 2007-07-20
> **cookies said:**
> Realplayer can be a REAL HORRID to get the plugin to work, trust me. And even if you DO get it set up, it is NO guarantee it will work.

Anyway, you must edit your /home/USERNAME/.bashrc file to where realplayer is like this
export PATH=/path/to/where/real/is/bin:$PATH

so like

export PATH=/usr/bin:$PATH

For the plugin download realplayer from the site:
Set it to install to some temp folder on your desktop

Copy these files into your /home/USERNAME/.mozilla/plugins folder from the mozilla folder in the realplayer directory.
nphelix.so
nphelix.xpt

And put nphelix.xpt in /home/USERNAME/.mozilla

Okay, annoying, yes, will not always work. 

I'd say use MPlayer instead. :|


Yeah!!!!! I got it working! Thank you! Thank you All. 

The 28th time is the charm.

My website traffic must look real odd to the folks at npr. :)

Everybody has been great.

---

### Post by st0nes on 2007-07-20
The latest episode of the program was corrupt (at least the podcast version).  That was the day before yesterday, it might be fixed now.  Perhaps that is part of your problem.

---

### Post by Paulmd on 2007-07-20
> **st0nes said:**
> The latest episode of the program was corrupt (at least the podcast version).  That was the day before yesterday, it might be fixed now.  Perhaps that is part of your problem.

I've not been having trouble with the podcast stuff. It's the RealPlayer stuff that was the headache. Anyway, I just got it fixed. Thanks to Cookie, and others.

---

### Post by fremmus on 2007-07-20
this worked for me

[http://archive.canonical.com/ubuntu/pool/main/r/realplay/](http://archive.canonical.com/ubuntu/pool/main/r/realplay/)


damn, all realplayer topics should be put together... its impossible to read all of them and find solution lol, i went thru all and nothing, hope this helps
google helped

---

