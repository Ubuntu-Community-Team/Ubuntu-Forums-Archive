---
title: "g4 12&quot; laptop screen brightness and trackpad"
date: 2008-06-11
forum: Apple Hardware Users
---

### Post by ruialexbarbosa on 2008-06-11
Hi,

I just put ubuntu 8.04 on my g4 1.33, 512ram, 12" powerbook.

Screen brightness is not working and I'd like to tap on the trackpad, as well as find a solution for a 2nd button (f12 works, but is not very practical).

Would you help me to sort this?

Thanks

Alex

---

### Post by mchladek on 2008-06-11
> **ruialexbarbosa said:**
> 
Screen brightness is not working

What video card do you have?  You can find out with the following command:

```
lspci | grep VGA
```

> **ruialexbarbosa said:**
> 
I'd like to tap on the trackpad

Do you know if you have a synaptics trackpad?  If so, you can play around with the options in your xorg.conf file.  Otherwise, you have to use the trackpad utility.  Issue these commands on startup:

```

sudo trackpad tap
sudo trackpad drag
sudo trackpad lock

```

> **ruialexbarbosa said:**
> 
find a solution for a 2nd button (f12 works, but is not very practical).


For the 2nd mouse button, I've had success with mouseemu.  Check to make sure it's installed:

```
sudo apt-get install mouseemu
```

You can then edit what key combo emulates the 2nd mouse button by making changes to /etc/default/mouseemu.  I use CMD (Apple Key; keycode 125) + mouse click for the 2nd mouse button.  I've seen tutorials on getting ctrl + click to work for the 2nd button, but it requires editing your keyboard layout (very complicated) and to me CMD + click is close enough.

Once you make changes to /etc/default/mouseemu, make sure to restart mouseemu for them to take effect:

```

sudo /etc/init.d/mouseemu stop
sudo /etc/init.d/mouseemu start

```

---

### Post by ruialexbarbosa on 2008-06-11
Hi,

great info there.

Here it goes:

Trackpad first: sudo trackpad tap , love it, this is what I wanted. How do I make it permanent? Guess I can avoid touching the xog.info file...

Mouseemu is great (ctrl+click, NOT CMD) works out-of the-box, and scroll is fine but it's alt key, can I change it to ctrl?

I don't need the middle button.

About the video card, mine says nVidia Corporation NV34M (GeForce FX Go5200) (rev a1)

Thanks for your help, it is much appreciated.

---

### Post by mchladek on 2008-06-11
> **ruialexbarbosa said:**
> 
Trackpad first: sudo trackpad tap , love it, this is what I wanted. How do I make it permanent? Guess I can avoid touching the xog.info file...

This was actually just brought up in another thread.  Take a look [here](http://ubuntuforums.org/showthread.php?t=488853).

> **ruialexbarbosa said:**
> 
Mouseemu is great (ctrl+click, NOT CMD) works out-of the-box, and scroll is fine but it's alt key, can I change it to ctrl?


You should be able to in theory.  I've never had much luck with the scrolling feature, though.  You'll need to find out what the keycode is for the ctrl button if it isn't in mouseemu's config file.  It's been a while since I've done that, unfortunately, so I don't remember.  Trying searching the forums or Google; something should come up.

> **ruialexbarbosa said:**
> 
About the video card, mine says nVidia Corporation NV34M (GeForce FX Go5200) (rev a1)

Unfortunately, I can't help here.  I had a similar problem that was caused by settings for my ATI video card, which obviously won't be any good to you.

---

### Post by ruialexbarbosa on 2008-06-12
Thanks. I will put another topic on the screen brightness.

---

### Post by usererror on 2008-09-30
Have you gotten your ATI video card brightness keys to work?  ALL my other keys work except the brightness keys...

I got my brightness keys fixed.  Here is the post:  [http://ubuntuforums.org/showthread.php?t=798974](http://ubuntuforums.org/showthread.php?t=798974)

---

### Post by ruialexbarbosa on 2008-10-07
Truth is I uninstalled ubntu from the powerbook. OSX is just fine.

I do use ubuntu on my main pc though, for 2 or 3 years now, and it's just fine.

---

