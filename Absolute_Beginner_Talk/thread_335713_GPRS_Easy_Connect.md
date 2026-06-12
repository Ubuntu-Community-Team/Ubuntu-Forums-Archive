---
title: "GPRS Easy Connect"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by Cochese on 2007-01-10
Hi
 
This is my first time using Linux and I am really enjoying it so far even though I don't really know what I am doing yet. I am dual booting with win xp and the installation was really easy, but I am having trouble setting up my aircard with GPRSEC. This is the only way I can connect to the internet atm.  

I have been trying to follow these directions, but I am a little confused.:confused: 

[http://www.gprsec.hu/modules/forum/viewtopic.php?t=61](http://www.gprsec.hu/modules/forum/viewtopic.php?t=61)

What am I supposed to install first?

Can someone translate it into noob talk or give me a nudge in the right direction?

Will my aircard even work with this?

Thanks in advance for any help, I really would like to get this setup.

---

### Post by Cochese on 2007-01-11
No one can help me with this or show me an easier way to set this up?

---

### Post by online14230 on 2007-01-11
Hey Cochese...
Just read your post and was wondering: Whats so difficult about it?

Its actually quite simple, even for me who has no internet connection on my Ububox. See, all you have to do is 
1. Install all dependencies.
2. Download GPRSEC.
3. Install it.
4. Plug in all your provider details, which can probably be found on Ross Barkman's APN page..
5. Have fun :)

I know. Ive been teaching myself all about GPRS and 3G for about 2 months now, because I SERIOUSLY didnt want to try dial-up at home. Our lines here are too slow, and expensive. Ive also been learning to code in C, because I wanted to do exactly what GPRSEC does: simplify cellular surfing. Thing is, I think it would be easier if we built a .deb used that. It would make things a LOT easier for most newbies, especially those who arent lucky enough to have internet on tap. Im guessing  GPRSEC will REALLY help Linux in general, and Ubuntu in particular to pick up speed. Oh yeah, I've been checking and ALL dependencies so far are already on my system, so Ill be installing GPRSEC in about 5 hours, and as soon as its working, Ill post here. Wish me luck. If I get it right, expect a detailed howto... :)


B.

OK. Im back.
GPRSEC working like a charm. Im actually connected via it :)
Anyway, you dont need a tutorial because you provided a link to a perfect one. What Ill do though, is translate it later today (After Ive had a good sleep, just getting home from nightshift) and post it in this thread. Have fun trying so long. Just start at the top and go for it.

---

### Post by Cochese on 2007-01-12
Hi, Online.

My problem is that I don't have all the dependencies and I can't connect to the internet while I am running linux because I haven't set this up yet.  Yes, it would be so much easier if there was a .deb file, but I am so new to linux I don't know how one would even begin on that.  There is another page that has all the depencides available, but I'm not sure if I installed them right and I still need to do one more. I can't find the ones I installed in Synaptics. 

This is another good link from that site.

[http://www.gprsec.hu/modules/docs/#31112](http://www.gprsec.hu/modules/docs/#31112)

I'm glad you got it working and hope to read some of your instructions.
Thanks for the response.

---

### Post by Cochese on 2007-01-12
Okay, I got the program up and running. Whew!! I will post my steps as they might differ from yours.

Next hurdle, getting it to connect. I have Sony Ericsson GC83, but the only ones on the list are the GC75 and GC85. What card to you have? Was it on the list. How did you configure all of your settings?

---

### Post by online14230 on 2007-01-12
Hey Cochese!
It worked this morning, but since then, nothing. It doesnt seem to see my cellphone anymore :(
Anyway, I have a Samsung D500 and a Motorola C650 laying around, both with USB cables, so I tried with them. This morning it worked with the Vodaphone 3G connect card. Anyway, I pointed GPRSEC at the only USB port it seemed to find and it worked. After I tried with the phones, nothing. Ill be checking up on that link you gave me, and Ill get back to you as soon as I can. Ill post that tutorial within the next 4 hours...

---

### Post by Cochese on 2007-01-12
Do you get the message, "You might not have your mobile turned on, did you?"

or something like that.

Mine is a pc card in my pci slot, not an actual phone. I don't know what port to set it on. The device manager doesn't seem to specify what port it's on, or I am not reading it correctly.

Also, the DNS isn't showing up, maybe that's because it's not connected yet, not sure, but you can't type them in. I'll keep messing with it.

---

### Post by online14230 on 2007-01-12
EXACT same problem, and the language used on the GPRSEC forum isnt exactly legible :(
Anyway, Ill be fiddling tomorrow morning again. Its 01h30 in the morning and Im at work. Dog tired!!!

---

### Post by online14230 on 2007-01-12
I figure if you just try ALL the ports GPRSEC finds, one should work. Problem is, it found SO MANY on my PC.

---

### Post by Cochese on 2007-01-13
I think I figured out what port it is, COM 13(/dev/ttyS2)

/dev/ttyS2 is what shows up in device manager.

Still having the same problem, though. I don't think it is reading me card correctly. I think I need to make a script similar to the GC75 for my GC83, but I don't know how to use the Script Generator that they provide. DNS still doesn't show up.

Yeah, their instructions are difficult to understand. The translated english seems quircky and I don't think they are very sympathetic to linux newbie's, but that might be a lost in translation thing.

---

### Post by online14230 on 2007-01-15
Hi there... bit of a short weekend, AND I LIVED THROUGH IT WITHOUT UBUNTU!!!

Anyways, I broke Ubuntu while trying to install downloaded debs which needed dependencies met, so I downloaded them via XP, and they needed dependencies... blah blah blah.
Back to GPRSEC. My cellphones BOTH use /dev/ttyACM0 and /dev/ttyACM1. Now what are those? Anyway, I know they use those because thats what wvdial 'lsusb' says. GPRSEC wont find them. A friend said I should replace the old ip-up and ip-down tables and tit should work... not sure though. I gave up on GPRSEC last night and tried wvdial. OK. All was well with the setup. I ran 'wvdialconf /etc/wvdial.conf' and it spat out a WHOLE lot of data, saying that it found a modem at /dev/ttyACM0, then I edited /etc/wvdial.conf and added in the usernam, password and 'stupid mode = 1' bit, saved the file and ran wvdial. All goes well till it reaches the CONNECT bit. After it connects, it runs pppd (I dont know why) and then disconnects. It complains about having nothing to do! I dont want it to do ANYTHING. I just want it to sit and wait there till I tell it what to do. Now... where do I go to from here???

Looks like Im deeper in the brown stuff than I thought I was!!!
B.

---

### Post by online14230 on 2007-01-16
Okay, Okay. I did it. GPRS working like a dream. All I do is plug in the phone and double click on the icon on the desktop. [http://julian.coccia.com/blog/index.php?m=200501&more=1](http://julian.coccia.com/blog/index.php?m=200501&more=1) shows you EXACTLY how tyo do it, in a very short time. This took me about 3 minutes to setup, plus about thirty seconds to make a launcher. Try it, all you need is the information from your provider...

I found this after looking on the net for about ten minutes, cos I got tired of ](*,) over GPRSEC.

Have fun, 

B.

---

