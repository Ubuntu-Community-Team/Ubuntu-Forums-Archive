---
title: "100% CPU while browsing web"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by rene100 on 2006-07-25
OK I have noticed that my ubuntu loads fast,  but as I use it, it gets slower and slower and slower over time until it is painful

I'm on a laptop with 2ghz mobile pentium 4-m, and 1 GB of ram (i have turned off swap) and  a radeon 9000 32mb video card, with 3d accel working under mesa3d.  I'm running Ubuntu dapper 686

When I'm browsing the web, my cpu constantly jumps to 100% and even now that I'm just typing its hovering around 50%

All I have open is terminal, a PDF, System monitor and Firefox with 2 tabs

(I've noticed in XP firefox will hog up my CPU after it's been running for too long and I have several tabs open, but nowhere near as fast as it's happening in Ubuntu)

Furthermore, if I close Firefox on Ubuntu my system still crawls, (unlike in windows where it seems to fix the problem)

---

### Post by rene100 on 2006-07-25
in fact, I don't think it's just web browsing.. almost anything I.   do seems to eat up way more CPU than it should..  Radar screensaver was 50%, maximizing a window makes the cpu jump to over 90%...

---

### Post by cantormath on 2006-07-25
> **rene100 said:**
> OK I have noticed that my ubuntu loads fast,  but as I use it, it gets slower and slower and slower over time until it is painful

I'm on a laptop with 2ghz mobile pentium 4-m, and 1 GB of ram (i have turned off swap) and  a radeon 9000 32mb video card, with 3d accel working under mesa3d.  I'm running Ubuntu dapper 686

When I'm browsing the web, my cpu constantly jumps to 100% and even now that I'm just typing its hovering around 50%

All I have open is terminal, a PDF, System monitor and Firefox with 2 tabs

(I've noticed in XP firefox will hog up my CPU after it's been running for too long and I have several tabs open, but nowhere near as fast as it's happening in Ubuntu)

Furthermore, if I close Firefox on Ubuntu my system still crawls, (unlike in windows where it seems to fix the problem)

I have improved my cpu usage when browsing with swiftFox browser. 
its suppose to be specific to the cpu.  I installed it using automatix.
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)
automatix is a script that lets you install a bunch of stuff you might want that people always seem to have a problem with.

---

### Post by s_h_a_d_o_w_s on 2006-07-25
Try 

top

in terminal to see whats sucking up your cpu.

---

### Post by rene100 on 2006-07-25
I did a page refresh and captured the top screen.  I thought it was firefox, but surprisingly it was Xorg eating up most of the CPU

top - 11:29:40 up 11:40,  2 users,  load average: 1.33, 1.20, 1.26
Tasks:  84 total,   2 running,  82 sleeping,   0 stopped,   0 zombie
Cpu(s): 85.1% us,  9.7% sy,  0.0% ni,  0.0% id,  0.0% wa,  5.2% hi,  0.0% si
Mem:   1034384k total,   864700k used,   169684k free,    77688k buffers
Swap:   618460k total,        0k used,   618460k free,   445164k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4370 root      25   0 76072  25m 8632 R 60.4  2.6 122:13.87 Xorg
21981 rene      15   0  112m  48m  20m S 22.6  4.8   5:32.24 firefox-bin
 6253 rene      16   0 36000  13m 9.8m S  8.7  1.4  67:10.66 gnome-system-mo
 5166 rene      15   0 46076  13m 8984 S  2.2  1.4   0:13.45 gnome-terminal
22903 rene      16   0  2200 1044  832 R  2.2  0.1   0:00.68 top
 4525 haldaemo  17   0  2008  856  756 S  0.7  0.1   0:21.52 hald-addon-stor
 4859 rene      15   0  8676 3740 2976 S  0.7  0.4   0:02.51 gnome-vfs-daemo
 4906 rene      15   0 34528  11m 8116 S  0.7  1.1   0:05.71 mixer_applet2

---

