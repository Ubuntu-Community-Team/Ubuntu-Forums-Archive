---
title: "Ubuntu or Studio?"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by Fish Finger on 2008-04-06
Hullo!

I've been playing around with a Live CD for a while, and I've decided that I definitely wish to install and start using Ubuntu. I was looking around websites for bits that I can install for more media-targeted things (eg Video production, Sound editing etc etc). Then I found Ubuntu Studio. 

Basically, my question is: Should I (bearing in mind I have no idea about Linux beyond a Live CD)...

a) Install regular Ubuntu, then gather all the separate programs which I need
b) Install Ubuntu Studio (which looks scary, Wikipedia says it has no graphical installer - does that mean I need to know all the codey stuff?)
3) Install regular Ubuntu, get used to it, then install Ubuntu Studio? 

And also, does Studio still do all the same basic things like normal Ubuntu?

And is there a minimum spec which Studio requires?

These probably seem like stupid questions, but I have absolutely no knowledge about Linux beyond using a Live CD. 

Thanks in advance,
Fish Finger :)

---

### Post by atomkarinca on 2008-04-06
If you're afraid that there is no graphical installer then install Ubuntu and you can install Ubuntu Studio from command-line. The major difference between Ubuntu and Ubuntu Studio is the realtime kernel, I guess. Jack works without a glitch with the rt kernel. I'm using Xubuntu Studio by the way :)

---

### Post by wolfen69 on 2008-04-06
no graphical installer shouldnt be a problem. it's basically the same as the regular installer, just not as pretty. if you are going to use the whole disk for ubuntu, it will not be a problem. during install just choose- "guided-use entire disk".

---

### Post by Fish Finger on 2008-04-06
Ahh excellent, thanks guys.

Can you use Studio in the same way as regular then? Eg would there be a big learning curve in the user interface once installed?

Thanks again :D

---

### Post by Mazza558 on 2008-04-06
> **Fish Finger said:**
> Ahh excellent, thanks guys.

Can you use Studio in the same way as regular then? Eg would there be a big learning curve in the user interface once installed?

Thanks again :D

As far as I know, Studio is just Ubuntu with a different theme (and editing apps installed), so it should be just as easy to use.

---

### Post by atomkarinca on 2008-04-06
Ubuntu Studio = Ubuntu + rt kernel + lots of great applications + cool theme-icons-wallpaper-splash and whatnot. You'll love it.

---

### Post by ShodanjoDM on 2008-04-06
Been using Ubuntu Studio since the first version (7.04). What do I like the most is that there is a choice to just install the "basic" desktop with minimal additional softwares (there's only OpenOffice Writer - instead of the complete OpenOffice.org packages, no default mail client installed, etc).  I like this since I can customize my system with more control.

Or you can go "all out" and install the graphic, audio or video or even the whole multimedia softwares included in the dvd.

---

### Post by Dingo Dave on 2008-04-06
> **atomkarinca said:**
> If you're afraid that there is no graphical installer then install Ubuntu and you can install Ubuntu Studio from command-line. The major difference between Ubuntu and Ubuntu Studio is the realtime kernel, I guess. Jack works without a glitch with the rt kernel. I'm using Xubuntu Studio by the way :)

I use Ubuntu and want to "upgrade" to Studio. What code should I write in Terminal to do this? Is is just a few lines and the computer do the rest?

Thanks!

---

### Post by ShodanjoDM on 2008-04-06
For the basic packages (desktop themes, icons, sounds etc):
```
sudo aptitude install ubuntustudio-desktop
```

For graphic softwares:
```
sudo aptitude install ubuntustudio-graphics
```

Video:
```
sudo aptitude install ubuntustudio-video
```

Audio:
```
sudo aptitude install ubuntustudio-audio ubuntustudio-audio-plugins
```

---

### Post by billgoldberg on 2008-04-06
> **Dingo Dave said:**
> I use Ubuntu and want to "upgrade" to Studio. What code should I write in Terminal to do this? Is is just a few lines and the computer do the rest?

Thanks!

According to [this website]("http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/") it's as easy as opening a terminal in ubuntu and copy/pasting this:

```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

---

### Post by Fish Finger on 2008-04-06
Wonderful! Thanks guys! I'm actually really looking forward to finally using it!

Thanks again,
Fish Finger

---

### Post by Dingo Dave on 2008-04-06
> **billgoldberg said:**
> According to [this website]("http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/") it's as easy as opening a terminal in ubuntu and copy/pasting this:

```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

I have just done like this and it went perfectly! No problems at all! The whole thing, including downloading all files, took about 30 minutes.

Thank you so much!

---

### Post by scooterpd on 2008-04-23
so is it safe to say that ubuntustudio has all of the default apps that come with ubuntu, plus more video/graphic/audio editing apps?  Basically, will i _**miss**_ anything by going with studio as opposed to standard ubuntu?

thanks

---

### Post by ShodanjoDM on 2008-04-23
> **scooterpd said:**
> so is it safe to say that ubuntustudio has all of the default apps that come with ubuntu, plus more video/graphic/audio editing apps?  Basically, will i _**miss**_ anything by going with studio as opposed to standard ubuntu?

thanks

No. If you install from DVD, it doesnt has a complete OpenOffice suite (just OO-writer), no Evolution mail and no games - among some other differences/omitted packages. Ofcourse you can always install them later as usual.

---

### Post by MetalMusicAddict on 2008-04-24
A clean install will not come with any OO.o components. It's missing mostly apps related to "desktop" systems.

Ubuntu Studio is geared towards multimedia production machines. If it's more a "desktop" app, it was dropped.

---

### Post by scooterpd on 2008-04-25
question:  How do i get the rt kernel and editing apps of ubuntustudio, while at the same time keeping the "taskbar"(the panel at the top of the screen by default) of ubuntu standard as is?  Basically, the only thing i dont like about studio is that on this top panel, it only has the studio icon.  It does not have the "Applications", "Places", and "System" drop-down menus like default ubuntu.  How do i get that in studio?

thank a lot for all of your help.  Ubuntu forum members are the best forum members i know.

peace out.

---

### Post by drsaamah on 2008-04-26
I would suggest installing regular ubuntu and THEN installing the ubuntu studio applications as explained above... BUT if you don't want to reinstall an OS... open up a terminal and type in
```
sudo apt-get install ubuntu-desktop
```
That should install all the normal ubuntu themes. After that go to System->Preferences->Appearance to select your a non-studio theme.
IF the "System" menu isn't at the top of the screen, then right click on your desktop and select "Change Desktop Background".  Then select the "Theme" tab on top of that window, and select a normal theme.
Let me know if this isn't what you want.  I don't actually have studio, so I don't know all the differences, but I believe this should work.  Peace mate!

---

