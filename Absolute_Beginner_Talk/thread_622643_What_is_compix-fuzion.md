---
title: "What is compix-fuzion?"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by webmiester on 2007-11-25
Hi guys,

I just upgraded from Kubuntu Fiesty to Kubuntu Gutsy Gibbon using Adept Manager.  I am using a Dell Inspiron 4000 laptop with PIII 850Mgz, an ATI video card, and a aroung 256KB memory

The performane is really really slow :( It like stops every 2-5 seconds, like as if the computer is perpetually busy, irregardless of what applications I open.  Before I do a clean reinstall Ild like to find answers as to why it might be extra slow.

Ive been looking through the threads, and I found that a few people blame it on "compiz-fuzion",apparently really slowing down on ATI systems.

What is Compiz-fuzion?  Is there a way I can by-pass this thing?

Also, if anyone else has any ideas why my computer is extra slow, Ill really appreciate it.

Oh, btw, Ive tried these:

taken from :[http://ubuntuforums.org/showthread.php?t=558731&highlight=gutsy+slow+kde](http://ubuntuforums.org/showthread.php?t=558731&highlight=gutsy+slow+kde)

Create a file at "~/.config/xserver-xgl/disable" - in my case I put a simple line like "##comment", although I suspect the only important issue is that the file exists. After restarting X, xgl is no longer running, instead I have good old Xorg again.

and this too:

sudo apt-get remove tracker
-- which only gave me a tracker not installed error...

---

### Post by cookies on 2007-11-25
First off, I don't think Kubuntu comes with Compiz Fusion..., some one back me up here.

And, as for slowdowns, I haven't the clue, but you could try

sudo apt-get remove strigi

---

### Post by macaholic on 2007-11-25
> Compiz Fusion is the result of a merge between the well-known Beryl composite window manager and Compiz Extras, a community set of improvements to the Compiz composite window manager. Compiz Fusion aims to provide an easy and fun-to-use windowed environment, allowing use of the graphics hardware to render each individual window and the entire screen, to provide some impressive effects, speed and usefulness. The first Compiz Fusion developer release was Compiz Fusion 0.5.2 on August 13th 2007, shortly after Compiz 0.5.2 was released. First stable release of Compiz Fusion is 0.6.0 released on October 20 2007. (compiz-fusion.org)
It shouldn't be slowing you down unless you enabled it when upgarding. My guess for why your system is sluggish, would be because your hardware is limiting it. If you wanted better performance I would change to Xubuntu instead, I have it running on my older machines and it works alot better then normal Ubuntu.

---

### Post by macaholic on 2007-11-25
> **cookies said:**
> First off, I don't think Kubuntu comes with Compiz Fusion..., some one back me up here.
Really? I though it was in the repositories, just not installed/enabled by default.

---

### Post by FuturePilot on 2007-11-25
Yes, Kubuntu does not have Compiz installed by default. It is in the repos though.

---

### Post by skyjacker on 2007-11-25
> **cookies said:**
> First off, I don't think Kubuntu comes with Compiz Fusion..., some one back me up here.

And, as for slowdowns, I haven't the clue, but you could try

sudo apt-get remove strigiIf kubuntu does come with Compiz Fusion, I didn't get it with my "clean install" of Gutsy.

---

### Post by webmiester on 2007-11-26
ok, il go try your suggestions :)

How do I change my kubuntu into xubuntu using apt-get?

---

### Post by kpkeerthi on 2007-11-26
You can install using 
```

sudo aptitude install xubuntu-desktop

```

To use Xubuntu after you've installed it:
Log out.
Under Session, select Xfce.
Log back in again. 

But I would suggest you do a clean install using xubuntu Live CD.

---

### Post by webmiester on 2007-11-26
The strangest thing happened...

I couldnt remove stringi via apt-get, it keeps giving me the "package not found" error... so I uninstalled it using adept...then...

The computer workingst like rocketfire!  Great I solved the problem :)

Only that the Pidgim buddy list wouldnt show.  And everytime I load Pidgim, it doesnt work.  But I got a YM message through Pidgim while I was waiting, so it meant I was also YM online... very strange!

So I rebooted my system... and it became really slow again :( :( :( huhuhu

I dont understand it at all!

Ill ty the xubuntu suggestion this time.

---

### Post by webmiester on 2007-11-29
OK guys,

Ive installed Xubuntu and it still slows down every 2-5 seconds.  When I dont understand was that even on Kubuntu it worked very well for a time after I uninstalled Strigi via adept.

Pidgim wouldnt load properly but the entire system worked really fast.  After I rebooted... the system went back to its slow state :(

The only applications opened at that time were Pidgim Messenger, and Skype Beta (which wasnt logged on).  This is really aweful...

---

### Post by limac on 2007-11-29
first off what's your ram capacity? what about ur processor. My computer was also slowed down due to have a weak ram and a processor, I replaced them with fresh and better ones (2 gb ram, 1.6 ghz intel processor) and my computer ran faster than ever. If it is not due to the hardware, probably you are running something high-end in your computer. And was your computer slower from the time you installed kubuntu? 

If it still doesn't work try the xfce desktop environment (xubuntu), should help you...

---

### Post by limac on 2007-11-29
on second thought how was feisty running for you, if fast do you think your computer got slower because of upgrading to ubuntu instead of installing it form the internet freshly. because that may happen...

---

### Post by webmiester on 2007-12-03
Hi guys,

yes,  My hardware isnt top notched with a 750Mgh PIII and 256Mb RAM, but Fiesty was operating on it with ease.

Ive reinstalled ubuntu from scratch, this time using the Gnome desktop.  It now runs like new :)  Thanks so much!

It was really the upgrade via adept that messed it up.

---

