---
title: "When Everything Goes Terribly Wrong..."
date: 2005-05-15
forum: Absolute Beginner Talk
---

### Post by moon2js on 2005-05-15
I've been using Linux/Ubuntu for a few months now, and I'm wondering if there is any guide for newbies about what do in Ubuntu/Linux when things go wrong. Specifically I'm refering to system freezes. On occasion, the entire system becomes unresponsive and I'm at a bit of a loss as to what to do besides the power button.

Is there anything I can do to safely bring the system around or safely shut it down? I know how to kill the xserver with [ctrl]+[alt]+[backspace], and sometimes I try the [ctrl]+[alt]+[del] from my Windoze days, which seems to reboot the system. And I know that I can switch terminals with [ctrl]+[alt]+[fx] and try to kill the offending program or bring down the system from there.

But if the system doesn't respond to these keystrokes, is there anything else that can be done?

I've heard that some people tend to ssh into an unresponsive system from another computer, and I'm trying to learn how to use ssh, but ssh is not something I will always be able to do in all situations.

Also, what kind of damage are we talking about when a system is shutdown inproperly? In either a system freeze/power button or simply power failure situation (i.e. someone tripped over the cord)?

And how can I assess and repair said damage?

---

### Post by Kimm on 2005-05-15
when the system becomes completely unresponcive there is not realy anything you can do... if you have the ability to see what % your CPU is at (for example in XFCE...), and its on a high level, something like 100% (most definently will be) then try to wait a while, just a couple of minutes to see it things go better. Otherwise if there is no way what so ever to comunicate with the computer i.e. Computer does not respond to keystrokes of klicks with the mouse then there is nothing left but to press the Power Button. As far as I know not much happens when you press the powerbutton and "uncleanly" turn the computer off, but then again I might be wrong and perhaps sometimes things do go wrong, but generaly Linux knows that it was not shut down properly and scans the HDD for you and fixes any errors it might find.

PS.
Another thing you can try is to just tap the power button, as in, not holding it in, just pressing it then letting it go, this should tell Linux (if its still active in any way) to terminate all processes and power down

Edit: ofcourse this also depends on your computer and BIOS

---

### Post by 23meg on 2005-05-15
the most likely form of possible damage from such undesired situations is data loss, and the most obvious and at the same time smartest thing to do has been the traditional one that has existed since the dawn of computing: 

**to make regular backups.** 

no matter how stable your system, how professional you are, how reliable your hardware, the importance of the above line can't be stressed enough. backups give you an absolute chance to recover from even the "worst case scenario". 

another precaution a safety conscious user like you should consider is the use of a UPS unit with a voltage regulator and power surge protection system. you'll also want to make sure your electricity is "clean"; meaning that your power source is properly grounded and multimeter measurements off the mains you plug your computer into matches the voltage and current values that apply to your region (a 4% tolerance is found acceptable by many).

if the system becomes totally unresponsive to anything you mentioned, the best you can practically do is to hold down the power button and shut down the computer, and then restart. make sure that the computer is actually totally "frozen", that the hd isn't performing any write operations, though.

if in spite of the above the worst has happened, and the damage isn't practically recoverable (which is very very unlikely), you'd resort to appropriate data recovery software, or if your budget allows, specialist data recovery services.

---

### Post by moon2js on 2005-05-16
[QUOTE=23meg]
**to make regular backups.** 
[/QUOTE]

I tend to backup manually at least once a month by physically copying pretty much my entire home dir to another computer on my home network. But I'd like to automate this process my computer is an old laptop and I'm a lug it around just about every where and use it for my writing and work, so I sort of figure it's due to breakdown. Ideally I'd like it to just automatically backup/sync whenever I plug it at home so I can have daily/weekly backups.

Today, my system went unresponsive while totem was running. This has happened before -- the screen goes blank, the keyboard is completely unresponsive, and the harddrive just whirls and whirls. But it won't ever come back, I can't kill the xserver (and I suspect the screen going blank means it is already dead) and it won't let me switch terminals.

But after pressing [ctrl][alt][del], the system will chug away and finally give way to a textbased login. If I sudo reboot from here, the system will restart and then the xserver will fail to start with a bunch of error screens and logs and then dump me back into a text login.

Maybe it's my ignorance about the shutdown command, but it I type sudo shutdown now and it will go through the shutdown process, taking down services and whatnot, but in the end it doesn't shut down and says something about "going single user mood" and I become root.

The shutdown command will just go through the shutdown processes but in the end it just doesn't shutdown and I get a root prompt. Is it safe to just hit the power button at this point? I don't recall it saying anything about unmounting the filesystem so I'm afraid of corrupting something.

So what I have to do is sudo reboot and then catch the BIOS screen and hit the power button there. Whatever causes the xserver not to start is only an issue after reboots, not a cold restart, which is why I have to do a cold restart to get xserver back.

Can anyone point out anything I don't know or am doing wrong?

---

### Post by Kimm on 2005-05-16
sounds strange, all I can think of is that X.org (or XFree?) doesnt support your video card completely... Have you downloaded drivers for linux from whoever makes your video card? (usualy very simple to install), oterwhise perhaps its a library error of some sort... I'we never experianced anything like what your describing so I cant realy help you...

---

### Post by jkndrkn on 2005-05-16
I have suffered from this exact problem. In my case, it was faulty graphics drivers. Are you using an nvidia card? If so, then follow these instructions on installing nvidia drivers. The current version of the drivers solved my crashing issues.

[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

---

### Post by moon2js on 2005-05-17
Graphics? My laptop doesn't really have a dedicated graphics card as it's a bit old. It uses something like an Intel 815em or something like that. I've always used the i810 drivers.

In Warty I had to trouble shoot in order to get videos to play at all and I could never get the videos to play in xv, only in x11 using zoom, which could get a bit laggy. I could never get xv to work. I'm not a very technical person but since my computer doesn't actually have a dedicated video card, I theorized that maybe there wouldn't be any advantage of using xv over x11 anyway since my GPU and my CPU are integrated and they actually share/call on the same system memory as I understand it.

When I installed Hoary, graphics and video *just worked* and I thought it had to do with xorg (as opposed to the xfree86 that I think came with warty). However I do get this weird totem crash, and it tends to happen whenever I'm watching a movie and I perform some other kind of action.

For example, it happened once when I was playing a video and opened a sound file. I was trying to figure out how linux sound works and seeing if I could mix video sound and sound from a different file and a different program. In other cases, it has happened when I was just abiwording, gaiming, firefoxing, etc. It has never happened when I was *just* watching the video, fullscreen or windowed. It doesn't happen often enough to cause me to seriously sit down and trouble shoot. But it has happened a couple times.

I'll definitely check into seeing if I can finetune or get better drivers when I get the chance, but since my system is so old, I kind of figure the drivers that come with linux are as good as they get.

---

### Post by jkndrkn on 2005-05-17
Ah, laptops. Have you used this laptop with windows for an extended period of time? Did you suffer from similar freezes and crashes?

Laptops are a little beyond the scope of my knowledge, but it seems to me that most of the severe freezes and crashes you run into in ubuntu are due to problems with drivers and hardware support.

---

### Post by moon2js on 2005-05-18
Nope. I can't say I ever had a problem with it running under Windows, which I did for years.

Hmm...maybe it has to do with the i810 video driver. That's definitely on my research list once I get some time to do some tinkering.

---

