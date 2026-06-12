---
title: "Media player problem: can't play &quot;experience ubuntu&quot; ogg"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by wobbly_bob on 2007-09-07
Hi :)

 Just installed Ubuntu Linux, and enjoying it so far, but have a problem. I have searched on the forum and around the help sections on the Ubuntu support pages, but am totally stuck.

My problem is that I can't play the sample ogg file "experience ubuntu" that comes with the feisty install. I tried installing the packages that were suggested in one of the stuck postings up above, but it makes no difference.

I get sound, but no video. If I stretch the player out it distorts. Once I managed to get the video, but with portions of it blocked out.

I'm at a loss as to how to fix this, any help greatly appreicated, thanks in advance! Nice to be here, nice to be linux :-D

---

### Post by bone2006 on 2007-09-07
should work out of the box, but consider download VLC player.  Use the package manager and download it, it doesn't reply on local codecs to play and you shouldn't have a problem playing anything with it.  If you have problems playing it with VLC, it's something you've done with your settings and not the player or codec

---

### Post by deadgobby on 2007-09-07
How much ram or memory do you have. What is your CPU. To little ram and a older CPU can = bad video play. Try this link and see if you get the same results.
Dl the ogg file and see if does happen. 
[http://screencasts.ubuntu.com/MoS2007/06_Tour_of_the_Ubuntu_Desktop](http://screencasts.ubuntu.com/MoS2007/06_Tour_of_the_Ubuntu_Desktop)

Gobby

---

### Post by wobbly_bob on 2007-09-07
> **deadgobby said:**
> How much ram or memory do you have. What is your CPU. To little ram and a older CPU can = bad video play. Try this link and see if you get the same results.
Dl the ogg file and see if does happen. 
[http://screencasts.ubuntu.com/MoS2007/06_Tour_of_the_Ubuntu_Desktop](http://screencasts.ubuntu.com/MoS2007/06_Tour_of_the_Ubuntu_Desktop)

Hi, thanks for your help, appreicated :)

I have 1/2 a gig of ram and  an Intel Celeron 2.7GHz processor, that should be enough?

I tried the link, and it plays fine. I tried another little test by going to YouTube to see if their videos would play, and they play fine.

I'm thinking it might be something to do with the graphics card? I have an Emachine and it's using an intergrated graphics card.

Any suggestions?

Thank you!


> **bone2006 said:**
> should work out of the box, but consider download VLC player.  Use the package manager and download it, it doesn't reply on local codecs to play and you shouldn't have a problem playing anything with it.  If you have problems playing it with VLC, it's something you've done with your settings and not the player or codec


Hi, thanks for the help :)

Yeah, obviously the sample video is supposed to work out of the box... thats why it's kinda a worry when it doesn't lol

I haven't changed any settings apart from changing the resolution and font size. 

I downloaded the VLC player  ( just the player with no plug-ins extras ) as you suggested and it's solved the problem partly. I can now play the video ( yay! ) but when I resize the window by dragging or I click to full screen I have the same problem was before: a black screen with audio playing.

What do you suggest? Thanks in advance.

---

### Post by RomeReactor on 2007-09-07
Hi. If you have desktop effects running, try disabling them and see if that makes a difference; is your integrated video card Intel?

---

### Post by wobbly_bob on 2007-09-07
Hi, RomeReactor,

Desktop effects are off.

The graphics card is an Intel one. I found the device manage, and it lists the graphics card. Here is what I found:

**Vendor:** Intel Corporation
**Device**: 82845G/GL[Brookdale-G]/GE
**Status**]: status
**Device type**: unknown
**Capabilities**: unknown

What do you think?

Thank you for your help :)

*edit* BTW, I tried downloading an mpeg vdeo and played it in the VLC player and had the exact some problem as when I play the ogg.

---

### Post by bone2006 on 2007-09-07
The 64bit version of ubuntu has a full screen problem with VLC.   Do you have the restricted drivers installed?  VLC can do full screen and works perfectly in ubuntu 64bit version when desktop effects are on, but when it's off it doesn't have full screen for me.  I posted this same problem I was having with VLC, but it's only a problem in the 64bit version of ubuntu.
I love VLC it plays anything you throw at it, works in windows, even plays things before the download is complete.

---

### Post by wobbly_bob on 2007-09-07
Hi, as far as I know ( I'm pretty certain ) that I have the 32 bit version. Is there a way of making sure?

Restricted drivers? I don't think so... I'm new to this, so I don't know :-) I clicked on "restricted" drivers  via the administration drop menu and it says "Your system does not need restricted drivers" 

Thanks for the help.

---

### Post by RomeReactor on 2007-09-07
I'm not certain this could help you, but if you're using the **i810** driver, try changing it to **intel**. In any case, take a look [here]("http://ubuntuforums.org/showthread.php?p=3326227#post3326227").

To find out which architecture you are running, enter this in the terminal:
```
uname -m
```

If it says **x86_64**, you are running the 64 bit version.

---

### Post by wobbly_bob on 2007-09-07
It works!!! Thank you, thank you, thank you! :-)

I changed the the rendering engine to X11 in the VLC player, and now it works just fine!

---

