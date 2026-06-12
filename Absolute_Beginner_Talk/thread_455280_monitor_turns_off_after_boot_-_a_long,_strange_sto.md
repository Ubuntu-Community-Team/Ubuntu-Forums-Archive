---
title: "monitor turns off after boot - a long, strange story"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by HarmonicaGoldfish on 2007-05-26
This is an odd little problem. It's a bit of a long story, but I want to include as many details as I can. I am new ish to linux and am not sure what is important info or not.

It began this morning. I was working as normal, surfing the internet and importing pictures from my camera, when all of a sudden my screen went black.

I shut off the computer manually, restarted it, and saw the Gateway splash screen, then the screen went black again. The computer started up though, I heard the song it plays when it goes to desktop.

So I brought it in to my local computer store to  be checked. I wanted to make sure it was the monitor and not something else. I had a funny feeling that perhaps a combination of the latest security update and plugging in my camera may have done something. The problems began just after I had plugged it in (usb). 

I need to mention that I have a 4 year old Gateway Profile. It is an all-in-one computer, the hardware is all attached to the back of a flat screen - so to change the monitor will be a pain in the butt I think. Here it is, it is the 4xl model: [http://www.referenceguide.com/reviews/gatewayprofile4.htm](http://www.referenceguide.com/reviews/gatewayprofile4.htm)

The service guy plugged my computer into another monitor and it no longer turned off after the splash. You could see it going through its bootup process. 

Right away he decided that it had to be the monitor so he shut it off. 

Luckily my father has an extra monitor, so I drove straight out here to pick it up. He suggested we try it out before I brought it home to make sure it worked - it is quite a large beast. 

So, we plugged it in, we could see the boot process - it spent quite a bit of time doing a force check, which I figured was because I had manually shut off the computer quite a few times. Then it went to the ubuntu start up image (the word ubuntu with an orange indicator line under it). As soon as it got to the end of the indicator line the monitor shut off, but the computer continued starting up because i could immediately hear the desktop song.

We did this a few times, and I realized that I no longer see the nvidia splash which usually comes directly after the Gateway splash (I think, around then in any case). So that got my dad to thinking that it must be a problem with the card or the driver.

But why would the monitor attached to my computer only show the gateway splash and nothing else before it goes black, and the plug in monitor show most of the bootup process and then go black?


Could it be a combination monitor/driver or card problem?

What can I do to see my computer again? I am presently writing this from my dad's pc (windows xp).

Is there something akin to windows safe mode so I can bypass nvidia?

My computer runs Fesity Fawn (upgraded from edgy) with the latest security update (this morning, around 6am EST).

Please help!

---

### Post by Happy_Man on 2007-05-26
Hmm... your problem is indeed strange. Did the service guy make sure it goes all the way to boot and login before shutting it off, or did he just yank as soon as it showed that it was booting? That's the only suspicious part.....

---

### Post by HarmonicaGoldfish on 2007-05-26
no - he felt (and at the time I agreed, little did I know...) that since we were seeing everything on the plug in monitor where before it was black on my monitor that it must be the monitor that had the problem.

At this point I do not even know if it is monitor, driver, card, or a combo. Before I bring it in to someone else...I'm hoping someone here can help to shed some light on this dilemma!

---

### Post by HarmonicaGoldfish on 2007-05-26
these are the specifications for the lcd panel and the video card:

LCD Panel 	17.0-inch active matrix TFT XGA (1280 × 1024) LCD color panel.

    * Maximum color depth: 16.2 million colors.
    * 0.264 mm × 0.264 mm.
    * Viewable angle: 30° through 90°.
    * Supports Video Scaling. 

Video Graphics Controller 	GeForce4 MX 440 with AGP 8X; 64MB of 250 DDR

---

### Post by HarmonicaGoldfish on 2007-06-02
the issue has evolved ;)

Monitor no longer turns off...now I have flashing colours and strange terminal activity.

I've started a new thread here --> [http://ubuntuforums.org/showthread.php?p=2767004#post2767004](http://ubuntuforums.org/showthread.php?p=2767004#post2767004)

---

