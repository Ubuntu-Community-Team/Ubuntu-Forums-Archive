---
title: "Final Hurdle to Moving away from Vista"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by flub on 2007-10-26
Hi,

I've been playing with the latest Ubuntu and I absolutely love it. I'm running it on a dual-boot Vista PC but there are a couple of things I need to work out/find solutions for before deleting MS forever. There are a couple of programs that I'm having a hard time working out/finding a Linux equivalent for.

Hope some of the great people here can offer up some ideas/solutions for the following programs? Any Linux substitute ?

**[COLOR="Gray"]1) URL Snooper[/COLOR]**
I do a lot of packet sniffing to extract FLV and other mediums from Flash sites to extract the raw movie streams. URL Snooper is a great Windows utility that shows me the low-lever stream info. 

*ANSWER: Wireshark is a packet sniffer/network monitor, works great for me* Thanks Loganm10

**2) PDF Fill. **
I often have to merge multiple PDF files together and PDF Fill is a great Windows util

**[COLOR="Gray"]3) FLV/AVI Conversion[/COLOR]**
I often need to convert AVI and FLV files to and from each other. 

*ANSWER : FFMPEG will do this, no problem. In fact most of your windows based ones are still just using a GUI over mencoder or FFMPEG to do the work. I normally just use command line, but I'm sure others can point you to some GUI implementations in Linux for these two.* Thanks KCPokes


**[COLOR="Gray"]4) Video Editing[/COLOR]**
I need to be able to perform very basic video editing of AVI files to join clips together and add titles etc.

*ANSWER:  Avidemux2 is a video editor, Ive never really used it much myself but I hear good things* Thanks Loganm10

**5) Replay Media Catcher**
This tool automatically downloads the underlying WMV, FLV files from most sites.

*ANSWER: youtube-dl is a console based app that can download the flv files off of youtube, works great, I dont know if it works on other sites tho* Thanks Loganm10

**6) AutoHotKey**
This is as far as I'm aware a windows only utility that allows me to create Text Macros so that when I hit a combination of keys eg   SIG*  it replaces the SIG* with the text that I have set up, in this case my Signature

**7) MOZY**
I currently use MOZY to perform all my backups online with the Free version of Mozy. Any solutions similar for Ubuntu?

**[COLOR="Gray"]8) VirtualBox[/COLOR]**
I've not looked into this so there maybe an easy solution, but I run Virtualbox and a number of old OS like W2K and XP etc Does virtualbox work on Ubuntu and can I load vista inside it?

*ANSWER: Absolutely. It is in the repositories and works well. I've ran it both ways, at work using XP as the host, and at home using Ubuntu as the host.* Thanks KCPokes


Thanks in advance and hope to get a few solutions for the above applications

Cheers :)

---

### Post by KCPokes on 2007-10-26
> **flub said:**
> 
3) FLV/AVI Conversion
I often need to convert AVI and FLV files to and from each other. 


FFMPEG will do this, no problem.  In fact most of your windows based ones are still just using a GUI over mencoder or FFMPEG to do the work.  I normally just use command line, but I'm sure others can point you to some GUI implementations in Linux for these two. 

> **flub said:**
> 
8) VirtualBox
I've not looked into this so there maybe an easy solution, but I run Virtualbox and a number of old OS like W2K and XP etc Does virtualbox work on Ubuntu and can I load vista inside it?


Absolutely.  It is in the repositories and works well.  I've ran it both ways, at work using XP as the host, and at home using Ubuntu as the host.

---

### Post by flub on 2007-10-26
Thanks you very much, I'll update the OP to show progress :)

---

### Post by flub on 2007-10-26
Just giving myself a little bump to hopefully get a couple more answered

---

### Post by loganm10 on 2007-10-26
1. Wireshark is a packet sniffer/network monitor, works great for me

4. Avidemux2 is a video editor, Ive never really used it much myself but I hear good things

5. youtube-dl is a console based app that can download the flv files off of youtube, works great, I dont know if it works on other sites tho

All of those programs are available in the software repositories

---

### Post by flub on 2007-10-26
Thanks very much, I'll update the post and check them out. I have a feeling that the youtube one is fairly basic and won't capture stuff from other sites that have the video embedded inside SWFs etc but I'll check it out.

Appreciate the help.

---

### Post by segalion on 2007-11-12
For autohotkey:
try 
[http://ldtp.freedesktop.org/wiki/](http://ldtp.freedesktop.org/wiki/)
and 
[http://xmacro.sourceforge.net/](http://xmacro.sourceforge.net/)

---

### Post by peabody on 2008-02-18
> **segalion said:**
> For autohotkey:
try 
[http://ldtp.freedesktop.org/wiki/](http://ldtp.freedesktop.org/wiki/)
and 
[http://xmacro.sourceforge.net/](http://xmacro.sourceforge.net/)

Also, mind if I plug my own program autokey?  Link is in my sig.  It doesn't do everything autohotkey does, but it does do hotstring expansion.

---

### Post by commonplace on 2008-03-03
For Mozy, how about [Spideroak]("http://spideroak.com")?

Disclaimer: I haven't tried it, but plan on doing so soon. It's at least worth looking into, I'd think, as it's very similar to Mozy I believe.

/Kevin

---

