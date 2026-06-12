---
title: "Computer very busy when doing nothing, fan wherring etc."
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by woodlandjustin on 2006-10-14
I use my laptop generally just for the internet, so I use firefox. I have Ubuntu 6.06 LTS, on a Toshiba satellite about 5 years old. Sometimes I have firefox open, and maybe 2 tabs for example, and then I am doing nothing, and so the screen eventually goes black, but still the computer seems busy, so much so that the fan often turns on!! I have no idea why it should be so busy while doing nothing!!!

Before I had Ubuntu I briefly had DSL (damn small linux). My machine was very quiet then. If I did nothing, the fan did not run. Actually even the other moving parts stopped! I don't know about computers but maybe there are some disks that wherr around inside? Anyway those stopped completely, so that my computer was utterly silent!! And, even if I then moved the mouse around and even clicked on other pages and browsed the internet, sometimes it would still remain utterly silent!! That seems very efficient. However, at the moment this system with Ubuntu seems very inefficient.
Is there a solution?
Thanks
Justin

---

### Post by adwait on 2006-10-14
ARe you runinng amarok? There is osme bug with the amarok sqlite database which causes it to continuously loop taking processor usage to 100%. Another thing that could cause problems is some superkaramaba widgets.

---

### Post by jordanmthomas on 2006-10-14
Perhaps the screensaver is running?  Some of those are pretty intense, and just because you can't see them on your screen because it is powered off doesn't mean they aren't still being rendered.

Try watching the command 
```
top
```
in a terminal.  You can see if a process has been raping your system by looking at how much CPU time it has taken in comparison to other programs

```
 [FONT="Courier New"] PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
 5117 jordan    15   0 22852  15m 3844 S  8.6  3.2  21:32.70 enlightenment      
 4521 root      15   0  430m  38m 6060 S  7.0  7.7  24:09.50 Xorg               
 5217 jordan    15   0  166m  50m  23m R  7.0 10.2 192:16.86 amarokapp          
 4972 root      15   0  6044 1316 1060 S  0.3  0.3   2:17.18 nmbd               
 5230 jordan    15   0 30264 9.9m 9064 S  0.3  2.0   0:13.02 kded               
16414 jordan    15   0  119m  59m  16m S  0.3 12.1   0:37.99 opera  [/FONT]            
```

As you can see, amarok has taken up a lot of my CPU in comparison to the others running.  Find the culprit, and make it pay!  :twisted:

---

### Post by woodlandjustin on 2006-10-19
Hi guys
I don't know what Amorak is. I did that code and it was really difficult to copy the output because it kept changing!! Finally I caught it (slippery fish!)

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4293 root      15   0 68172  40m 5476 S  8.3 16.2  23:46.51 Xorg
28638 justin    15   0 77752  15m 9740 S  4.3  6.2   0:06.01 gnome-terminal
10965 justin    15   0  131m  22m  12m S  2.7  8.8   4:52.28 rhythmbox
 5463 justin    15   0  217m  89m  15m S  0.3 35.8  22:48.20 firefox-bin
 8064 justin    15   0  2836  856  676 S  0.3  0.3   0:54.79 esd
25311 justin    15   0 27364 7120 4372 S  0.3  2.8   0:29.75 audacity
    1 root      16   0  1564   84   60 S  0.0  0.0   0:02.77 init
    2 root      34 

And like I said it kept changing. Anyway there is a snap shot. Does it mean anything to you? (Nothing to me!!!)
My fan is currently coming on and off, mostly off.
Thanks!
Justin

P.S. How can I delete al of the screen savers then? I heard they were only of any actual use for old monitors anyway not LCD, is it? If it'll help I'll scrap them!
Thanks!

---

### Post by jordanmthomas on 2006-10-19
a) amarok is a media player.  It had only taken that much time because I always have it running.
To stop the screensaver:
```
killall gnome-screensaver
```
will turn off the screensaver.  You should be able to make it not start up in System --> Preferences --> Session

As a side note, you could have stopped top by pressing Q.
I don't see anything unusual here, but X using that much CPU hints that you don't have proper graphics drivers installed (explaining why screensavers beat you so bad.)

---

### Post by tgunner on 2006-10-19
Yes, screensaver does sound like the issue. To easily turn it off, go to: System -> Preferences -> Screensaver -> click Blank Screen -> click Close.

---

### Post by woodlandjustin on 2006-10-20
Will that turn it off FOR EVER? Or can I just uninstall it or delete it permanently? It seems not right to me to have some junk on my computer I never wanted in the first place and never will want, not serves any function. Surely better to use the space for something else!
Thanks all

By the way I have troubles with all of my many media players (banshee, rythm box, gxine etc etc. They all have different malfunctions and errors, though usually I can find at least one of them that can play which file I want. Is there one you can recommend that can do everything and actually works? Thanks!
Justin

---

### Post by sKuarecircle on 2006-10-20
With regards to your Media player issues, have you downloaded Automatix ?( if not do a search ion the forum) and do it. Download the Non-Free codecs and you media player issues will be sorted for ever, alsio there are many other useful bits in Automatix that you might find useful.

---

### Post by woodlandjustin on 2006-10-20
> **sKuarecircle said:**
> With regards to your Media player issues, have you downloaded Automatix ?( if not do a search ion the forum) and do it. Download the Non-Free codecs and you media player issues will be sorted for ever, alsio there are many other useful bits in Automatix that you might find useful.

Did that long ago and still there are some video clips I can't see. And often clicking on video clicks caused the firefox to totally freeze and I loose all my tabs 'cause I have to force quit. I am now afraid to click on any video clips! It crashed it so often! Some people said it was BECAUSE of automatix and that I should uninstall all that automatix did and start again using the step by step guide somewhere in Ubuntu codex something or others page. I don't have the energy to do that to be honest. The whole thing is too time consuming.
I don't get it. I know I'm not a programmer or anything but I would have thought there would be some sort of logic to this system. For example I used automatix to instal muine, in one of my attempts to find a media player that worked. It could not even open mp3s!! Hw is that possible? All the codecs were there, so the other programmes could open them?
I really don't get this whole OS.
Thanks for help!
Justin

(I haven't mentinoed yet the problems all my CD burning programs have! If I'm lucky one of them will be able to do the task I want!! All different malfunctions too!)

---

### Post by woodlandjustin on 2006-10-21
Seeing as that output from doing "top" in he terminal keps changing every 2 seconds, here are a few freeze frames I just took now. I came back to my computer and the fan was wherring away like mad. The screen was black. Moving the mouse makes the "enter password" box come up, so I do it and then I'm back in. All I have running is Firefox. And nothing should have been happening right, seeing as I was logged out or whatever you would say ssing that the sreen was black and I had to reenter my password. Now it's been maybe 10 minutes since I logged back in, just to take the code output (below) and write this. The fan is still full on. I am hoping that this code stuff will help you guys understand what is wrong with my system!
Thanks!


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4295 root      15   0 48496  34m 8128 S  3.0 13.7  38:18.19 Xorg
 9301 justin    16   0  2196 1100  856 R  1.0  0.4   0:00.30 top
 5099 cupsys    26  10  4200 1760 1296 S  0.3  0.7   0:02.02 cupsd
 9250 justin    15   0 32588  13m 8372 S  0.3  5.3   0:02.84 gnome-terminal
    1 root      16   0  1564  524  460 S  0.0  0.2   0:02.74 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.09 events/0
    5 root      11  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.10 kblockd/0
    9 root      10  -5     0    0    0 D  0.0  0.0   0:00.06 kacpid
  110 root      15   0     0    0    0 S  0.0  0.0   0:00.02 pdflush
  111 root      15   0     0    0    0 S  0.0  0.0   0:00.05 pdflush
  113 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  112 root      15   0     0    0    0 S  0.0  0.0   0:00.23 kswapd0
  700 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 kseriod




  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4295 root      15   0 48508  34m 8128 S 11.6 13.7  38:32.99 Xorg
 5393 justin    15   0 14912 5116 4184 S  4.3  2.0   0:02.05 gnome-screensav
 5395 justin    15   0  184m  72m  20m S  3.0 28.8   4:33.03 firefox-bin
 4474 messageb  15   0  2192  860  672 S  1.0  0.3   0:00.42 dbus-daemon
 5356 justin    15   0 18192 5980 4624 S  0.7  2.3   0:00.90 gnome-power-man
 9331 justin    16   0  2196 1100  856 R  0.7  0.4   0:00.55 top
 4490 haldaemo  15   0  6804 2232 1508 S  0.3  0.9   0:02.83 hald
 5099 cupsys    26  10  4200 1760 1296 S  0.3  0.7   0:02.07 cupsd
    1 root      16   0  1564  524  460 S  0.0  0.2   0:02.74 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.09 events/0
    5 root      11  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.10 kblockd/0
    9 root      10  -5     0    0    0 D  0.0  0.0   0:00.06 kacpid
  110 root      15   0     0    0    0 S  0.0  0.0   0:00.02 pdflush


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4295 root      15   0 48520  34m 8128 S  5.0 13.8  38:43.09 Xorg
 5395 justin    15   0  176m  72m  20m S  4.6 28.8   4:40.61 firefox-bin
 9375 justin    16   0  2196 1096  856 R  1.3  0.4   0:00.54 top
 9250 justin    15   0 69556  13m 8884 S  0.7  5.5   0:07.11 gnome-terminal
 5099 cupsys    26  10  4200 1760 1296 S  0.3  0.7   0:02.10 cupsd
    1 root      16   0  1564  524  460 S  0.0  0.2   0:02.74 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.09 events/0
    5 root      11  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.10 kblockd/0
    9 root      10  -5     0    0    0 D  0.0  0.0   0:00.06 kacpid
  110 root      15   0     0    0    0 S  0.0  0.0   0:00.02 pdflush
  111 root      15   0     0    0    0 S  0.0  0.0   0:00.05 pdflush
  113 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  112 root      15   0     0    0    0 S  0.0  0.0   0:00.23 kswapd0



  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5395 justin    16   0  176m  72m  20m R  4.6 28.8   4:54.23 firefox-bin
 4295 root      15   0 48544  34m 8128 S  4.3 13.8  38:56.18 Xorg
 9408 justin    16   0  2192 1100  856 R  1.0  0.4   0:01.69 top
 5099 cupsys    26  10  4200 1760 1296 S  0.3  0.7   0:02.22 cupsd
 5248 syslog    25  10  1768  708  584 S  0.3  0.3   0:01.40 syslogd
 9250 justin    15   0 69556  13m 8884 S  0.3  5.5   0:09.64 gnome-terminal
    1 root      16   0  1564  524  460 S  0.0  0.2   0:02.74 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.09 events/0
    5 root      11  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.10 kblockd/0
    9 root      10  -5     0    0    0 D  0.0  0.0   0:00.06 kacpid
  110 root      15   0     0    0    0 S  0.0  0.0   0:00.02 pdflush
  111 root      15   0     0    0    0 S  0.0  0.0   0:00.05 pdflush
  113 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0

---

### Post by jordanmthomas on 2006-10-21
hmmm..gnome-screensaver hasn't been taking up much of your CPU time so perhaps this isn't the cause for your fans to spin up.  If you are using the computer, does it stay quiet?  

According to your CPU usage history, all seems well.  
Next time your fans start whirring, get the output of
```
uptime
``` so we can see how busy your computer has really been.

**ps, this is bothering me because I don't know what's wrong.  :(

---

### Post by woodlandjustin on 2006-10-21
Thank you very much for your interest in this problem.
First of all the latest update, and then I'll try to do what you just asked of me.

Well the fan WAS going when I was using it, as I had turned it on and was trying that post for 10 minutes with the fan still going. Later I decided to turn it off and try to clean it. So I shut down. But, it would not shutdown. I guessed it might have been too hot? Anyway it at least did try to shutwond but I had to finish it by holding the power button down. But the leds looked like it was actually in standby or something. Anyway, it'sa laptop and I tried taking the cover off the get at the dust that might be there. I could only pry the top open a bit. Anyway I blew a whole load of compressed air through every hole I could find including the pried open cover. By that time it should have been pretty damn cool at least!!

Then I came back and turned it on. Clicked on software update thing as it prompted me. It checked my sytem as usual and now says "You can install 3 updates". I have not clicked on it yet so it should be doing nothing. I do have firefox open and that is all else. And, the fan is going like crazy!!

Here is the "top" code output now. Maybe different now (I don't remember the 80.3% of cpu part before):

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5145 justin    16   0  178m  70m  21m S 80.3 28.0   6:16.55 firefox-bin
 5515 justin    15   0  2188 1000  768 R  2.0  0.4   0:00.02 top
    1 root      16   0  1564  532  460 S  0.0  0.2   0:02.72 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.10 events/0
    5 root      11  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.03 kblockd/0
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  110 root      15   0     0    0    0 S  0.0  0.0   0:00.01 pdflush
  111 root      15   0     0    0    0 S  0.0  0.0   0:00.02 pdflush
  113 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  112 root      15   0     0    0    0 S  0.0  0.0   0:00.12 kswapd0
  700 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 kseriod
 1796 root      22   0     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt
 1806 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd

Next I'll post what you asked.

---

### Post by woodlandjustin on 2006-10-21
^ above ^ is an update. And below is this "uptime" thing:

> **jordanmthomas said:**
> hmmm..gnome-screensaver hasn't been taking up much of your CPU time so perhaps this isn't the cause for your fans to spin up.  If you are using the computer, does it stay quiet?  

According to your CPU usage history, all seems well.  
Next time your fans start whirring, get the output of
```
uptime
``` so we can see how busy your computer has really been.

**ps, this is bothering me because I don't know what's wrong.  :(

~$ uptime
 16:08:46 up 28 min,  2 users,  load average: 1.25, 1.04, 0.86

Like I said fan is wherring like mad and this is immediately after my last post so above is the relevant output of "top".

---

### Post by woodlandjustin on 2006-10-21
And now I see that these screensavers though maybe not the cause, certainly don't help it. The fan was on full power while I wasn't using it just now, and there was a screensaver. As soon as I moved the mouse the screensaver dissappeared and the fan went to its less speedy mode of operation. Now (2 minutes later) it has turned off. (However it is often ON while there is no screensaver on, as I have described at length above.)
Justin

---

### Post by anaconda on 2006-10-21
> **woodlandjustin said:**
> Before I had Ubuntu I briefly had DSL (damn small linux). My machine was very quiet then. If I did nothing, the fan did not run. Actually even the other moving parts stopped! I don't know about computers but maybe there are some disks that wherr around inside? Anyway those stopped completely, so that my computer was utterly silent!! And, even if I then moved the mouse around and even clicked on other pages and browsed the internet, sometimes it would still remain utterly silent!!

DSL can be very silent, because it is often run completely from RAM, and it is also very light. When you run your os rfom ram your hd can be stopped all the time! so it will be very silent..

---

