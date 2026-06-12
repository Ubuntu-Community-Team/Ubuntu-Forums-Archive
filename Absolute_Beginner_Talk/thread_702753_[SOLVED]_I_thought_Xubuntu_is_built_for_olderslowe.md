---
title: "[SOLVED] I thought Xubuntu is built for older/slower PC..."
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by incen on 2008-02-20
I think my laptop is ok and not considerend as an really elder one. :P
It's with Intel centrino 1.7 GHz and 512+128 MB ram. All functions well in Windows XP so far.

However, after installing Xubuntu. Though the process to boot loader is extremely fast (a little bit bothers me in some sense :P), but REA~~~LLY slow to boot into Xubuntu. It takes about 5 min or so to go to the login page. What's wrong with this? This is even longer then booting into XP.

Also, when I browse webpage in Xubuntu, if I scroll my mouse up or down whenever it goes to the end of the page (upper bound or bottom bound), it just jumps to the next desktop. Like... there are 4 desktops available in Xubuntu (2 for Ubuntu) at the bottom right corner, right? And it just jumps to another one, which is so weird and a bit annoying. :(
Any way to fix this?

Thanks a ton!

---

### Post by divindavid on 2008-02-20
with your specs you can run ubuntu i am running ubuntu7.10 on my P3 at about 996MHz and with 256mb of ram faster than i ran windows

---

### Post by kerry_s on 2008-02-20
i've always thought xubuntu is a real bad job. you should try the debian version->
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso)

you can change the number of desktops and how they work in the settings.

---

### Post by bodhi.zazen on 2008-02-20
I think this is a common misconception about Xubuntu. Xubuntu uses XFCE and is marginally lighter then Ubuntu, mainly due to the lighter default Apps.

If you are interested in lightweight, try Puppy , DSL, Zenwalk.

Additional ideas : [http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

---

### Post by incen on 2008-02-20
Well... I didn't mean to choose really lightweight OS though. I just wanted to have Linux on my laptop so that I can play with Linux even back home, not just with Lab PC. At that time, I saw people so far like Xubuntu and it seems it fit my needs and my laptop's config. Well... I just don't know why it took long to get into login page. Usually it is really fast for my Lab PC. Well... since that is a monster one. Is this slowness a general issue for Xubuntu?

---

### Post by bodhi.zazen on 2008-02-20
No, the slowness you are describing is not typical for xubuntu.

---

### Post by incen on 2008-02-20
Then, what could be the possible cause?

I have 40 GB hard drive divided by 20/20 basically when I only had Windows on.
Last week, I put Xubuntu on and made it like this:
Disk C (20 GB): Windows system disk as usual
Disk D (4 GB): Fat32 (both Windows and Xubuntu can access to it)
Disk X (8 GB): for Xubuntu system
Disk Y (900 MB): for Xubuntu swap
Some space is taken by IBM as Access IBM function, I believe.

I so far haven't put much stuff in Xubuntu. Well... I should say, this slowness happened right after I installed Xubuntu. I was wrong about the time I mentioned (~5 min). It's more or less 3 min as I just measured. Really not sure why... :(

---

### Post by Iceni on 2008-02-20
Xubuntu is kind of slow when booting on my old laptop as well. Probably about 2-3 minutes, and I don't use gdm. 

The difference between ubuntu boot and XP boot is mainly that XP is not done booting when you log in, while Ubuntu (mostly) is.

---

### Post by incen on 2008-02-20
I see. Nice to see your reply! At least I know it's kinda ok to wait for its booting. Otherwise, it really drags me crazy since I keep wondering if something wrong with my installation or getting some bad packages. What's GDM?

---

### Post by doorknob60 on 2008-02-20
Does it show anything weird when it boots up? Like my brother's computer....something is definately wrong with it because it hangs for about two miutes sometimes when loading hald (he has Xubuntu. There's also a way to disable the xubuntu logo so you can see if it's hanging somewhere during boot, I just forgot it :P Can someone remind me on that? Because that's NOT normal for Xubnutu at all, because on one of my other computers it has similar specs and loads Ubuntu in under a minute.

---

### Post by mimada on 2008-02-20
Try booting the live CD. If it's as slow (or slower) than your installation, it may be a problem with Ubuntu. If it boots faster or runs smoother then it's a problem with your installation.

---

### Post by incen on 2008-02-20
Well... what I meant "booting" is the period between the boot loader and the login page. And during that time, it's entirely black. No any Xubuntu logo yet. >< That is why I felt strange and uncomfortable about it. So... that's why I have to ask... :P

Anyway, does anyone have the idea why it will jump to another desktop while I scroll my mouse? I think I said it wrong. It happens when I scroll in a desktop if there's nothing more can be scroll... Does this make sense? For example, if the desktop now is without anything on it, once I scroll my mouse and it will jump to the next or previous desktop depending on which direction I scroll my mouse. Or if there's a terminal and I scroll my couse, it happens too.
Any ideas? :confused:

---

### Post by Iceni on 2008-02-20
> **incen said:**
> I see. Nice to see your reply! At least I know it's kinda ok to wait for its booting. Otherwise, it really drags me crazy since I keep wondering if something wrong with my installation or getting some bad packages. What's GDM?

GDM is the pretty graphical interface you use to log in:) It takes some memory so I diabled it and boot into a command line.

---

### Post by brian10161 on 2008-02-20
I think I may have an idea to try. It fixed my Toshiba Satellite A100's Boot time. My boot time without this fix was around 10 minutes. Once up and running it was fine, but still...

Open a terminal, and install Startup Manager

```
sudo aptitidue install startupmanager
```

and then type

```
sudo startupmanager
```

Then enable "Enable text during boot"

That completely fixed mine.

If you don't want to install the program just yet, try this. When booting, push ALT + F1 and it will show text when booting. If that speeds up your boot time, then do what I posted above. That should fix it for you!

Hope that helps mate, Xubuntu shouldn't be that slow on that system, my A100 is a Celeron 1.73GHz and boot time is under 40 seconds now! You should be able to run Ubuntu (GNOME) with no speed problems on that system!

---

### Post by incen on 2008-02-20
> **mimada said:**
> Try booting the live CD. If it's as slow (or slower) than your installation, it may be a problem with Ubuntu. If it boots faster or runs smoother then it's a problem with your installation.

Really thanks for this idea! I tried and now I think I know what my problem is! :popcorn:
It took about the same time or probably longer to boot into Xubuntu with Live CD. I think part of it comes from the reading speed of the CD/DVD-ROM. Anyway, after comparing, I found the problem!
The totally black period happening between the boot loader and login page is actually the period that the Xubuntu loading/running bar! Because I haven't even seen the running bar since I installed it, I didn't notice that should be there! Instead of having a loading bar, it is a totally black screen. How can I get the running bar back if it was lost but should be there originally? It looks kinda weird when you know the computer is on but the screen has totally nothing on. :)

---

### Post by brian10161 on 2008-02-20
If your not seeing a boot screen, my post should help you out. It worked on mine mate :)

---

### Post by incen on 2008-02-20
So it's just because I don't have startupmanager? It's kinda weird though. Why isn't it installed when I install Xubuntu??? I just hope I can see the loading bar.......... :(

---

### Post by incen on 2008-02-20
> **Iceni said:**
> GDM is the pretty graphical interface you use to log in:) It takes some memory so I diabled it and boot into a command line.

So does it mean that instead of disabling my GDM I have to enable it to see the loading bar? But where to?

---

### Post by sumguy231 on 2008-02-20
> So does it mean that instead of disabling my GDM I have to enable it to see the loading bar? But where to?
I should clarify for this thread that the graphical login manager (GDM) and the graphical loading bar (usplash) are different and independent programs. I've never used startup manager, but I think that 'text on boot' option will disable the loading bar.

---

### Post by incen on 2008-02-20
Well... I didn't modify my Xubuntu at all after installing it. However, I don't have the loading bar at all. [COLOR="Red"]**I just want it back!!!**[/COLOR] I don't have "text on boot", either. While loading/booting, it's just totally black, NOTHING AT ALL!

I just want to be normal... Like is there something to set the loading bar back? :KS

---

### Post by MasterJS on 2008-02-20
It means that the resolution for that loading bar (the usplash) is set to too low a resolution for your screen. Using startup manager, you can change the resolution. Change it to 1024 x 765. If it is on 800 x 600, then you'll never see it.

---

### Post by brian10161 on 2008-02-20
> **incen said:**
> Well... I didn't modify my Xubuntu at all after installing it. However, I don't have the loading bar at all. [COLOR="Red"]**I just want it back!!!**[/COLOR] I don't have "text on boot", either. While loading/booting, it's just totally black, NOTHING AT ALL!

I just want to be normal... Like is there something to set the loading bar back? :KS

When you enable the Text on bootup option, it will put the text BELOW THE SPLASH. The splash screen will still be there, but it fixed my bootup. Trust me.

When booting, push ALT + F1 and you will see text INSTEAD of the boot screen. If this speeds up your boot time, then enabling Text on boot will speed up boot time while retaining boot logo.

Trust me :)

---

### Post by incen on 2008-02-20
> **MasterJS said:**
> It means that the resolution for that loading bar (the usplash) is set to too low a resolution for your screen. Using startup manager, you can change the resolution. Change it to 1024 x 765. If it is on 800 x 600, then you'll never see it.

OMG! I almost cried out when I finally saw the little mouse in a circle!!!
I installed startupmanager and realized that the resolution was even worse. It's on 640 x 480. :( I picked it back to 1024 x 768 and then reboot. Then, I saw something differently! I saw little mouse in a circle and a bar even while switching off!!! I didn't have this before! And then, while reboot, I got the loading bar again! Just as it with my Ubuntu!!! :popcorn:

And then, more amazing thing is the booting time is just about 30 sec!!! [COLOR="Red"]**From 3 min to 30 sec!!!**[/COLOR] I don't know the resolution problem would almost kill my laptop (I mean in some way - slowness). The resolution in login page and after is just fine so I didn't realize there's any problem. I'm glad that I dared to ask this question and now it got solved!!!

Thank you all, guys! :lolflag:

---

### Post by bodhi.zazen on 2008-02-20
Woot ... :guitar:

Please mark this thread as solved, it saves the time of many volunteers looking to help ...

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by incen on 2008-02-20
Haha, I just did it. Probably at the same time as you posted this one. Since I was looking for how to mark it... Thanks for reminder! ^^

---

