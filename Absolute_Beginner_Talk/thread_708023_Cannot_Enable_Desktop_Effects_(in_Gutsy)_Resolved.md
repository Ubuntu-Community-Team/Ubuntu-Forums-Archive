---
title: "Cannot Enable Desktop Effects (in Gutsy) Resolved???"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by abhijitvalluri on 2008-02-25
There are quite a lot of threads on the topic "CANNOT ENABLE DESKTOP EFFECTS".
To be able to address them all, I've created this thread, so that everyone facing problems with Desktop Effects can know about this.

In one of the threads, I found a solution that works.
> 
...Here's how I did it:

sudo vi /etc/xdg/compiz/compiz-manager

I added the following line:
SKIP_CHECKS=yes

Then, I was able to turn on the effects. I noticed ...

You can see the entire post here
[http://ubuntuforums.org/showthread.php?t=583977]("http://ubuntuforums.org/showthread.php?t=583977")

But one question is troubling me.

Why are some graphics drivers Blacklisted in the first place???:confused:

What potential hazards, problems and risks do I face by introducing the line "SKIP_CHECKS=yes" in compiz-manager, which in effect disables the checks it performs one the graphics drivers  I have??? (I really don't know what checks it performs) 	:???:

Can it cause any long-term, severe or irreversible or unrepairable problem to my computer? :shock:

Please do excuse me for being so critical (and may be pessimistic) in this regard, but I want to keep my system safe and I DEFINITELY DON'T want to cause any damage to my computer by disabling the checks that compiz (or whatever application) performs.

---

### Post by oedha on 2008-02-26
can you post the display adapter of yours ? 
or 
what graphic card do you use ?
you can foind out from terminal by typing :==> sudo lshw -short -C display

---

### Post by jessika-kaos on 2008-02-26
I don't think it can cause any damage. Check this page:

[http://wiki.compiz-fusion.org/Hardware/Blacklist]("http://wiki.compiz-fusion.org/Hardware/Blacklist")

looks like it's just because of bugs

---

### Post by abhijitvalluri on 2008-02-26
82G965 Integrated Graphics Con

That is what I saw after typing "sudo lshw -short -C display" in the terminal

---

### Post by Babysittah on 2008-02-26
Thats right yo! Yo computah'z gutz might be the cause 4 all that, check it:lolflag:

---

### Post by abhijitvalluri on 2008-02-26
I have just experienced my **first** problem. I can't play ANY video at all!

On the following site, I found that intel 965 class of video drivers are blacklisted by compiz-manager
[http://wiki.compiz-fusion.org/Hardware/Blacklist]("http://wiki.compiz-fusion.org/Hardware/Blacklist")

Now it also says that the reason is "XV does not play with XAA under compiz, only with EXA "

After a bit of searching in this forum ([http://ubuntuforums.org/showthread.php?t=701567]("http://ubuntuforums.org/showthread.php?t=701567") )I found that XV is "X video extension", which in turn is an extension of X11 (your display protocol) to rescale video output (e.g. watch a divX movie in fullscreen).

Now, I think it all adds up.

By adding the line "SKIP_CHECKS=yes" to compiz-manager, I forcably enabled Desktop Effects on a blacklisted video card, and rightly according to the problem stated in the above mentioned site (wiki.compiz-fusion.org) I am unable to play videos.


Fine, everything tallies, but I ***want*** to use Desktop Effects **as well as** play videos and all.

:-k Is there a way to make gutsy run on EXA? Since that "reason" says "XV does not play with XAA under compiz, only with EXA" ???? :-?

P.S. Please help me out and solve this problem.
     In short my problem is: To be able to enable desktop effects as well as play videos audio etc.

---

### Post by sayakb on 2008-02-26
Btw, does anybody know how to enable direct rendering for Intel cards? I have GMA950 in my laptop.

---

### Post by rakusson on 2008-02-26
> **oedha said:**
> can you post the display adapter of yours ? 
or 
what graphic card do you use ?
you can foind out from terminal by typing :==> sudo lshw -short -C display

Hi,

your command to check the graphic card didn't work for me. Instead I used
```
lpsc -nn | grep VGA   
```

the output showed the details of my VGA card. What would be the output of your command? and wondering why your command didn't work for me. I am using 7.10

---

### Post by Golem XIV on 2008-02-26
> **abhijitvalluri said:**
> I have just experienced my **first** problem. I can't play ANY video at all!

On the following site, I found that intel 965 class of video drivers are blacklisted by compiz-manager
[http://wiki.compiz-fusion.org/Hardware/Blacklist]("http://wiki.compiz-fusion.org/Hardware/Blacklist")

Now it also says that the reason is "XV does not play with XAA under compiz, only with EXA "

After a bit of searching in this forum ([http://ubuntuforums.org/showthread.php?t=701567]("http://ubuntuforums.org/showthread.php?t=701567") )I found that XV is "X video extension", which in turn is an extension of X11 (your display protocol) to rescale video output (e.g. watch a divX movie in fullscreen).

Now, I think it all adds up.

By adding the line "SKIP_CHECKS=yes" to compiz-manager, I forcably enabled Desktop Effects on a blacklisted video card, and rightly according to the problem stated in the above mentioned site (wiki.compiz-fusion.org) I am unable to play videos.


Fine, everything tallies, but I ***want*** to use Desktop Effects **as well as** play videos and all.

:-k Is there a way to make gutsy run on EXA? Since that "reason" says "XV does not play with XAA under compiz, only with EXA" ???? :-?

P.S. Please help me out and solve this problem.
     In short my problem is: To be able to enable desktop effects as well as play videos audio etc.

Check my reply in this thread:

[http://ubuntuforums.org/showthread.php?t=695195]("http://ubuntuforums.org/showthread.php?t=695195")

It should answer most of your questions.

---

### Post by abhijitvalluri on 2008-02-26
Your suggestion works only for Totem movie player not for others. What should I do for other players, like Mplayer, SMPlayer, VLC, Real Player.

Also the video quality is very poor. Can I increase the quality of the video, like for instance increase the resolution of the video etc.

Thanks

---

### Post by Golem XIV on 2008-02-26
Sorry, I can't help you much more.  The only thing I can suggest is to fiddle with the other players' configuration settings to see if you can enable "No XV" video rendering.

I don't think you can increase the resolution of the videos.  That's something that is set at the moment of recording or encoding.

Your best bet so far is to get a decent video card, from what I've seen nVidia cards are the easiest to configure and run in Ubuntu.  Of course, if you have a laptop then you're SOL until Intel releases a driver that actually works.

---

### Post by abhijitvalluri on 2008-02-27
I indeed plan to buy an NVIDIA video card. The exact model of the card I plan to buy is NVIDIA GeForce 7600 GT. 

Is it compatible with Ubuntu, i.e. is it** "blacklisted"**? Can it play videos and at the same time be able to enable Desktop Effects without having to enable "No XV" (and of course that "SKIP_CHECKS=yes" line as well)????

Thanks

---

### Post by jessika-kaos on 2008-02-28
I traded my ATI card for a 7600 GT and it works beautifully. No problems with video playback at all, and I was able to get alpha blurring working in compiz, which isn't yet implemented in th ATI drivers. No regrets yet.

---

