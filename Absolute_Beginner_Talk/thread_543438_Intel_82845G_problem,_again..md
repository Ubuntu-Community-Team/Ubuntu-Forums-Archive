---
title: "Intel 82845G problem, again."
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by ricky 07 on 2007-09-05
Right, umm, over the past few weeks I've been having a play with Ubuntu 7.04, but there has been one issue that has niggled with me the whole time. The screen resolution is in 640x480. I've looked and looked all over the forums and haven't been able to find a solution for my laptop because most have been Dell issues, an EI System 4411 which is basically a rebadged Advent and has the Intel 82845G card. I know this has been done to death but before I install next to my Vista, I want to get 1024x768 up and running. I really like Ubuntu and I want to use it or Kubuntu but both have the same problem. I have VERY little experience of Linux so I'd prefer it if people went that tiny bit slower with me. If someone tells me what commands to use though, I can do that using Terminal.

Thanks.

A very puzzled user. :confused:

---

### Post by sharke on 2007-09-05
> **ricky 07 said:**
> Right, umm, over the past few weeks I've been having a play with Ubuntu 7.04, but there has been one issue that has niggled with me the whole time. The screen resolution is in 640x480. I've looked and looked all over the forums and haven't been able to find a solution for my laptop because most have been Dell issues, an EI System 4411 which is basically a rebadged Advent and has the Intel 82845G card. I know this has been done to death but before I install next to my Vista, I want to get 1024x768 up and running. I really like Ubuntu and I want to use it or Kubuntu but both have the same problem. I have VERY little experience of Linux so I'd prefer it if people went that tiny bit slower with me. If someone tells me what commands to use though, I can do that using Terminal.

Thanks.

A very puzzled user. :confused:
This is not usually hard to fix . i  think you will have a dell xs260 graphics controller controlling your intel card and usually dell sets it up with a 1 mb vifeo cache . If you now howto get into the bios you can change this setting to maximum which gives 8 mb and all your resolution problems should be fixed.

Regards
Sharke

---

### Post by ricky 07 on 2007-09-05
> **sharke said:**
> This is not usually hard to fix . i  think you will have a dell xs260 graphics controller controlling your intel card and usually dell sets it up with a 1 mb vifeo cache . If you now howto get into the bios you can change this setting to maximum which gives 8 mb and all your resolution problems should be fixed.

Regards
Sharke

Thanks for your help, I should have mentioned that I am quite experienced in Windows and know how to do the BIOS etc. Unfortunately, there was no option to change it to 8MB when I checked. Advent is usually quite a bargain bucket brand of PC and it's usually dirt cheap here in the UK. This particular model only cost £299 so I'm not sure that is the graphic controller you mention. Well Device Manager in Windows says 'Intel 82845G/GL Graphics Controller'.

---

### Post by abhilash82 on 2007-09-05
Can you post your xorg.conf file that you can find at /etc/X11/?

---

### Post by ricky 07 on 2007-09-05
> **abhilash82 said:**
> Can you post your xorg.conf file that you can find at /etc/X11/?

Sure, I'll just boot into Ubuntu and post it from there.

Hmm, I have no network connection in there so it may take a slight bit longer.

---

