---
title: "Ipod Nano 8gb help"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by buffybot5 on 2008-01-06
On Dec 24th I switched to Ubuntu.  On Dec 25th, I got an ipod nano.  I have tried every program possible.  I am so inexperienced with linux, and I am over my head.  With gtkpod, I managed to get files onto the ipod.  Of course, the ipod says I have no music, just file space taken up.  I tried Hipo, Amarok, and Rhythmbox.  None of them acknowledge the ipod.  Now, when I pull up gtkpod, with the ipod plugged in, gtkpod crashes.  When I pull up rhythmbox, the ipod icon disappears.  

So, I uninstalled everything and tried Banshee and Exaile. I installed the ipod driver for Exaile, as well as python-gpod.  

Now when I click on ipod device driver/llittle plug button on Exaile, I get a message saying: Error connecting to iPod. Make sure you specify the right mount point in the plugin configuration.  

I want to throw the computer and ipod in a lake, I'm so frustrated.  What is a mount point? 

I would really appreciate help from someone with more than a week's experience with ubuntu!  Thanks :)

---

### Post by salempc on 2008-01-06
Well, I also turned to ubuntu around 20 Dec, and I also got an iPod Nano 8gb which will sync songs but won't show them up.

I found out that this was due to Apple's ItunesDB file that will only work with iTunes. As far as I know there's no fix to it yet, but I'm sure it will be fixed soon ;)

Am I right? If not, I'd love to know how to do this too...

---

### Post by eroica on 2008-01-06
i have a 2nd gen ipod nano and when i plug it in i get an icon on my desktop showing the ipod name. My system is also setup to use Rhythmbox when an ipod is plugged in. what are u getting on your desktop on plugging in your ipod? Also have you downloaded any music onto your ipod from anywhere? I'm no expert but let's see if we can get you working w/Rhythmbox. First let's make sure you are setup properly. In the menu goto system>Preferences>removeable Drives and media and make sure Portable music player has rhythmbox selected. Also in Rhthmbox under edit>plugins make sure portable players plugins is checked. I included two snapshots to guide you.You may have to log out and in again for changes to take effect...

---

### Post by Joeb454 on 2008-01-06
eroica, you should realise that the 2nd gen Nano's work fine with Linux, it's the 3rd Gen Nano's & iPod Touch/Classic's that don't work.

It's something to do with the way the iTunesDB file is encrypted I believe. Sooner or later there'll be a way to use them on Linux/Ubuntu, until then the only way you can use them properly (as far as I know!) is to dual-boot with Windows :(

---

### Post by eroica on 2008-01-06
ok i didnt know and he didnt state it in his question. forgive me for trying to help.....

---

### Post by buffybot5 on 2008-01-06
Thanks for the quick responses! I will attempt to eroica's suggestion with Rhythmbox.  I'm not certain what generation of nano it is.  I may  just have to use my office computer with windows for ipod, if all else fails.

---

### Post by buffybot5 on 2008-01-06
Wait, Rhythmbox crashes if the ipod is connected.

---

### Post by jd8001 on 2008-01-13
Hey,
    I'm a little late on this reply, but I used the thread at this link to get my third gen ipod nano to work
[http://ubuntuforums.org/showthread.php?t=611404&page=2](http://ubuntuforums.org/showthread.php?t=611404&page=2)

Make sure you follow his instructions to manually fix the bug/problem. Also, I would recommend going into itunes and restoring the ipod to factory conditions first. It takes about five minutes and seems to set the device to a great starting point. As a testimony to the method I've had to fix my ipod about three times and each time it works. I've gotten good enough where it takes me about ten minutes to fix my ipod after I've been screwing around with it. Also, I highly recommend gtkpod for music or video, however I'm still working on cover art and pictures


JD

---

### Post by buffybot5 on 2008-01-20
Thanks! Turns out resetting it on another computer did the trick. Now it works just fine with gtkpod.   I just have to figure out gpodder for the podcasts!

---

### Post by citizenchris099 on 2008-07-01
the following links methods worked out perfectly for me. the first is for amarok and the second is for rhythmbox. 

[http://maketecheasier.com/how-to-sync-amarok-with-ipod-classic-3rd-generation-ipod-nano/2008/03/10](http://maketecheasier.com/how-to-sync-amarok-with-ipod-classic-3rd-generation-ipod-nano/2008/03/10)

[http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)

---

