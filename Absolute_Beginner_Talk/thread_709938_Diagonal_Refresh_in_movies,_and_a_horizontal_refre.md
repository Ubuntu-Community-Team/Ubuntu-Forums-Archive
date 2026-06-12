---
title: "Diagonal Refresh in movies, and a horizontal refresh in Firefox."
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Duffkiligan on 2008-02-27
I have looked through the forums and google to come to the conclusion that I can't find the answer.

I've found problems similar, but not the same.

Every movie that I watch, or any game that I play has a very annoying horizontal line through it as it refreshes.
Also, firefox, when I scroll down has horizontal refresh bars.


I've tried to find the answer, but can't.

If you need more info on my laptop, I can provide it.


Thank you,
Duff

---

### Post by FuturePilot on 2008-02-27
What graphics card do you have? There might be a driver for it. Check System&#8594;Administration&#8594;Restricted Driver Manager. 
Also are these movies and games Flash based by chance? I've noticed that the latest version of Flash player has a problem with tearing.

---

### Post by Origin415 on 2008-02-27
What kind of video card do you have? If it is an nVidia or ATI card you need to install the proper modules, you can do that easily in System -> Administration -> Restricted Drivers Manager.

Both those companies only provide closed source, proprietary drivers, so they are disabled by default to adhere better to the open source philosophy, instead vesa drivers are used, which as you have noticed, are extremely slow (using software rendering instead of your video card)

Edit: FuturePilot beat me to it :P

---

### Post by Duffkiligan on 2008-02-27
I believe it's some crap, Intel Chipset. 945 I think.

It was a cheap laptop to get me through the day, basically.

It says I don't need any restricted drivers...

---

### Post by ryanhaigh on 2008-02-27
I have a similar issue when watching videos when I have compiz (desktop effects) enabled. I can't run my games with compiz enabled so cannot confirm that. Try disabling compiz and see if the tearing still occurs, there are also options to enable workarounds for video in the advanced effects configuration tool (can't recall the actual name but the command to start it is ccsm)

---

### Post by Duffkiligan on 2008-02-28
How do I disable compiz?

I know I enabled it before, but set my desktop effects off, I thought that would just shut it off...

---

### Post by ryanhaigh on 2008-03-01
Turning off desktop effects should indeed have turned it off. Run the following command in the terminal just to be sure:

```
ps aux | grep compiz 
```

If it is not running you should see no output. 

Also post the contents or attatch a copy of your /etx/X11/xorg.conf file

---

