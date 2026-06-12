---
title: "Edgy Live CD problems"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by Astral Abraxas on 2007-02-28
I managed to install Ubuntu Dapper using safe graphics mode. Now I went and downloaded a live CD of Ubuntu Edgy and the safe graphics mode does not work nor any other method I tried.

After getting the screen about "Cannot display this video mode. Optimim Resolution 1280x1024" I tried using F4 and picking different vga's. This made that screen no longer appear, and at first seems tow work, but once it loads up, the screen is scrambled quite badly. To the point I can't recognize what I am doing but I can see myself highlighting windows and using the application button when randomly using the mouse.

Anyways... I was wondering how I could go about fixing this problem?

---

### Post by firefly2442 on 2007-02-28
Can you give some more details on your computer?  Laptop/Desktop?  System specifications, etc.

I can't remember if you can install via text mode in the desktop ISO.  You might want to try using the "alternative" ISO.  This allows you to install the same Ubuntu version but it does it in text mode which might go easier on your monitor.  Maybe someone else might have more ideas as to why the video mode doesn't work or where you can check for errors.  Hope this helps.  Good luck. :)

---

### Post by Quillz on 2007-02-28
Don't even bother with the 6.10 Live CD. It's never worked for me or for many others. Assuming you have 6.06, just upgrade to 6.10 via Software Updates. It's slower, but at least it works.

---

### Post by timjayko on 2007-02-28
yah i agree with last poster.. edgy live cd didnt work but upgrading in dapper works

---

### Post by Astral Abraxas on 2007-02-28
heh, thats what I am currently doing ^_^. at 80% at the moment >.>; *sigh* and after I erased my dapper dvd x.x... oh well.

Intel(R) Pentium(R) D CPU 2.80GHz

Umm... not sure what else you would want to know =P.

---

### Post by m2project on 2007-02-28
I essentially am having the same problem at the moment, as per my other post below (or above, depending where it is) entitled " newb CD/install, Radeon x1600, Acer AL1916W, major headaches -m2project ". I'll copy it here for reference.

============

Hey guys. What at first seemed so simple has been driving me nuts for four hours so I figured its time to call for help from someone whose brain works :P I could figure everything else out if I could SEE the ubuntu desktop! I'm new to linux but I'm not stupid. My commodore 64 works just fine.

My display scrambles, I think it must be in 640x100000000000000000 resolution or something! It worked once after I set my refresh rate to 60hz (instead of 70 or 75) but I guess that was a fluke. Reset after reset, cold boot after cold boot and I can't access anything, it freezes when i press ctrl alt f1 too.

I am now downloading ubunto-6.06-dvd-amd64.iso but honestly don't even know if this is the best file I could be using. Here's what I'm working with basically

Intel Pentium(R)D CPU 2.80 GHz, 1.00 GB of RAM, Radeon x1600, Acer AL1916W flatscreen (which I believe is what is causing the problem on its plug and play default driver but I am not certain what to do about it).

This is a store bought HP media center edition with windows XP machine all I've put into it is a 3d card. I've browsed about an hour for problems similar to mine but didn't drum up anything helpful. Please help, I'll worship you forever.

============

---

### Post by m2project on 2007-02-28
How are things turning out Astral? I'm still waiting on my download.

---

### Post by Astral Abraxas on 2007-02-28
IT WORKED! hallelujah!

although, it got ugly for a moment. when it booted up all my windows had no bars, so they were like locked into place and I couldn't close them. So I started up terminal, reconfigured xserver-xorg to my nvidia drivers... restarted xserver which didn't do much, so I logged out and chose session to be GNOME. Still didn't do much, so I rebooted and now it seems to be working o.0

---

### Post by m2project on 2007-02-28
I'll have to rub my  genie lamp as usual. I would have thought magic and miracles on installation would be microsoft's dominion. Cross your fingers for me and i hope I'll be joining you soon.

---

