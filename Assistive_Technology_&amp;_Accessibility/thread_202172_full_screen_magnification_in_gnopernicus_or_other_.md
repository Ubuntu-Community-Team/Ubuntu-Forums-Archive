---
title: "full screen magnification in gnopernicus or other magnifier?"
date: 2006-06-23
forum: Assistive Technology &amp; Accessibility
---

### Post by yellowband on 2006-06-23
Hi

The biggest reason i havn't fully switched over to linux yet is that i need a screen magnifier for most of my computer tasks.  Its unfortunate that gnopernicus looks so terrible by default. Its kind of a catch22 in that i need scrren magnification to see the screen to configure proper full screen magnification.  Has anybody else gotten full screen magnification working yet?  

better yet, are there any other known screen magnifiers that just work prooperly by default?  i am surprised that this is so hard to accomplish.  I have had a smooth screen magnifier in windows for over a decade now with zoomtext,where fullscrren magnification is no problem.  

I found a guide and i ahve some free time this weekend so if i figure how to get gnopernicus to work decently, i'll post my experience.  

thanks for any addition help, if anybody else feels like giving it a try.

---

### Post by linbetwin on 2006-06-23
I don't use full-screen magnification, but there is a guide in the Ubuntu Wiki that shows how to set that up.

Anyway, I think gnopernicus/gnome-mag is dead. It's a resource hog, it locks up all the time and displays crappy magnification. Everybody is waiting for the new compiz-mag. I hope this project won't be abandoned in the middle of the road too.

Does anybody know how this project is progressing? When can we expect an alpha or beta? Or is it already available?

---

### Post by yellowband on 2006-06-23
oh wow, that sucks that gnopernicus is not being worked on any longer. In its current state, the magnifier really isn't usable.   That new project looks interesting. I am also curious as to when there will be a usable version.  I would be willing to try the beta even. 

What are you using for screen magnification right now linbetwin, seeing as you dislike gnopernicus as much as i do.?

---

### Post by linbetwin on 2006-06-24
[quote=yellowband]What are you using for screen magnification right now linbetwin, seeing as you dislike gnopernicus as much as i do.?[/quote]

I use Windows XP and the simple magnifier included. It hasn't changed at all since Windows 98SE and it's the same in Vista beta 2, but it just works. No funky features, no excess of configuration options, no lockups, 3,5 MB of RAM consumption, easy on the CPU too, pointer and cursor tracking. docking, smooth rendering... and that's about it. I tried the ZoomText trial, but I don't need 90 % of its features and I can't afford it.

During the Dapper development I suggested on the accessibility mailing list that the default configuration of gnome-mag be changed (8x magnification and placement in the lower third of the screen). It was done like this for a while, but then somebody decided to place the magnification window elsewhere and they have managed to completely hide the menu box. They couldn't have hid it better if they tried! Novice users won't even know there's a menu box from which you can change settings. Who will tell them they have to press ALT+F2 and then ALT+F3 to open a configuration dialog that can't be seen?

I also ranted on the mailing list about the fact that nobody in the Linux world seems to care or know anything about accessibility. Daniel Holbach scolded me and avdised me to file bug reports. So I did (see bugs [36008]("https://launchpad.net/distros/ubuntu/+source/gnome-mag/+bug/36008") and [36013]("https://launchpad.net/distros/ubuntu/+source/firefox/+bug/36013")), but did anybody do anything about them? Ubuntu likes to stress its commitment to accessibility, but so far it is no more accessible than any other "major" distribution. There has been a lot a work put into making the LiveCD accessible, but let me tell you something: I can find a friend or relative to help me install Ubuntu - it only takes 30 minutes or so - but I can't use Ubuntu if gnome-mag locks up all the time and can't track keyboard editing.

---

### Post by yellowband on 2006-06-25
As a new linux user I'm shocked that accessability (at least as far as screen magnification goes) is so scattered.  Windows has had a screen magnifier that works very well for at least a decade (zoomtext).  I'm not knocking linux again as a windows user.  i want to commit to linux, learn it well and switch over completely but not being able to read what's on the screen is a pretty big drawback.  I can't believe that here aren't any other users like me out there and thatscreen magnification is so undeveleoped.  

What would you suggest is teh best way to get involved and contribute?  Where are these maling lists and who do i need to email to raise such issues.  Who do i contact to get on some beta testing lsts?  Where can i find some resourses on screen magnification development?  This is one thing that frustrates me in linux right now. i am finding it hard to locate the information and development project that are essential to me.

---

### Post by jasongrieves on 2006-06-30
hi,

I have a big review/guide I am working on for the full screen magnifier for gnome-mag.  Was I talking to you through email about this?  I have the full screen working very well in Ubuntu.  Do you have this document yet?  Do you want to work with me on this.

This might be of interest to you
xmcm.sourceforge.net

a project a good number of us are working on.  Interested?

---

### Post by yellowband on 2006-07-12
hey jason,
did you get the email i sent you a while ago?  I'm definately interested in both compiz-mag and xmcm.  And in getting involved in general.  I have ubuntu as my fulltime OS now, but its getting hard on the eyes wihtout any software magnification.  

I tried installing xgl/compiz on my laptop (in anticipation for compiz-mag to be finished soon) but getting that going was hellish.  I refverted back to my mesa drivers for the time being.  

What is this xmcm exactly?  does it work to the point where full screen magnification could be used on a regular basis for most purposes? if so, i can probably bring my laptop to my school and have a nerd help me get it going.  

keep me posted, preferably at [email]minofifa@gmail.com[/email].

---

### Post by jr.gotti on 2006-07-12
Excuse me if I sound stupid...but what about the "Zoom" feature in XGL/Compiz?

Works perfectly as screen magnification...

---

### Post by Henrik on 2006-07-12
It's a good start, but the Zoom feature doesn't let you work with the desktop while it's zoomed and it doesn't read desktop info from the AT-SPI framework. (magnification for low-vision is more than just Zoom). 

We have been working on it for a few months though, see: [https://wiki.ubuntu.com/Accessibility/Specs/compiz-mag](https://wiki.ubuntu.com/Accessibility/Specs/compiz-mag)

If you know compiz well, feel free to help out :)

---

### Post by jasongrieves on 2006-07-12
> **pixelPOET said:**
> Excuse me if I sound stupid...but what about the "Zoom" feature in XGL/Compiz?

Works perfectly as screen magnification...

Like Henrik said its a good start, but its not usable for the Desktop.  There is a great need for a full screen magnifier similiar to Zoomtext.  There is a  trial run of Zoomtext for Windows if you want to compare the zoom to a really full fledged magnifier.  Zoomtext has come a long way, and we have a lot of catching up to do :)

---

### Post by musther on 2006-07-12
There is a simple magnification thingy built into the X windows system, not quite sure if it's supposed to be a screen magnifier or what, I suppose it is, but it's very quick and easy to use.

Funally the problems, it doesn't seem to follow the cursor, just the mouse, but there may be some settings to change somewhere.

Anyway, all you have to do is hit Control-Alt-Numberpad Plus together, hit it again to zoom in further, after it zooms to it's maximum it will pop back out to normal size, or you can use Control-Alt-Numberpad Minus to zoom out.

Just remember that it must be numberpad plus and minus.

Hope this is helpful.

---

### Post by txkcraig on 2006-07-13
If you are interested in a Windows screen magnifier similar (though not quite as good) to Zoomtext, try the freeware version of iZoom.  The company is (i)ssist.  [http://http://www.issist.com/index.asp?page=iZoom]("http://http://www.issist.com/index.asp?page=iZoom")

---

### Post by yellowband on 2006-07-15
> **musther said:**
> There is a simple magnification thingy built into the X windows system, not quite sure if it's supposed to be a screen magnifier or what, I suppose it is, but it's very quick and easy to use.

Funally the problems, it doesn't seem to follow the cursor, just the mouse, but there may be some settings to change somewhere.

Anyway, all you have to do is hit Control-Alt-Numberpad Plus together, hit it again to zoom in further, after it zooms to it's maximum it will pop back out to normal size, or you can use Control-Alt-Numberpad Minus to zoom out.

Just remember that it must be numberpad plus and minus.

Hope this is helpful.


hey cool find! Unfortunately, it is not working on my computer.  the screen goes black and then comes back on. I cAn tell that it has magnified things, but it looks all streaky and completely unreadable.  Anybody know what the problem could be?  i'm using the default mesa project drivvers for my ATI radeon 300 mobile card, because the ATI driver is being a pain.

---

### Post by cerdiogenes on 2006-07-26
Hi people,

I'm one of the gnome-mag developers and I'm currently working in full screen support using the COMPOSITE extension. Something similar in what is being done in compiz-mag and xmcm.

We achieve a very good performance compared to gnome-mag (without composite) and xmcm performance.

These changes are not yet in CVS, but if someone wants to try it (have any development experience) patchs to make it's works can be found in [http://bugzilla.gnome.org/show_bug.cgi?id=348375](http://bugzilla.gnome.org/show_bug.cgi?id=348375)

This works better with X11R7.1, what is not shipped with the majority of the distributions, but it must work also with X11R7.0. How I have already talked, this is not working perfectly, but if someones want to see it or help with it, I'm leaving the path.

Best regards,
Carlos.

---

### Post by Cabb on 2006-07-27
Hi,
I'm glad I found this forum thread! I'm also one of those wanting to switch to Linux, but haven't got full-screen magnification to work and therefore a switch for me is inpossible. I can use the OS at low resolutions if I hold a magnifying glass up to the screen, so I can (try to) get things working. In Windows I use Zoomtext, at a magnification at 3x, and at 800x600 screen resolution. I also frequently use the invert colors feature.
For the Linux part I've been following this guide: [http://accessibility.freestandards.org/a11yweb/presentations/kraft-20050126-mag.html](http://accessibility.freestandards.org/a11yweb/presentations/kraft-20050126-mag.html)
I tried the first procedure, and it worked quite fine, allthough I couldn't get to the magnification level I needed, and the low resolution made things look a bit bad. Also I tried playing around with the themes (background colors etc.)
I can get a nice black background, and using white text then makes it much easier for me to see. But the problem is that in some applications I saw the background change, but not the text, and therefore I had black text on a black backgroud, or something like that anyway.

I'm really glad to hear there are people working on this, cause when I first started googling for this topic I couldn't find much info. The things I found were scattered all over the place.

-Daniel

---

### Post by cerdiogenes on 2006-07-27
I just installed Ubuntu 6.06 here today and noted that when I start gnome-mag with composite support or xmcm some of the panels properties change and the applications are not more aware of they, since if an application is maximized the panels are totally hidden. It's also occurs with others users here?

Thanks,
Carlos.

---

### Post by jasongrieves on 2006-07-27
> **cerdiogenes said:**
> I just installed Ubuntu 6.06 here today and noted that when I start gnome-mag with composite support or xmcm some of the panels properties change and the applications are not more aware of they, since if an application is maximized the panels are totally hidden. It's also occurs with others users here?

Thanks,
Carlos.
at least with XMCM i suspect this is due to the magnifeid window being placed on top of the root window.  In other words gnome-panels have the property of being always on top but because we take the entire screen for fullscreen magnification, we go ontop of even those panels.  After using the magnifier I have seen the panels no longer retain their "always on top"

you should be able to run "sudo killall gnome-panel" and that will effectively restart the gnome-panel.  I am not sure what this will do while  in full screen magnification mode.

---

### Post by cerdiogenes on 2006-07-27
> **jasongrieves said:**
> at least with XMCM i suspect this is due to the magnifeid window being placed on top of the root window.  In other words gnome-panels have the property of being always on top but because we take the entire screen for fullscreen magnification, we go ontop of even those panels.  After using the magnifier I have seen the panels no longer retain their "always on top"

you should be able to run "sudo killall gnome-panel" and that will effectively restart the gnome-panel.  I am not sure what this will do while  in full screen magnification mode.

Ow, this makes sense, since the panels are windows "always on top" when COMPOSITE is enabled they lost this property. I was thinking why this does not happen with X11R7.1 and now I realize that this may be due the Overlay window that was added to COMPOSITE (to resolve, including, this issue).

Best regards,
Carlos.

---

### Post by Cabb on 2006-07-28
So at this stage is there any solution that would work reasonably well to use for someone like me who has to use magnification all the time?

---

### Post by jasongrieves on 2006-07-28
hi,

[https://wiki.ubuntu.com/Accessibility/Reviews/gnome-mag](https://wiki.ubuntu.com/Accessibility/Reviews/gnome-mag)

My friend is a power user of Zoomtext and now uses full screen magnification with this.  Says it works out very well.  I got him setup with it and he is very satisfied....contact me with questions/comments!

---

### Post by Cabb on 2006-07-31
Hi again,
Such a review of yours is just what I've been missing, great job!
In fact I have a new experience to post today :)
I decided to try this out on VMWare, and I got it working! I had more trouble getting the system to work in general than I had setting up the magnification, but now everything works quite good. Performance is very bad of course using this in VMWare, but the fact that I indeed got it working at all was a little surprising.
While editing xorg.conf and such I used ZoomText, which worked quite nicely, except that mouse tracking was a bit inaccurate.

This is just awesome!

---

### Post by jasongrieves on 2006-07-31
> **Cabb said:**
> Hi again,
Such a review of yours is just what I've been missing, great job!
In fact I have a new experience to post today :)
I decided to try this out on VMWare, and I got it working! I had more trouble getting the system to work in general than I had setting up the magnification, but now everything works quite good. Performance is very bad of course using this in VMWare, but the fact that I indeed got it working at all was a little surprising.
While editing xorg.conf and such I used ZoomText, which worked quite nicely, except that mouse tracking was a bit inaccurate.

This is just awesome!

good to hear!  Did you have any problems with the guide?  Any trouble spots or glitches in the writing?  Eventually I wan to try to write a script to emulate the required steps.  Just not sure when I will get around to it.

Thanks for the comments

---

