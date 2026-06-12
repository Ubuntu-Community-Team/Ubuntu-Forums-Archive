---
title: "What command do I need for this problem???"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by edcouch on 2008-02-12
Hello folks, the onboard video on my motherboard packed it in, so I installed a PCI video card, and now when it boots, it stays in DOS, and I get a promp for the username and then password, and when I put these in it then gives me a command prompt.  But..... I haven't got a clue what to type in as a command.  I am assuming that  it can't find my new video card, so I will have to point it in that direction so that the operating system can pick it up,.  
Can anyone please tell me "EXACTLY" what is is I need to type in as a command?

Thanks in advance!

---

### Post by oilchangeguy on 2008-02-12
> **edcouch said:**
> Hello folks, the onboard video on my motherboard packed it in, so I installed a PCI video card, and now when it boots, it stays in DOS, and I get a promp for the username and then password, and when I put these in it then gives me a command prompt.  But..... I haven't got a clue what to type in as a command.  I am assuming that  it can't find my new video card, so I will have to point it in that direction so that the operating system can pick it up,.  
Can anyone please tell me "EXACTLY" what is is I need to type in as a command?

Thanks in advance!

First, DOS died with Windows ME. That was Microsoft's last operating system layered on top of DOS. So your computer is not running in DOS. What else did you do to it, besides add a video card?

---

### Post by dstew on 2008-02-12
I think you are looking at the login and command line of a linux shell. You will have to reconfigure your video display system. After you log in, enter the command```
sudo dpkg-reconfigure xserver-xorg
```and answer the questions the best you can. After that, enter```
startx
```and see if you get a display.

---

### Post by Dr Small on 2008-02-12
Try reconfiguring Xorg:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

And then start X11 with:
```
startx
```

---

### Post by edcouch on 2008-02-12
Thanks for your replies!  Obviously I don't know what I am doing, but I am trying.  I did what you said dstew, and it says xserver not installed.  then I rebooted it and now it comes up to a command that says root#    and I entered my usual password but that doesn't do it.  I guess i will just have to reload the OS, or do you have any other suggestions?
Thanks again!

---

### Post by brokenhachi on 2008-02-12
when it says root# you have to type "login" then you can enter your username and password. (i think)

---

### Post by edcouch on 2008-02-12
Thanks very much guys but I think I will just have to re-load the OS.  It would be great if i knew something about writing code, but unfortunately.............

---

