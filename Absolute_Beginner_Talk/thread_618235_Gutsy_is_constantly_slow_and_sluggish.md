---
title: "Gutsy is constantly slow and sluggish"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by Cpt Black on 2007-11-20
Hi,

I have 7.10 - Gutsy on a Dell Inspiron laptop, 2Gb RAM, 1.73GHz processor.

I think it was after a set of updates, but now Ubuntu is really slow. Simple things such as scrolling in firefox, the page seems to 'chug' down when using the scroller on the mouse. Similarly, streamed movies in firefox, or playing DVDs in the normal player has a stop-start on the video, although the sound is fine.

I am dual booting with Vista, and there are none of these problems in Vista - could it be a bad update for the driver of the graphics card?

Cheers,
CB

---

### Post by natman on 2007-11-20
Hi, are you running compiz? if so try disabling a few of the fanc extras ( or go back to "normal" effects).
Also at the terminal type "top" and see if anything is hogging the cpu, i had a problem with gnash running down the processor ( 70+ % ! ) hope that helps, if it doesnt copy the output of top into the thread.

---

### Post by Cpt Black on 2007-11-20
Hi, I don't think I'm running compiz. I have copied the output below.l

Many thanks for your reply
CB

P.S. Being in Ubuntu now, the best way to describe it is like a time delay between typing or using the mouse and the command actually being done

top - 12:55:32 up 12 min,  2 users,  load average: 2.31, 2.59, 1.69
Tasks: 117 total,   4 running, 113 sleeping,   0 stopped,   0 zombie
Cpu(s): 82.4%us,  8.8%sy,  0.0%ni,  2.9%id,  0.0%wa,  1.8%hi,  4.1%si,  0.0%st
Mem:   2075908k total,   623600k used,  1452308k free,    65588k buffers
Swap:  1951856k total,        0k used,  1951856k free,   298220k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5947 chris     25   0  148m  49m  21m R 30.6  2.4   0:46.08 firefox-bin        
 5391 root      15   0  328m  51m  13m S 15.8  2.5   0:56.83 Xorg               
 5720 chris     15   0 16856 9048 7088 S  2.6  0.4   0:02.49 gtk-window-deco    
 5721 chris     15   0 18152  11m 5092 R  1.0  0.6   0:08.75 compiz.real        
 5843 chris     15   0 35100  11m 8896 S  1.0  0.6   0:03.43 sensors-applet     
 5964 chris     15   0 63120  19m  10m S  1.0  1.0   0:02.30 gnome-terminal     
 5687 chris     15   0 16788 2780 1828 S  0.7  0.1   0:01.01 gnome-screensav    
 5724 chris     15   0 47908  20m  15m S  0.7  1.0   0:06.11 gnome-panel        
 5126 root      15   0 11432 1880 1220 S  0.3  0.1   0:00.58 tclsh              
 5630 chris     15   0 39036  10m 7972 S  0.3  0.5   0:01.00 gnome-settings-    
 5723 chris     16   0 79944  18m  13m S  0.3  0.9   0:04.64 nautilus           
 5751 chris     15   0 49732  17m  12m S  0.3  0.8   0:03.37 nm-applet          
 6118 chris     15   0 56128  34m  11m S  0.3  1.7   0:05.52 checkgmail         
 6150 chris     15   0  2368 1164  876 R  0.3  0.1   0:02.20 top                
 6409 chris     15   0 31532  10m 7428 S  0.3  0.5   0:00.84 notification-da    
    1 root      18   0  2948 1856  532 S  0.0  0.1   0:01.25 init               
    2 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd

---

### Post by jaybombalous on 2007-11-20
> Hi, I don't think I'm **running** compiz. I have copied the output below

nope, not at all!!! :)

> 
5721 chris 15 0 18152 11m 5092 R 1.0 0.6 0:08.75 compiz.real 

---

### Post by Cpt Black on 2007-11-20
Ha, fair enough.

What is it and how do I get rid of it?

Cheers,
CB

---

### Post by shad0w_walker on 2007-11-20
Compiz is the desktops graphical effects, transparency, wobbly windows, that sort of stuff. It can be turned off from the appearance menu. System > Preferences > Appearance.

Look in the visual effects and select the none option.

---

### Post by Cpt Black on 2007-11-20
Awesome, that does the trick.

Many thanks for the help. Another bit of linux knowledge in the bank!!

CB

---

