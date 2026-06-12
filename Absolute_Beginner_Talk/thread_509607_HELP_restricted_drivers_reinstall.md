---
title: "HELP restricted drivers reinstall"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by paradoxchild on 2007-07-25
I'm not sure what caused my initial problem, but now I have a bigger problem.

I need to somehow either reinstall or re-enable restricted drivers. I have nvidia-glx-new installed and reconfigured xserver multiple times. I've tired a bunch of stuff like modprobe -i nvidia which worked for some people, changing nvidia to nv, installing nvidia-glx, reinstalling drivers a ton of times. Updating, upgrading, dist-upgrade, etc.

Pretty much what happened is I plugged in my new lcd monitor, got reconfigured xorg to get 1440x900 res and the correct refresh rate. For some reason though any videos I had wouldn't show up, and it made the whole system kinda glitchy when trying to play it. Eventually it ended up that after reinstalling and installing other nvidia drivers, including automatix ones, and trying to configure it differently through nvidia-config thing, it still didn't fix it. So I went a disabled the restricted drivers (nvidia graphics accelerated) restarted x (ctrl alt backspace), I went into my videos, played one, and it worked fine. I looked at the restricted drivers manager and it said that it was still enabled. So I restarted my pc to make sure everything worked and all hell broke loose. Then I did everything I mentioned above, and I still can't get my system back up

If someone could tell me how to re-enable restricted drivers from terminal that would be great since that is the only thing I can use. 

If no one has that answer at least tell me of a way to reinstall ubuntu without destroying all my settings and programs, I have some custom stuff that is really annoying to set back up, and some stuff that would take awhile to set back up because I'm not sure where to get it at.

Please Help!!!!!

---

### Post by wolfen69 on 2007-07-25
did you try the regular nvidia drivers? (not new)

---

### Post by paradoxchild on 2007-07-25
yes, i've tried all the drivers but I can't get it back up, I'm pretty sure it's because I disabled the restricted drivers. If you think it's something else and know how to fix it tell me, I'll try it.

---

### Post by overdrank on 2007-07-25
> **paradoxchild said:**
> yes, i've tried all the drivers but I can't get it back up, I'm pretty sure it's because I disabled the restricted drivers. If you think it's something else and know how to fix it tell me, I'll try it.

Hi, Ok lets try this command. I believe you are saying you have the desktop gui so use the keys all at the same time alt.ctrl,F1 and this will take you to the terminal.Login user name and password the run this command
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Answer the questions and hopefully this will get you going then you can use Envy to install you drivers for the video card. Good luck!

---

### Post by paradoxchild on 2007-07-25
tried that and it still didn't work, let me clearly explain my situation.

I am running feisty, which was upgraded from edgy. I have the nvidia-glx-new drivers installed. In the gui, to try to solve my weird problem of not being able to play videos I went to the restricted drivers manager and disabled using the nvidia graphics accelerator, which I guess was put in when upgrading to feisty, since nothing else fixed the problem and it seemed that the video driver was the problem. I restarted x (ctrl alt backspace) and was able to play videos fine. I restarted the computer to make sure everything was fine, and then I could no longer get a gui up anymore, even after reconfiguring xserver-xorg a bunch of times, and installing other nvidia drivers.

So I would like some way to enable the "nvidia graphics accelerator" restricted drivers, it would be easy to do in gui just by going to restricted drivers manager, but I can't get a gui up, I'm doing everything in command line, and booting into recovery mode. 

The error I get is that screen(s) were found but unusable, than something like fatal error: no screens found.

I've tried other commands that other people have used to fix the no screens found, like modprobe -i nvidia, but nothing works.

---

### Post by paradoxchild on 2007-07-26
Alright I've tried everything I can think of and everything I've found on the forums, and done each with different nvidia drivers installed. (nvidia-glx, nvidia-glx-new)

I've dpkg-reconfigure -phigh xserver-xorg and used nv driver, I've reinstalled drivers a million times, I've done nvidia-xconfig, I've done nvidia-glx-config enable, and everything else I've listed before this.

The closest I get to a gui is starting x with the nv driver but there I get one color and no desktop, but I can here it boot up, or a color with a bunch of lines of another color going diagonally across the screen. But when I get to this point I can't do anything else because it won't let me go back to runlevel 1 or any other level (command line run levels). If I restart the gui (ctrl alt backspace) it just changes the color I get to look at. Someone please help !

---

