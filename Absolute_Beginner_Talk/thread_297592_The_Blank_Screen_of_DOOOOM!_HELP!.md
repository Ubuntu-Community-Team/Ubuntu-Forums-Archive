---
title: "The Blank Screen of DOOOOM! HELP!"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by That_Geek on 2006-11-11
Well, that title may have been a bit dramatic, but it means what i want it to say

lets go through a timeline of events

1.i wanted to install enemy territory and i posted a thread about it, thanks so much to everyone that helped, cause it is installed

2. i tried to run it from command line and it booted up into ET like normal, then like a second and a half later it reverted back to the ubuntu desktop

3. I tried this again and it did the same thing

4. A few more times like this, then i got smart and read the error message

5. it said something like no hardware acceleration, type in xxxx code to launch anyway

6. so i put in the xxxx code and it started right up, but as it said, without any hardware acceleration

7. So i thought, well this sucks, im gonna hafta go find some drivers for my nVidia geforce fx-5200 gfx card

8. so i read a wiki about a bunch of problems and solutions in Ubuntu

9. I tried what i said, it installed with almost no trouble whatsoever

10. Then, at the end it said you know, restart to implement changes or whatever

11. (heres where the real trouble starts) it booted up and i got i believe is whats called the splash screen where it lists a bunch of system processes and it has "ok" on the right side of the screen and a bar goin across the top

12. anyway, it got past the splash screen to what should have been the login, and it was just all black

13. Then it gave me a command prompt, but with no connection to x (i tried to launch ET, and thats what it said, no connection to x server)

13. so i tried to boot into failsafe mode and it did the exact same thing, except that it gave me the blue screen of death

Now, i know the problem was when i installed the nvidia drivers, anyone perhaps know how to fix this

Thanks a bunch everyone

---

### Post by Liolikas on 2006-11-11
Linux do not make BSOD it is **unpossible.**

---

### Post by That_Geek on 2006-11-11
what is BSOD?

remember, im a complete newb to linux, it took me 100 hours and many failed attempts to even get ET to run

---

### Post by Liolikas on 2006-11-11
the blue screen of death == BSOD

---

### Post by That_Geek on 2006-11-11
ahh, yes, BSOD is rather unpossible
lol

---

### Post by doobit on 2006-11-11
I have not had this problem, so take my advice with a grain of salt. I only hope to point you in a direction. First, try to start the x server from the command prompt using the command: startx

That will at least give you some more error statements to give you some direction. There is a better way to install the nvidea drivers here on the forums that I've seen and you should probably do a search and try to find them.

When all else fails, or even before that, you might want to try Automatix2 at [www.getautomatix.com](www.getautomatix.com)

---

### Post by That_Geek on 2006-11-11
well, i just worked on it for a few minutes and now instead of BSOD, i get frequency out of range, try other frequencies

i used the ```
 sudo nano /etc/X11/xorg.conf
```

and then tried to update it with 

```
 sudo dpkg-reconfigure -phigh xserver-xorg 
```

also, i used the startx command and the exact same same frequency out of range thing came up

is the frequency out of range thing a step forward or a step back?

---

### Post by That_Geek on 2006-11-11
may i please bump this?

---

### Post by doobit on 2006-11-13
Frequency out of range means you have chosen a refresh rate that's not supported by your monitor.
It's a step forward because now you should be able to correct it. Edit Xorg.conf I would start with 60HZ or 70HZ

---

### Post by SZorg on 2006-11-13
If you're not sure how to do that, the easiest way is to put _60 after the resolution of your choice. It should look like:
[code]"!280x1024_60" or "1024x768_60", whatever your resolution is.


To be safe, I would do it on all bit depths (1-24) and remove the other options. Obviously, back up before you do this.

---

