---
title: "Boot up problem (black screen with loading cursor)"
date: 2009-01-07
forum: Apple Hardware Users
---

### Post by Djesse on 2009-01-07
Hi all, I'm a Linux newbie so I don't have much knowledge about Linux or Ubuntu. I only use Ubuntu for a few days and now I've encounter this problem that's really killing me. this might be long, sorry.
I'm using Ubuntu x64 8.04 Hardy Heron on a 2nd revision MacBook Pro dual boot with Windows XP Pro 32bit right now, and last night I was trying to install Handbrake 0.9.3 from source code, because the deb pack I downloaded from the Handbrake website didn't work, I was able to install it by double clicking the deb pack, it appears in the main menu, but when I click it, it won't start. That's why I was trying to install it from source code, I followed some tutorials from the internet but still no luck, and I realized that I need to install something else first, such as "jam", "yasm",and getting the proper ffmpeg from the medibuntu repository. I did all that but still no luck, I also installed the libdvdcss2 library for DVD playback in VLC, and the w64codecs. When I was trying too watch DVDs using VLC, It was fine but the video quality wasn't so good, but I just keep watching the DVD for about one hour, but when I try to run other applications it won't work, I tried to run the movie player, I can see in the task bar it says "starting movie player" but later it just gone away and the movie player never come up, same thing happened the other apps I tried. So I think I maybe mess something up when I was trying to install Handbrake from source code, I thought I should restart my computer, and that's when the real nightmare begins. Everything seems to be fine, the orange bar in the loading screen fills up quickly like before and the screen turns black, flashed a few times, just like usual. And I can see the cursor turn into a white ball with some black dots spinning around inside it, I was expecting the log in screen to appear but it never does. I leave it like that for about 10 minutes but still the same, and I hit the power button, restart the computer and still the same. I've been trying to find a solution in this forums and Google around, follow a bunch of tutorials but still no luck. Can someone please help me, I've been trying for a whole day, rebooting my computer more than a dozen times since I only have one computer, I'm really tired of trying so I post this thread hoping someone can help me. So sorry for such a lengthy story, I just think I should let you guys know what I've been doing with my computer before the problem would help. Thank you for reading this, any suggestion would be appreciated. I'm so desperate now:cry:

---

### Post by neu2buntu on 2009-01-07
not sure but maybe you needed to install the 32bit version of ubuntu instead of the 64bit(just a suggestion,)

---

### Post by Djesse on 2009-01-07
> **neu2buntu said:**
> not sure but maybe you needed to install the 32bit version of ubuntu instead of the 64bit(just a suggestion,)

Thank you so much for the quick reply, I really hope I don't have to do this.

---

### Post by neu2buntu on 2009-01-07
no problem.... do you know what your processor is?

---

### Post by neu2buntu on 2009-01-07
try booting up with your live ubuntu cd and open the terminal and copy and paste the output of ```
cat /proc/cpuinfo
```

the terminal can be found in >applications>accessories !!

---

### Post by Djesse on 2009-01-07
> **neu2buntu said:**
> try booting up with your live ubuntu cd and open the terminal and copy and paste the output of ```
cat /proc/cpuinfo
```

the terminal can be found in >applications>accessories !!

I don't have the LiveCD now but I know what my CPU is. It's an Intel Core2Duo 2.33 Ghz, code name should be something like "meron". I'll try to find my LiveCD again.

---

### Post by neu2buntu on 2009-01-07
yeah you are ok with the 64bit install....with merom.  so the problem lays elsewhere.   you will need to dig out your livecd tho,to see what damage you have done.... to be honest i would not have a clue how to go about fixing your system if you messed it up installing something from source...sorry

---

### Post by Djesse on 2009-01-07
> **neu2buntu said:**
> yeah you are ok with the 64bit install....with merom.  so the problem lays elsewhere.   you will need to dig out your livecd tho,to see what damage you have done.... to be honest i would not have a clue how to go about fixing your system if you messed it up installing something from source...sorry

OK, I've found my LiveCD, just tell me what should I do and I'll post the result here. And thank you so much for trying to help neu2buntu.

---

