---
title: "new to ubuntu, gone all slow!!"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by marcher83 on 2008-03-09
Hey guys 

Ive only had ubuntu on my computer for about 3 months, was a windoze user, i like is so much better, my mate got me onto it.

So i have been trying to teach my self, and using these fourms (which is so very helpfull)
Cept  been installing things when i dont know what i am doing, latlest thing i installed was emerald, scince that everyhing i use is so slow, its like all the computer resorses are being used by somthing , firefox, email everything is slow to open and very laggy.


PLease help . should i resintall and start again?

---

### Post by chewit on 2008-03-09
This tutorial will help clear some of your old files out and hopefully make it faster.

[http://ubuntuforums.org/showthread.php?t=140920&highlight=clear+rubbish]("http://ubuntuforums.org/showthread.php?t=140920&highlight=clear+rubbish")

---

### Post by 3rdalbum on 2008-03-09
First, when your computer becomes slow, go into the terminal and run the command "top".

Copy the information and paste it into here, and we'll see what's eating up your CPU.

---

### Post by oskar2000 on 2008-03-09
you can also use the gnome-system-monitor (alt-f2 and type, or System-Administration-System-Monitor)

---

### Post by marcher83 on 2008-03-09
thanks guys for quick reply

here is the paste!!

top - 16:50:07 up  1:17,  2 users,  load average: 0.94, 0.74, 0.72
Tasks: 113 total,   3 running, 110 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.0%us,  2.5%sy,  0.0%ni, 95.3%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   1035324k total,   606916k used,   428408k free,    17148k buffers
Swap:  3028212k total,        0k used,  3028212k free,   328636k cached

mark@mark-desktop:~$ I  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                             
mark@mark-desktop:~$ 0  577m  41m 3940 S    5  4.1  25:13.77 Xorg                                                                                                                
 5830 mark      15   0 90736  21m  12m S    2  2.1   0:00.48 gnome-terminal                                                                                                      
 5362 mark      15   0 33124  25m 7204 R    1  2.5   5:22.73 Xgl                                                                                                                 
 5640 mark      15   0  191m  57m  22m S    0  5.7   0:44.87 firefox-bin                                                                                                         
 5850 mark      15   0  2368 1168  876 R    0  0.1   0:00.05 top                                                                                                                 
    1 root      15   0  2948 1852  532 S    0  0.2   0:02.56 init                                                                                                                
    2 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                            
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                                         
    4 root      34  19     0    0    0 S    0  0.0   0:00.02 ksoftirqd/0                                                                                                         
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                          
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                                         
    7 root      34  19     0    0    0 S    0  0.0   0:00.01 ksoftirqd/1                                                                                                         
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                                          
    9 root      10  -5     0    0    0 S    0  0.0   0:00.02 events/0                                                                                                            
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1                                                                                                            
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                             
   31 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0                                                                                                           
   32 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                                                                                                           
   33 root      16  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                                              
   34 root      16  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                                        
  122 root      10  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                                                                             
  147 root      16   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                                             
  148 root      15   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                                             
  149 root      11  -5     0    0    0 S    0  0.0   0:00.00 kswapd0                                                                                                             
  200 root      11  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                                               
  201 root      11  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                                               
 2038 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                                       
 2053 root      10  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                                               
 2099 root      10  -5     0    0    0 S    0  0.0   0:00.06 ata/0                                                                                                               
 2100 root      10  -5     0    0    0 S    0  0.0   0:00.18 ata/1                                                                                                               
 2101 root      17  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                                             
 2196 root      10  -5     0    0    0 S    0  0.0   0:02.08 scsi_eh_0                                                                                                           
 2197 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                                                                           
 2220 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2                                                                                                           
 2221 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_3                                                                                                           
 2257 root      14  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_4                                                                                                           
 2258 root      10  -5     0    0    0 S    0  0.0   0:00.09 usb-storage                                                                                                         
 2439 root      10  -5     0    0    0 S    0  0.0   0:00.06 kjournald                                                                                                           
 2645 root      12  -4  3028 1376  408 S    0  0.1   0:00.27 udevd                                                                                                               
 3620 root      19  -5     0    0    0 S    0  0.0   0:00.00 kpsmoused                                                                                                           
 4223 root      18   0  1696  520  448 S    0  0.1   0:00.00 getty

---

### Post by 3rdalbum on 2008-03-09
I don't see anything wrong there, unless you hit top during a time when the computer was running fast. I did notice that you're running XGL - have you got an ATI card?

Since you mentioned that the last thing you installed was Emerald, let's try simply turning off Compiz. Close the terminal you've got open, press Alt-F2, and type (or paste) this in:

```
metacity --replace
```

If your speed improves, then your problem is probably with Emerald, or with Compiz itself.

---

### Post by marcher83 on 2008-03-09
No good. 
yeah i have a ati radeon x800, i have a feeling i installed a nivida driver at some stage and this was my problem, if only i was more computer illitrate!! :)
ubuntu is so much better than windows...cant believe how fast and bugg free its been untill now!... thou i suspect its my own falt .

one if the biiggest problems what ever i have done. is when browsing (like now) when i type it takes a while to display on screen, when scrolling up and down the screenit goess all "jerky" and takes about a minute to get to the bottom of the page!!!

---

### Post by Exonimus on 2008-03-09
that does sound like a wrongly(or not) installed video driver... are you sure you installed the correct one?

also, dont want to sound irritating, but you meant to say:  more computer literate. I you were more illiterate, you'd want to know less and less about computers :D

---

### Post by marcher83 on 2008-03-09
haha yer sorry !! 

to be honest with you , im not 100% sure its all installed.... i followed a link i had stubbled accross.   i nede a book or something to read. about ubuntu....1st time in my life i have switched o/s


ill do a search and try suss it out....

---

### Post by Nitro Fan on 2008-03-09
> **oskar2000 said:**
> you can also use the gnome-system-monitor (alt-f2 and type, or System-Administration-System-Monitor)


I just tried this cant make it work any ideas?

---

### Post by marcher83 on 2008-03-09
click "system" --> "Admin" -->"system monitor"      same thing

---

### Post by billgoldberg on 2008-03-09
> **marcher83 said:**
> haha yer sorry !! 

to be honest with you , im not 100% sure its all installed.... i followed a link i had stubbled accross.   i nede a book or something to read. about ubuntu....1st time in my life i have switched o/s


ill do a search and try suss it out....

I might be stating the obvious here but did you try

"system -> administration -> restricted drivers managment" to install the ati driver?

It sounds like a graphic card problem.

I had the same problem with my pc without the correct driver.

For compiz fusion (and thus emerald) to run good I needed to follow the instructions [here]("http://linuxowns.wordpress.com/2007/12/07/gutsy-gibbon-710-xgl-ati-fglrx-compiz-fusion/") after I installed the ati driver.

---

