---
title: "OMG I killed it :)"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by redmonster13 on 2007-08-18
I installed ubuntu ultimate and ran the video driver update with envy, I am now at the command line with no graphical interface at all. How do I fix this? I am posting on my little crappy folding box right now and really dont want to do another reinstall if I can avoid it.

---

### Post by JcZndeR on 2007-08-18
i suggest u rerun envy with
```
envy -t
```

---

### Post by redmonster13 on 2007-08-18
I still cant get xserver to start, any ideas on which driver to install?

---

### Post by Arisna on 2007-08-18
Okay, what graphics card do you have?  Unless it's a nVidia or ATI card, you don't want to use Envy.

Also, I'm pretty sure Envy backs up the xserver configuration before it alters it, but you might do best to run "sudo dpkg-reconfigure xserver-xorg" and choose the most appropriate driver.  VESA is always a safe choice.

---

### Post by redmonster13 on 2007-08-18
I think you saved me some trouble and taught me something new, thank you very much.

---

### Post by chuckyp on 2007-08-18
This is exactly why people shouldn't be using envy or automatix or any of that garbage.

---

### Post by Arthur Archnix on 2007-08-18
What is this envy?

An advanced script? Or something more sinister, like Automatix?

---

### Post by redmonster13 on 2007-08-18
Well I have killed it about 7 more times since I posted this. Trying to get twinview working and my resolutions set is driving me nuts. Normally I would just boot back into windows and play a game or something, but I have finally made the switch. I formatted my windows drive and I am done with it, so I have no choice but to get this working.

BTW, no I still dont have twinview working.

---

### Post by funpop on 2007-08-18
post some details of your card..
its fairly easy to setup twinview with a nvidia card

---

### Post by redmonster13 on 2007-08-18
MSI 6800 ultra (nvidia)

I am running  a 22 inch LCD via dvi and a 19 inch lcd via vga, so I usually get a black screen on the 22 inch and a cute little floating note on the 19 inch telling me something about exceeding maximum resolution. I unplug the 19 inch and the 22 will work.

so I am ploding through by doing searches on this site to find anything about twinview.

---

### Post by funpop on 2007-08-18
do you use nvidia's drive tool to set up your twinview ?

in a terminal type: nvidia-settings

the driver you need is nvidia-glx-new, just install it from the repos
To enable the driver, run "sudo nvidia-glx-config enable".

---

### Post by redmonster13 on 2007-08-18
I just finished another reinstall and I am now installing updates, I will try that and let you know how it goes.

---

### Post by scotty32 on 2007-08-18
instead of reinstalling cant you run the 

```
sudo dpgk-reconfigure xserver-xorg
```

when at command line - i had loads of trouble with an ATI card kept reinstalling till a learnt that line

---

### Post by redmonster13 on 2007-08-18
Ok, so twinview is working. 

Now to get my back button on my mouse working then it is on to getting compiz-fusion up and running.

I expect more reinstalls :)

---

### Post by Arthur Archnix on 2007-08-18
Reinstalls... man... it took me so long to figure this out that I get mad when I see this. Sorry, but I get upset to see other people suffering through the same windows-dementia that held me for so long.

Linux isn't windows. In windows, if you don't set something up right simply removing it or making the right changes doesn't mean your mistakes aren't there. Buried deep, in that mysterious cavern called the "registry". But linux doesn't have that. 

If you make a mistake in linux, install something you shouldn't, when you remove it it's gone. To Linux, it's like it never existed. You can install, mess up and fix it, and then there's no difference, none at all, than if you installed and got it right the first time.

May you find the ubuntu way. [-o<

---

### Post by redmonster13 on 2007-08-18
telling me I did something wrong isnt much help, how about next time adding something constructive.

I got it all working BTW for anyone who is interested.

---

### Post by Caffeine_Junky on 2007-08-18
Glad to see you got yourself all setup and working !  Nice job!

---

### Post by redmonster13 on 2007-08-18
I'm gonna cry, I had everything working perfect and I restarted to get some updates and now my back button doesnt work again (not a big deal I can fix it) and none of the desktop settings are being saved when I exit.

I have my storage hdd with an icon on my desktop, but when I restart I have to remount the drive every time to get it to show up on the desktop. In turn the picture that I use for the desktop background has to be reassigned as well.

Does anyone have any advice on the current batch of problems?

---

