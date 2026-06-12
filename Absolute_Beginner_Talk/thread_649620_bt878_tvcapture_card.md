---
title: "bt878 tv/capture card"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by bumanie on 2007-12-25
I have a winfast tv/capture card (with the very common bt878 chipset). Not interested in tv, only the analog video capture facility.
1) I know the driver is in feisty's kernel
2) I know that I have permission to use it (only user)
3) I know that it is listed in hardware as A) a video capture and B) a sound capture device
What I don't know is to make it available for use.
Is there a list that needs to be modified or something?
I have crawled the internet and found a few tips on how to ensure that it is installed and recognised, but I have not been able to find anything describing how to enable it so I can use it.
Does anyone have any idea? 
Any help greatly appreciated.

---

### Post by overdrank on 2007-12-25
> **bumanie said:**
> I have a winfast tv/capture card (with the very common bt878 chipset). Not interested in tv, only the analog video capture facility.
1) I know the driver is in feisty's kernel
2) I know that I have permission to use it (only user)
3) I know that it is listed in hardware as A) a video capture and B) a sound capture device
What I don't know is to make it available for use.
Is there a list that needs to be modified or something?
I have crawled the internet and found a few tips on how to ensure that it is installed and recognised, but I have not been able to find anything describing how to enable it so I can use it.
Does anyone have any idea? 
Any help greatly appreciated.

Hi and maybe this will help
[http://www.mythtv.org/wiki/index.php/Tuner_Card](http://www.mythtv.org/wiki/index.php/Tuner_Card)

---

### Post by bumanie on 2007-12-25
Thanks for trying overdrank. I had read that already. Unless I am missing something, it doesn't help with my fundamental problem of how to add the capture card to a gui or how to enable its use via a command to capture video. I need to be able to choose it somehow so that I can capture from an analog video camera.
Guess I could upgrade to a digital video camera - that would solve my problem (and probably be a whole lot easier).

---

### Post by rkd on 2007-12-25
I don't know anything about using TV capture cards, but let me ask a couple of questions that might get you going on the right path.  (This may be one of my lamer posts, since I'm basically just guessing here.)

When you say you know the driver is in feisty's kernel, how sure of that are you?  Might it not be loaded, so you have to manually load it? (I think that's done with a modprobe command, or something like that).

What do you mean by (only user) at the end of the assertion that you have permission to use the device?  If you are logged on as bumanie, but the device is owned by root and doesn't set appropriate permissions for world access to the device, you won't have permission to access.  If you are logged on as root, then I guess this wouldn't be the case, but I gather that logging on as root is not typical.

An app with a GUI that would use the device might find it and display it among the list of devices it can use and let you select it from the list.  Have you tried running an appropriate app to see whether it can find the device and offer to use it?

A command line app that would use the device probably would expect it as one of the command line parameters, in which case I guess you'd have to know its name.  I suppose you could look through the /dev directory, looking for a device or devices with names related to winfast or bt878.

---

### Post by bumanie on 2007-12-25
Hi rkd, 
Sorry I took so long , I was reading about file system structures.
When you say you know the driver is in feisty's kernel, how sure of that are you? Might it not be loaded, so you have to manually load it? (I think that's done with a modprobe command, or something like that).

I followed a how to that said bt878 was in the kernel since a version well before feisty. I also did a number of suggested command lines and the bt878 was in the list that was generated. I am at work now and can't remember the url for the how to I followed - it should be in history on my home computer, but that doesn't help now - Sorry.

What do you mean by (only user) at the end of the assertion that you have permission to use the device? If you are logged on as bumanie, but the device is owned by root and doesn't set appropriate permissions for world access to the device, you won't have permission to access. If you are logged on as root, then I guess this wouldn't be the case, but I gather that logging on as root is not typical.

In the how to it gave a command to see which users had access to the card its ouput was my username - and as stated, I am the only user on the computer

An app with a GUI that would use the device might find it and display it among the list of devices it can use and let you select it from the list. Have you tried running an appropriate app to see whether it can find the device and offer to use it?

So far the only GUI I have seen it on is the list of hardware - there doesn't seem to be any reference to it on any other GUI. As for running a particular app, I have no idea which one to run. That's why I started reading up about the file sytem structure, but it isn't something you can learn in few minutes.

A command line app that would use the device probably would expect it as one of the command line parameters, in which case I guess you'd have to know its name. I suppose you could look through the /dev directory, looking for a device or devices with names related to winfast or bt878.

Thankyou for that suggestion. I will try and look later today when I finish work and have slept (night shift worker). In fact thankyou for all your input. I guess I was hoping someone would read the post and say "Yeah , I did it this way,"or "hey, follow this guide." 

Wishful thinking I know, but the guide I followed (which confirmed the installation of the chipset drivers etc.) only went that far. It did not say how to make it device available for use.

---

### Post by rkd on 2007-12-25
Sorry, I assumed you were more familiar with Linux than you seem to be.  I'm just a beginner, too.

Anyway, I thought you would have already decided what application you were going to use to take the video from the capture card.  That's the application I meant you could check to see whether it found the card.  I did some searching and some of the applications I found (not sure which, if any, of these would work with your card) were:

tvtime
webcam
unicap/ucview
XdTV/Xawdecode
Xane
KwinTV
Zapping
and, of course, MythTV

I didn't check whether they are in the Ubuntu repositories.  Probably at least some are.  So if you haven't already chosen an application, you might look over these and choose one that looks simple to set up, just to use it to see whether the hardware is working.

And I saw one reference to the video device name being /dev/video1 (don't remember which card that was).  I don't know whether other cards come up as difference device names.

If you would post a link to the howto you were following, I'd like to look at it.  It might give me an idea that you didn't get.

---

### Post by bumanie on 2007-12-25
Sorry I'm still at work so can't find the guide (I did look, but couldn't find it. It took a long time to find in the first place! I hope it is still in my history). There are some areas of ubuntu I'm becoming fairly familiar with, but others such as this (things I have never looked at before) sometimes takes a while to get ones head around and 'think linux' so to speak. When one has only used these programs under windoze, it sometimes takes a bit to get out of that mode of thinking.
OK, I now see what you mean re the app, as I said sometimes getting out of the windoze mode of thought is hard when one doesn't find specific instuctions to steer one in the right direction.
My video device was video0 (zero). Out of the programs you've listed (and thanks very much for that), the only one I've heard of is myth tv. The program is really unimportant, as long as it works.
Am I right in thinking that myth tv would probably be the best supported?
I believe it does support the bt878 driver. From what I have read, the bt878 is a very common (although slightly old) chipset, used in many (older) capture cards.
I guess when I get the time I will try and set up myth tv or one of those others you've so kindly mentioned.
PS: There are post X-mas sales are starting here in a few hours. May be I should buy a digital video camera - it would probably be easier!!! 
Thanks again.

---

### Post by rkd on 2007-12-25
I, too, only recognize MythTV from that list.  MythTV no doubt is well-supported, but some of the others might also be well-supported.  I simply don't know.

One thing about MythTV is that it does a lot and so might be kind of complicated to configure after getting it installed.  I got the impression that some of the other programs were much simpler, so they might be quicker to get installed and configured.  And maybe one or two of them are already installed.  If the point is just to find out whether the TV card and its driver are working, then maybe a quick to set up program would be better for the test.  But if you aren't in a rush and think you might want to use MythTV in the long run, perhaps it would be worth a little extra time to set it up now to do the test.  It really is your call, and I don't know enough about any of the programs to give good advice.

A digital video camera might be easier to set up and get working (though I have no experience with that), but I'm pretty sure it is a lot more expensive.  Again, your call.

---

