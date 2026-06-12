---
title: "Firefox and Flash"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Ciwan on 2008-01-25
Hi guys

I'm a total newbie to Ubuntu, so small clear steps would be much appreciated.

I'm trying to watch videos on youtube. but I need to have Flash Player installed. I clicked on the Install Plugins and Firefox automatically installed the Flash Player.

But again you tube says "get flash player" in order to play the video !! and that Install Plugins button appears again !!!

I click on it again, and it says Flash is allready installed !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Someone please Help :(

Thanks

---

### Post by LaRoza on 2008-01-25
Search the forum.

If flash was correctly installed, restart firefox. If that doesn't work, find the .deb of Flash and uninstall flash then install from the .deb.

---

### Post by coolbrook on 2008-01-25
I normally advise to go directly to Adobe and [download the flash player](http://www.adobe.com/go/getflashplayer), install it through terminal and close Firefox before or when prompted during installation.  Works like a charm.

---

### Post by Ciwan on 2008-01-25
Which Option do I choose ?? there are 3 !!!!

How do I install it through the Terminal !!!

I'm a newbie ! :(

---

### Post by stchman on 2008-01-25
> **Ciwan said:**
> How do I install it through the Terminal !!!

I'm a newbie ! :(

In a terminal type:

```
sudo apt-get -y install flashplugin-nonfree
```

This should work.

---

### Post by Ciwan on 2008-01-25
Hi Stchman

I did that, and it didn't work !!!

here is what I get instead of the Video in Youtube


[[ Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player. ]]

:( :(

---

### Post by RayDeCampo on 2008-01-25
This issue has been extensively discussed in the following thread:
[http://ubuntuforums.org/showthread.php?p=3923465](http://ubuntuforums.org/showthread.php?p=3923465)

I suggest you look there before installing anything.

---

### Post by Ciwan on 2008-01-25
OK RayDeCampo Thanks

I'll have a read there and get back to you guys

Cheers

---

### Post by Ciwan on 2008-01-25
Wow thanks RayDeCampo

I installed the Package thing, and now I can watch youtube videos, which means Flash has been installed successfully :)

Thanks for all your help guys :D

---

### Post by coolbrook on 2008-01-25
No problem.  At the top of this thread, go to **Thread Tools** and mark this thread as 'Solved'.

---

### Post by LaRoza on 2008-01-25
> **Ciwan said:**
> Wow thanks RayDeCampo

I installed the Package thing, and now I can watch youtube videos, which means Flash has been installed successfully :)


In case you didn't understand my post, a ".deb" is a Debian installer. I realize I wasn't very explicit, but that is because I see this issue many times a day.

---

### Post by stchman on 2008-01-25
> **Ciwan said:**
> Hi Stchman

I did that, and it didn't work !!!

here is what I get instead of the Video in Youtube


[[ Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player. ]]

:( :(

Try this, you need to remove any trace of the old flash plugin.

[http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

Hope this helps.

---

