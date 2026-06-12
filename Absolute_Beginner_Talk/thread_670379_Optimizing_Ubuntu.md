---
title: "Optimizing Ubuntu?"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by skaldicpoet9 on 2008-01-17
I recently just got back from the computer lab on campus. While I was there I noticed that running apps (especially Firefox) were much faster on the kernel that the campus is using. I have noticed that Ubuntu is running much slower then it should, I used to have Ubuntu running on my desktop (which has all the same specs except for RAM which this laptop has 1gb more of) and I had no problems with it. Now I have Ubuntu on my laptop and 1) when I boot Ubuntu it takes a really long time to actually get me to the login screen 2) when using apps there is a slight, but noticeable delay between the time I click on the app and the time it opens and 3) there is a slight bit of lag when scrolling through web pages on Firefox. Due to my time on the desktop I know that this is not normal. I am somewhat under the impression that it may be due to my ATI drivers, of which i have heard that there are some issues using ATI drivers on Linux. Anyways, I was wondering if there was anyway that I can possibly do to fix this problem? 

btw my laptop's specs are:

Gateway MX6429
1.8 GHz AMD Turion 64 Mobile Technology ML-32
ATI Radeon Xpress 200M
1.4gb of RAM

---

### Post by dstew on 2008-01-17
It is possible that your campus computers are running a slimmed-down custom kernel, which might indeed be faster than that used by Ubuntu. Do you know anything about the kernel?

---

### Post by skaldicpoet9 on 2008-01-17
Yes, this is entirely possible and but the thing is I have already had Ubuntu installed on my desktop that has all the same specs (except for the RAM was 1gb less then this laptop) and there was no discernible difference between Ubuntu and running XP. However, I now have Ubuntu installed on this laptop so I would assume it would run at least the same as the desktop, right? But it doesn't. I really think it might be this ATI driver, sometimes when I click on a tab or navigate through webpages I see screen tearing...on my desktop I was using the video driver that came with Ubuntu.

---

### Post by skaldicpoet9 on 2008-01-17
Someone please help! I love Ubuntu! It doesn't deserve to run like this :(

---

### Post by skaldicpoet9 on 2008-01-17
Does anyone think it might help to disable my ATI driver and then re-enable the video driver that came with Ubuntu?

---

### Post by mike555 on 2008-01-17
Laptops most often have slower harddrives and slower processors to try to keep heat down ,  it might also be a graphics thing (ATI)   .

---

### Post by xxrealmsxx on 2008-01-17
> **skaldicpoet9 said:**
> I recently just got back from the computer lab on campus. While I was there I noticed that running apps (especially Firefox) were much faster on the kernel that the campus is using. I have noticed that Ubuntu is running much slower then it should, I used to have Ubuntu running on my desktop (which has all the same specs except for RAM which this laptop has 1gb more of) and I had no problems with it. Now I have Ubuntu on my laptop and 1) when I boot Ubuntu it takes a really long time to actually get me to the login screen 2) when using apps there is a slight, but noticeable delay between the time I click on the app and the time it opens and 3) there is a slight bit of lag when scrolling through web pages on Firefox. Due to my time on the desktop I know that this is not normal. I am somewhat under the impression that it may be due to my ATI drivers, of which i have heard that there are some issues using ATI drivers on Linux. Anyways, I was wondering if there was anyway that I can possibly do to fix this problem? 

btw my laptop's specs are:

Gateway MX6429
1.8 GHz AMD Turion 64 Mobile Technology ML-32
ATI Radeon Xpress 200M
1.4gb of RAM

The long boot time is a hardware issue that a lot of laptop owners are suffering from under ubuntu.

As for the crap performance, I feel the same about my zv6000 but I blame it on XGL and our video driver. I have 2 gigs of ram and XP runs a lot faster than ubuntu.

---

### Post by ugm6hr on 2008-01-17
> **xxrealmsxx said:**
> The long boot time is a hardware issue that a lot of laptop owners are suffering from under ubuntu.
Do you see a splash screen before you get to the login screen?  When you say a long time - are we talking 2minutes+?  If the answers are no and yes, then this might help:
[http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075) (see post 2)

> As for the crap performance, I feel the same about my zv6000 but I blame it on XGL and our video driver.
I would recommend using the latest ATI driver (if compatible), and uninstalling xgl - see the entry about 3D effects here:
[http://ubuntuforums.org/showpost.php?p=3950616&postcount=3](http://ubuntuforums.org/showpost.php?p=3950616&postcount=3)

---

### Post by skaldicpoet9 on 2008-01-17
Hey, thanks for the help ugm6hr :)

That fixed the long boot time. 

However, I already have the latest ATI drivers and my apps still lag a bit. And some games like Open Arena and Armagetron have a slight flickering effect while I play them. Is there any way for me to fix this?

---

### Post by ugm6hr on 2008-01-18
> **skaldicpoet9 said:**
> However, I already have the latest ATI drivers and my apps still lag a bit. And some games like Open Arena and Armagetron have a slight flickering effect while I play them. Is there any way for me to fix this?

Afraid I don't know.  I don't play games.  But...

Have you uninstalled xserver-xgl?
Do you have Compiz on?  If so, you might need to do follow this: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#3D_desktop_effects](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#3D_desktop_effects)

And does the ATI Catalyst Control Centre work OK?

Have you tried turning Compiz off when playing games?  This will show you the effect:
```
glxgears
```
Returns a fps (frames per second) - mine is about 7-900fps with Compiz on, and 1600fps with it off.  Presumably, games require a reasonable fps to play without flickering.  Proper gaming video cards seem to manage 3000+ fps.

If those don't work, I'm afraid I don't know.

---

### Post by xxrealmsxx on 2008-01-18
> **ugm6hr said:**
> Do you see a splash screen before you get to the login screen?  When you say a long time - are we talking 2minutes+?  If the answers are no and yes, then this might help:
[http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075) (see post 2)


I would recommend using the latest ATI driver (if compatible), and uninstalling xgl - see the entry about 3D effects here:
[http://ubuntuforums.org/showpost.php?p=3950616&postcount=3](http://ubuntuforums.org/showpost.php?p=3950616&postcount=3)

Your first solution worked. I uninstaller XGL and just turned off desktop effects since the performance hit wasn't worth the eye candy and my video card does not have composite support as of yet.

Thanks for the assistance though.

Now my only issue is getting hibernate/standby to work :).

---

### Post by jingo811 on 2008-02-19
> **ugm6hr said:**
> Afraid I don't know.  I don't play games.  But...

Have you uninstalled xserver-xgl?
Do you have Compiz on?  If so, you might need to do follow this: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#3D_desktop_effects](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#3D_desktop_effects)

And does the ATI Catalyst Control Centre work OK?

Have you tried turning Compiz off when playing games?  This will show you the effect:
```
glxgears
```
Returns a fps (frames per second) - mine is about 7-900fps with Compiz on, and 1600fps with it off.  Presumably, games require a reasonable fps to play without flickering.  Proper gaming video cards seem to manage 3000+ fps.

If those don't work, I'm afraid I don't know.


The gamers thread moderator AI once told me this or implied to be exact :)

**aiglx** = for Compiz-Fusion
**fglrx** = for gaming
> **Artificial Intelligence said:**
> As far as I understand one of the driver you need to do the compiz stuff the other one is good for gaming, so you have to pick.

(or get a nvidia card).
[http://ubuntuforums.org/showthread.php?t=442752&page=2](http://ubuntuforums.org/showthread.php?t=442752&page=2)

---

### Post by sailor2001 on 2008-02-19
also is your ipv6 turned off?  In browser address:  about:config   filter search ipv6...double click line to change false to true.. Also do a forum search on "quiet ro"

---

