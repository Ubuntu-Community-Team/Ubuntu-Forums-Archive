---
title: "Pismo -won't boot to cd"
date: 2008-05-14
forum: Apple Hardware Users
---

### Post by wanthh on 2008-05-14
Mac Pismo will not boot to xubuntu 8.04 LiveCD. Hold c key -it boots to OS 9. LiveCD works in another machine (Gateway X200). Thanks for any help

---

### Post by avtolle on 2008-05-14
> **wanthh said:**
> Mac Pismo will not boot to xubuntu 8.04 LiveCD. Hold c key -it boots to OS 9. LiveCD works in another machine (Gateway X200). Thanks for any help
You need the ppc release; the Live CD you have is, I presume, the i386 release, as it boots the Gateway. See the first sticky at the top of the thread for the locations to obtain the PPC version. Good luck.

---

### Post by wanthh on 2008-05-15
Best tip so far, thanks. The Mac Pismo is booting to livecd while holding the c key but now its going to the white screen. Mac has 380Mb RAM memory. Is that enough for Ubuntu 8.04?

---

### Post by avtolle on 2008-05-15
> **wanthh said:**
> Best tip so far, thanks. The Mac Pismo is booting to livecd while holding the c key but now its going to the white screen. Mac has 380Mb RAM memory. Is that enough for Ubuntu 8.04?
That's enough to run it, I believe, but I'd suggest grabbing the alternate install cd if you are planning on installing it anyway. I've more RAM on my Cubes than you do on the Pismo, but I could never get the Live CD to boot "right". Even after installing, there were issues to be resolved by editing the /etc/X11/xorg.conf file, etc. Maybe others have had success with the Live CD on a similar computer who can give you better assistance than I.

You might also want to take a look at: [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ) as it has some information that may be of assistance.

---

### Post by stream303 on 2008-05-15
I forget if the pismo has the 8gb partitioning limitation (make it 7gb to be safe)...

---

### Post by avtolle on 2008-05-15
Forgot about this; when you boot from the Live CD, at the second yaboot prompt (if you got that far), did you try "Live video=ofonly" as an option (without the quotes, of course). That may help.

---

### Post by wanthh on 2008-05-15
Using "live video=ofonly" the Pismo boots until a page of "* starting ---" statements  and [ok]'s. Last line on page is * running local boot scripts (/etc/rc.local) . Blinking line for an entry went away. I have no idea what to do now. Would the alternate CD really be the easier way to do this?

---

### Post by avtolle on 2008-05-15
> **wanthh said:**
> Using "live video=ofonly" the Pismo boots until a page of "* starting ---" statements  and [ok]'s. Last line on page is * running local boot scripts (/etc/rc.local) . Blinking line for an entry went away. I have no idea what to do now. Would the alternate CD really be the easier way to do this?

I had the same problem with the Live CD, when I wanted to see if it would work (had not installed from a Live CD since 5.10). As mentioned earlier, the alternate cd worked for me to get the system installed. I'd d/l the alternate iso, do the md5sum, burn at low speed to a good quality CD-R, and try that. I think it will be a lot easier in the long run.

---

### Post by wanthh on 2008-05-15
Thats what I'm going to do now. You've been a great help. Thanks.

---

### Post by avtolle on 2008-05-15
I'm presuming you want to install xubuntu, as your first post indicated. Looking at the xubuntu site, 8.04 is out in beta, not final. So, I presume further you are doing a ubuntu install instead. I will tell you that I was able to install 8.04 server as a minimal install (skipped the part about what kind of server I wanted, LAMP, etc. during the install) and put the xubuntu desktop package on top of it "just to try it out". It went well as to install, etc., but I found that I had issues with sound that I didn't want to wrestle with, and removed it. Anyway, good luck with the next step.

---

### Post by wanthh on 2008-05-15
The Mac pismo took the alternate install. of Ubuntu 8.04. All ok until final second stage. Removed cd and booted but screen went scattered then faded- no graphical interface. I did want Xubuntu because of 400 MHz processor and 380MB Ram. Xubuntu said to be better on this old machine. I could not find Mac powerpc download for it so I tried Ubuntu 8.04 as suggested. I'm about to go back to OS 9 unless someone knows if Xubuntu (any) will work on the Pismo (firewire) and where to download the image. LiveCD + trial preferred, alternate if not. Thanks if anyone can answer.

---

### Post by stream303 on 2008-05-16
Don't run away just yet - you are close.

Once we get Ubuntu running, if you still want Xubuntu, you can always install it manually by running

```
sudo apt-get install xubuntu-desktop
```

and switching to it at your next login session by specifying xubuntu at the gdm login screen, usually at the lower left.  I don't know why Xubuntu isn't providing a specific Hardy iso, and hope that they aren't going to stop updates for it - this is the kind of stuff xubuntu is made for.

Tip: You may not even need/want a full Xubuntu - from Ubuntu, you could just install the main component, XFCE4, and switch to that at the next login....

Here's a good link on where to download the PPC images:
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

Back to the main problem though.  It appears you might have to manually edit your /etc/X11/xorg.conf file to accomodate the pismo.  I'd have to look back in the archive PPC threads - I'm sure I've seen a few.

That fact that you are seeing dmesg lines scrolling by when you do video=ofonly is a good sign, but it appears that once it reaches the gui desktop, X is misconfigured.  When the screen goes black, can you get to a virtual terminal via CTRL-ALT-F1 ?

As a diagnostic, you could try installing the older Feisty 7.04 and see how that goes, especially when it comes to the /etc/X11/xorg configuration.

---

### Post by Free Hot Porn on 2008-05-16
yea think so 2:guitar:

---

### Post by wanthh on 2008-05-16
Best results yet were with Ubuntu 7.04 FF Live CD. Using "live video=ofonly" will go all the way to a blue screen with message:" Failed to start the x server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem? ". I think it has something to do with the video card but I don't know which it has or how to find out. It does seem as if its close to working but I've reached the limit of my abilities. I can follow directions well but just don't know coding. If anyone can get me past this; please write.

Latest: Tried to reinstall OS 9 but unable since Ubuntu alternate setup method wiped HD. OS 9 is now asking for mounted volumn, needs HD to be destination. I ran the Apple Hardware Test CD - all passed and learned this; The Mac Pismo memory is S0Dimm0/J2 = 64MB and S0Dimm1/J1 = 256MB. Video graphics is an ATI Rage M3pA  res. 1024x768. I now just want to get the machine running; prefer xubuntu or ubuntu and then OS9. I don't know how to make the HD the destination for OS9- no choices.

---

