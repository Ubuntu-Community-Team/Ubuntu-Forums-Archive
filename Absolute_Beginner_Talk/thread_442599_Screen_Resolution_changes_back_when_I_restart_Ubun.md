---
title: "Screen Resolution changes back when I restart Ubuntu..."
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by keiwc on 2007-05-13
Hey,
        I recently installed Envy Nvidia Settings onto my Ubuntu Feisty Flaw, i am able to change the resolution in the Nvidia settings to 1440x900. and it looks clear. But when i restart the OS, it changes back to 1024x1280. I dont really understand why, I was wondering if anyone else is experiencing the same problem. Thanks. :)

---

### Post by Hobo Joe on 2007-05-13
Open terminal, then type:
```

sudo nvidia-settings

```

Set everything how you want it, then click, 'save to X configuration file'.

The it doesn't save unless you open it with sudo. I still have no idea why, but that's just how it is.

---

### Post by Happy_Man on 2007-05-13
> **Hobo Joe said:**
> 
The it doesn't save unless you open it with sudo. I still have no idea why, but that's just how it is.

That's because you need root permission to edit xorg.conf, which sudo gives. Thus, the need to run program with sudo to give root permission to edit xorg.conf.

---

### Post by Hobo Joe on 2007-05-13
But couldn't it just prompt your password?

---

### Post by Happy_Man on 2007-05-13
That's the decision of the guys who made the program, not the OS.

---

### Post by keiwc on 2007-05-13
Thanks a bunch! Works great now. :)  The Nvidia Logo also loads, when the OD starts up, very nice indeed.

---

### Post by Hobo Joe on 2007-05-13
Yeah, I just got it up and running yesterday, it's great. :)

But now I want to install 32-bit but it doesn't work.... :(

---

### Post by pizpot on 2007-05-20
This is not working nvidia. Hello!?! And another thing nvidia, this is not Windows. Don't go screwing up linux. I have edited my /etc/X11/xorg.conf (as sudo) and for each depth I set the resolutions like this:

Modes      "1024x768" "800x600" "640x480"

and yet when I run sudo nvidia-settings, I see every resolution under the sun. Really, what the hell do I want 1152x864 flashing at 50Hz. My monitor looks blurry at 1280 and guess what it keeps reverting to, 1280x1024. What are you going to do next, make a binary file registry? SHeesh.

Thanks alot, I was much happier with the default resolution setting program, but now it is also not sticking. I used the Automatix nvidia installation and it is ubuntu7.04.

---

### Post by awdyson on 2008-02-13
I was having the same problem with a 1440X900 resolution.
I guess it's a gnome issue.

anyway, I found a [[COLOR="Blue"]bug repor[/COLOR]t]("https://bugs.launchpad.net/ubuntu/+source/control-center/+bug/16694") with this fix:
```
gconftool-2 -t int -s /desktop/gnome/screen/default/0/rate **your rate**

gconftool-2 -t string -s /desktop/gnome/screen/default/0/resolution "**your resolution**"
```

I assumed rate was the refresh frequency, but my machine started at 50hz after I set that value to 60.
that was fine for me as both values are within my monitor's limits, but I'd check the screen settings *(System -> Administration -> Screen and Graphics)* after to make sure you aren't going to hurt anything.

good luck all; this one frustrated me for a while.
-Alex

---

### Post by jonatan5 on 2008-02-14
I have the same problem  Screen Resolution changes back when I restart Ubuntu,
     but_ I do not understand witch line I must change in xorg.conf file_. There are lists of lines with all possible resolutions, but there is none, with   Default written   or something. 
Should I just delete all resolutions what I do not want.
 Ok, I guess then I would have a black screen after next restart.

---

