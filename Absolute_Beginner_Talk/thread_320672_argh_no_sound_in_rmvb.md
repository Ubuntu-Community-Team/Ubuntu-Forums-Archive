---
title: "argh no sound in rmvb"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by synt4xerr0r on 2006-12-17
no sound comes from rmvbs they play just no sound i have tried playing with all different player none give sound to rmvb all sound works on my pc except rmvb files and i have the codecs for them what is the problem?

---

### Post by synt4xerr0r on 2006-12-17
any help would be appreciated very much

---

### Post by synt4xerr0r on 2006-12-17
its been a while...................................... so sorry for the triple post

BuMp~

---

### Post by synt4xerr0r on 2006-12-17
i have been searching google and everywhere i have dled every codec i can find stil lno fix

---

### Post by synt4xerr0r on 2006-12-18
,.,

---

### Post by synt4xerr0r on 2006-12-19
guess no one knows

---

### Post by synt4xerr0r on 2006-12-22
its been a week so.... bump

---

### Post by z987k on 2007-05-19
I'm having the exact same problem in fiesty.  Need to get sound to work, or if I can just convert it, but something tells me if I convert it to avi and the codec doest play sound the avi file will end up with no sound. 
 Oh and people need to stop using these shitty *** codecs.

---

### Post by Egils on 2007-05-23
You can try the following workaround, which has been posted in other threads as well:

>  Originally Posted by NeoChaosX  View Post
I'm having this problem, too. It started happening in Feisty; in Edgy, Real files played audio just fine in Kaffeine as well. It was exactly like one problem I had a year ago when I couldn't get WMVs to play sound despite having w32codecs installed; it turns out I had to tweak ~/.xine/catalog.cache to get it to play sound. Maybe playing with that file again will get it working, but I'm not so sure.

chggr: I'd prefer not to use VLC for a number of reasons, one of which there are some format it actually doesn't support (I have a few videos encoded in Indeo v4, which it doesn't support). So fixing xine to get this working would be preferable.

ETA: Found a solution. Open up ~/.xine/catalog.cache in a text editor and find this section:
Code:

[/usr/lib/xine/plugins/1.1.4/xineplug_decode_real_audio.so]
size=11300
mtime=1171041406
type=131
api=15
id=realadec
version=10104
supported_types=52494336 52559872 52756480 
decoder_priority=5

Bump up the 'decoder_priority' value to 10. That should get audio with Real files working.

First scratchy sound in SDL games, now this. And Canonical smoothed out all my audio problems with Edgy...
Reply With Quote

Or alternatively you can install mplayer and the w32codecs package (which it sounds like you already have).

---

### Post by Freiburg05 on 2007-05-24
I found yesterday that I have this problem (which I hadn't in Edgy), but the solution above have worked very well for me. Thanks!

---

### Post by Griff on 2007-05-29
That totally worked for me Egils.  Thanks for the post.  I did a search and this was the first thread that popped up and your solution worked perfectly for me.  The only issue, which really isn't an issue, it that once a vid comes up it takes a couple seconds for the sound to come on.  The sound's in sync so like I said it really doesn't matter.

-Griff

:popcorn:

---

### Post by Egils on 2007-05-29
We should thank NeoChaosX, the source of the solution - I'm just handballing information ;).

In case there are any AMD64 Fiesty users reading these threads, I'm happy to report that it is now possible to play back rmvb files with 64-bit mplayer. Previously you had to go through the slightly awkward process of installing 32-bit mplayer but this is now no longer necessary, I found the rmvb files to play after installing mplayer and multimedia codecs from automatix (possibly with the assistance of the medibuntu repository).

---

