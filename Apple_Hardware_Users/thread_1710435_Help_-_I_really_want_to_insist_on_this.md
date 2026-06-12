---
title: "Help - I really want to insist on this"
date: 2011-03-19
forum: Apple Hardware Users
---

### Post by canhoto on 2011-03-19
Well... I don't stop asking questions and problems.

Now...:
- Until now Ubuntu would start up automatically and I had to hold "x"  when booting to start up Mac OS X, which is still my main OS;
- To change that, hoping to automatically start up from Mac OS and  holding "l" if I wanted to run Ubuntu, I changed the yaboot.conf file,  adding
> default=macosx I also ran the ybin

When I restarted:
- Mac OS didn't start up automatically
- Ubuntu didn't start up automatically
- Ubuntu didn't start up even if I hold "l"
- Mac OS does start up if I hold "x", like before

So, I have the same "x" need to run Mac OS... but I can't get to Ubuntu anymore!

How can I solve the problem without having to reinstall Ubuntu?

Thanks

---

### Post by applemuncy on 2011-03-20
From:
[https://wiki.ubuntu.com/PowerPCFAQ#Yaboot%20Configuration](https://wiki.ubuntu.com/PowerPCFAQ#Yaboot%20Configuration)

try changing:
default=macosx
to:
defaultos=macosx

---

### Post by linuxopjemac on 2011-03-20
[http://mac.linux.be/content/yaboot](http://mac.linux.be/content/yaboot)

---

### Post by canhoto on 2011-03-20
Sure, thanks, but I don't now how to access Ubuntu again. If I do nothing when booting, I will have a black screen. If I hold "l" it will be the same - black screen.

Only if I hold "x" I'll have Mac Os X.

---

### Post by canhoto on 2011-03-20
Good news.

I don't know how, but I managed to have the yaboot screen and access Ubuntu again, Now I'll try to follow the instructions you gave me.

---

### Post by canhoto on 2011-04-03
Now it automatically starts up Mac OS X, but I don't know how to choose Ubuntu... I tried to hold down "l", but without success.

---

### Post by B_Free on 2011-04-03
Don't hold down the l or the x. Just type l and then return. Or x and then return if you want the Mac. OR
When starting the machine, hold the option key down (you have to wait a few seconds) then using the arrow keys select the drive you want and then select the arrow pointing right, then the return key.

---

### Post by canhoto on 2011-04-04
> **B_Free said:**
> 
When starting the machine, hold the option key down (you have to wait a few seconds) then using the arrow keys select the drive you want and then select the arrow pointing right, then the return key.

I just have a black screen when I start up with the option key. I tried several moves but it didn't work. It ends always with rebooting from Mac OS.

---

### Post by B_Free on 2011-04-04
I've been where you are. These are a few of the things I've done, some work, some don't. 
When you start the Mac OS, does it say something like, there is another drive that could not be mounted, gives you the option of rejecting, ignoring it, or initialize it? Did it happen the first time you started the Mac OS, and you opted to reject it? If you did reject it, it will be hard to get it back.
Try starting from your install disk (Linux), when the desktop appears (Ubuntu), say restart, then hold down the option key. It should give you the terminal option of l (for linux), x (for the Mac), and c (for the CD). If it does, type l, and press return.
If you don't have a live CD, then start up from the Ubuntu install CD and the prompt in the upper left corner, type l and then return. See if that works. If it returns with another boot prompt type c and return. Start from the CD and then restart and, hopefully, type l and return.
OR
Put your CD in (your in your Mac OS) and restart. Instead of holding down the c key, hold down the option key. You should get at least the choice between starting from the CD or the Mac OS. If the Linux drive is shown, choose it, press return.

---

### Post by canhoto on 2011-04-04
The problem is that with my monitor (an Asus) I can't see what's going on. It says "no signal" and then it goes to standby (black screen). When I startup Mac OS, for instance, I never see the apple and the spinning wheel. The first image I see is my desktop.

Anyway, I tried with an old Apple monitor, holding down the alt key, and the two images were there (Mac and Linux). I tried two or three times, but there was a very quick screen with something written, and then it turned back to Mac OS. The third time I managed to see that I had to press "l" to go to Linux. There was a bit of a confusion and I had the Yaboot prompt. I typed "Linux" and there it was, my Ubuntu back again.

The question is: what exact configuration do I have to have in yaboot.conf, so that my default OS (if I just press the power button) is Mac OS but I just have to hold down "l" on start up to go to Linux?

---

### Post by canhoto on 2011-04-04
Well, I think I finally can manage it. The problem is that I don't see anything of yaboot with my monitor. But I inserted a "delay" line in the yaboot.conf (of about 15 sec). Now I know  when the prompt is there waiting for my "x" or "l"; it gives me time to type "l" and enter, and if I do nothing, after 15 secs it goes to Mac OS. It slows down the overall start up process if I just want to go to Mac OS, but I don't mind to pay the price and have Ubuntu. Anyway, most of the time I have the computer sleeping rather than shut down, so that's not a problem.

---

### Post by B_Free on 2011-04-05
No! The only time you hold down a key is when you are in Mac OS and you want to start up from the cd. Then you hold down the c key. If both Linux and the Mac are on the same drive you can only get to Linux by holding down the option key. You never hold down the l key. You type l (one time when you see the prompt) and then the return key. If you see both drives when you hold down the option key, select the correct drive and press return.
Did you install Linux when your Asus monitor was connected? You probably have to edit your xorg.conf file. Search this forum, there are plenty of people explaining how to do that.

---

### Post by oswaldkelso on 2011-04-06
Provided you've configured yaboot correctly you can get back from OSX control buy simply zapping the pram.To stop OSX gaining control again the recommended solution is to delete OSX and install a properly supported OS for PPC like Debian :)

---

