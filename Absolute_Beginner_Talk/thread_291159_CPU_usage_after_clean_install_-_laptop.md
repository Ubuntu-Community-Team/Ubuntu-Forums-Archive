---
title: "CPU usage after clean install - laptop"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by fatneck on 2006-11-02
Hi, I've reinstalled Ubuntu Dapper Drake on my laptop (details in sig) and let it update itself completely. Now when I boot but before opening any programs I seem to be getting anything from 70% CPU usage to 100% yet the only process that shows up is the System Monitor which shows up less than the amount being used.

So the System Monitor could be wrong, but the fans are on all the time and the machine feels sluggish as you'd expect it to with its CPU maxed out. Incidentally I have installed Ubuntu on much older specced desktops without this problem so its not an underpowered laptop.

It also feels like a PC can feel running only generic video drivers. As I have an ATI card this could also be something to do with it, as the screen refreshes very slowly as I get to the login screen.

Is this 2 separate issues, sorry to cross post if it is. I want to get the CPU down to normal before worrying about the gfx.

Any help greatly appreciated. Thanks.

---

### Post by Lord Illidan on 2006-11-02
I would install the correct kernel, I think it would be the linux-k7 kernel.

Try it, by running :
```

sudo apt-get install linux-k7
``` in a terminal.

---

### Post by randiroo76073 on 2006-11-02
Noticing you have 512 shared memory, just curious what you have graphics set at?

---

### Post by fatneck on 2006-11-02
Thanks for the replies. Just installing the K7 kernel now so I'll come back to you on that one.

No idea about the gfx - in Windoze it defaulted to 128 shared with seemingly no way of changing it. Not really sure how I'd go about finding out here...?

---

### Post by fatneck on 2006-11-02
No difference after the kernel upgrade so if anyone has any more suggestions I'll be glad to hear them. Thanks!

---

### Post by Lord Illidan on 2006-11-02
Try opening System Monitor and selecting View - All Processes. Which is taking up the most cpu now?

---

### Post by fatneck on 2006-11-02
gnome-system-monitor about 60%
Xorg about 26%

and the CPU history line is still fluctuating between 75ish and 100%

The monitor shouldn't be using that surely, but something is eating the CPU cycles...

---

### Post by mad0master on 2006-11-02
Well, are u running on battery or AC power?
If AC power, try "cpu-freq" and set the avaible minimul frequence. See this page: [http://doc.gwos.org/index.php/CPUFreq](http://doc.gwos.org/index.php/CPUFreq)

---

### Post by podunk on 2006-11-02
You might try the command
```
top
```
because I'm sure the system monitor isn't using that much.

Have you installed the video drivers? xorg shouldn't be taking up 25% of your cpu.

---

### Post by fatneck on 2006-11-02
Running on AC Power, but there seemed to be no difference when I pulled the lead out and switched to battery.

Will try teh CPU FREQ later/tomorrow, and the 'top' command. Even if the System Monitor is wrong the machine is still sluggish.

The ATI drivers are definitely not installed, but I haven't even got on to that nightmare as was hoping to fix the CPU issue first - unless they are related perhaps...?

---

### Post by podunk on 2006-11-02
The problem might very well be that all your CPU is being used to render your desktop instead of doing real work. For instance doing "top" on my machine with an old ATI card xorg is less than 1% of my CPU. With 15 apps open it goes up to between 1 and 2 percent. Playing a movie it's around 20%.

I *think* a valid way to tell if it's graphics related would be to press CTRL ALT F1 to exit your desktop to the command shell. Use the top command and see what your CPU usage is. If it's dropped down to 1 or 2 percent it would be a strong indication? 

When you are ready to return to the desktop press CTRL ALT F7

---

### Post by drobvice on 2006-11-02
My install sped up dramatically after fixing my fglrx driver.  I have a 9800 pro card.  I was rendering a tv card input but it seems firefox isn't as sluggish with pages with alot of ads as well.

---

### Post by fatneck on 2006-11-03
After running 'top' Xorg looks to be using about 10-15% and then not much else is happening. However the line above says CPU usage 75% or thereabouts, so even this can't agree with itself...grrrrr :)

---

### Post by fatneck on 2006-11-03
Update - have now installed the ATI drivers successfully (I think). Glxgears was previously giving me about 17 fps and now its about 100. However, in Windows this machine will play Quake 3 Arena reasonably, so I'm not convinced, and its still not totally smooth.

CPU still too high though.  Any more help be appreciated.

---

