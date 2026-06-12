---
title: "Can't start ubuntu!"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by advilandy on 2007-03-25
This has been an ongoing, worsening problem. Each time I boot into ubuntu the screen with the progress bar loads almost all the way and then the ubuntu logo and underneath the bar turn weird colors. Usually after this, the login window appears and I can run ubuntu sans the ability to crtl+alt+f1 into a new terminal, which shows just a mess of colors.

I have no idea what is wrong, and running envy, replacing my xorg.conf and trying to type in my username/password do not work. I am reduced to logging into safe mode and then typing startx as root to get anything working.

Anyone know what this could be?

-advilandy

---

### Post by medad on 2007-03-26
Not sure if I can help, but if you could explain what configuration that you have (i.e. video card, monitor, etc...), maybe and which version of Ubuntu you are loading; it would give an idea of what you are dealing with.

---

### Post by profXavier on 2007-03-26
What are your system specs? Nvidia or ATI? If you are getting strange colors on both your login screen (or before it) AND in your shell, that sounds like a real issue.  X doesnt run when you are in a shell, ctrl-alt-f*, so if your colors are off in there, then maybe its a monitor issue.  Maybe check the connectors to your monitor/video card to ensure they are connected properly.

Maybe try another monitor, if you have one available.

---

### Post by advilandy on 2007-03-26
I have an ati x850 pro, and I fixed the not booting issue by reconfiguring gdm as root in recovery mode, but I still get the weird discoloration on the loading screen and when I crtl+alt+f*. I don't think it's the monitor as it hasn't ever had any other problem, but at least I am able to log in and use xgl now.

Is there any way to disable the initial screen that shows the progress of starting up processes and instead use the sort of thing recovery mode uses when it starts up (the mess of text)? I feel like it's this screen my computer is having an issue with in some capacity.

*edit*
I used envy to install  my ati driver and installed beryl step by step so I don't think it's my xorg.conf or anything.
Also, I have a ViewSonic 17'' monitor (I'm at work now so I don't know which model)

---

### Post by jhenager on 2007-03-26
Another thing to check would be the physical connection of the video card (assuming it isn't onboard video). There is a thing called 'thermal creep' where a card (because of expansion and contaction from heating and cooling) causes connection problems.

---

### Post by billybobjoe on 2007-03-26
I am having the same problem with my x700 pro.  It happened when I tried to update my ati drivers.  Hey Advilandy, what was your solution?  Please be thorough on what you did in the root console.  I am a noob and do not know the terminal commands.
Thanks

---

### Post by advilandy on 2007-03-26
@billybobjoe
The solution to the not being able to log in was to go to root and reconfigure gdm and xorg:

```
sudo dpkg-reconfigure xserver-xorg
sudo dpkg-reconfigure gdm
```

Put these lines in one at a time and obviously after each there will be a little bit of input needed to configure your card, but the defaults are usually okay so that you can pretty much just hit enter or type yes all the way through.

Also, try installing envy to configure your xorg stuff...it's way easier just to type sudo envy when something goes wrong.

Let me know if you have any other problems/solutions, and I I try and respond (I have a bunch of stuff going on including an ochem midterm coming up tomorrow)

@jhenager
Thanks for the suggestion - I will check the connection later on tonight!

---

### Post by advilandy on 2007-03-28
Doesn't seem to be the thermal creep...I'm going to keep looking for a solution and I'll post if I find it.

---

### Post by billybobjoe on 2007-03-28
Thanks for the help Advilandy, Im up and running again.  Thanks again

---

