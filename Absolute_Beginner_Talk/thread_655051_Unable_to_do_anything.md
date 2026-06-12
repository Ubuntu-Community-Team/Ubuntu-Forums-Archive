---
title: "Unable to do anything"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Armithius on 2007-12-31
I just finished installing Ubuntu 7.10 on my 64-bit machine using an alternate CD. The install went fine, no problems there. It starts up alright, but right after the loading screen, I get a screen that says

   *Starting anac(h)ronistic cron anacron                                             [OK]
   *Starting deferred execution scheduler atd                                     [OK]
   *Starting perodic command scheduler crond                                    [OK]
   *Checking battery state...                                                               [OK]
   *Running local boot scripts (/etc/rc.local)                                        [OK]
_

Here's a (terrible) screenshot if it helps (apologies for the large image): [http://img147.imageshack.us/img147/6545/ubuntuscreenlg7.jpg]("http://img147.imageshack.us/img147/6545/ubuntuscreenlg7.jpg")

And it just sits there. I don't know if I'm supposed to type something in there or what, but everything I've tried to type in has yielded no results. There's no actual prompt, so I'm not terribly surprised. I wonder if something in my machine isn't compatible somehow? Any help you guys can give me would be greatly appreciated.

---

### Post by Sef on 2007-12-31
1) What are your system specs?

2) What is your system specs?  (When I have seen that, it has been a problem with my video card.  For some reason it can't find the drivers for it.)

---

### Post by Armithius on 2007-12-31
Processor: AMD Athlon(tm) 64 Processor 3200+, ~2.0GHz
Memory: 1022MB RAM
Hard Drive: Western Digital 160 GB
Video Card: ATI Radeon X1300 Series
Monitor: ViewSonic E70fb
Sound Card: SB Audigy 2 ZS Audio [B000]

---

### Post by Sef on 2007-12-31
Do you have the same problem if you use recovery mode?  (When the computer first starts up, press esc to get into the grub boot menu.)

---

### Post by PmDematagoda on 2007-12-31
Your problem Armithius is most likely a problem with the X-Server configuration. When you reach the end of the normal boot of Ubuntu, press Ctrl+Alt+F1 to get you to a tty, once there, execute:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

After the reconfiguration is complete, execute:-
```
sudo /etc/init.d/gdm start
```

That should restore the GUI.

---

### Post by Armithius on 2007-12-31
No dice. Seems it can't see my graphics card, as was suggested earlier...

---

### Post by PmDematagoda on 2007-12-31
> **Armithius said:**
> No dice. Seems it can't see my graphics card, as was suggested earlier...

I thought that was the case. I would have been able to help, but I have very little experience concerning ATi cards. I hope you are able to solve the issue quickly, good luck:).

---

### Post by Armithius on 2007-12-31
Thanks. A friend of mine was able to help, so I'm all set now.

Thank you everyone.

---

### Post by LunaMouse on 2007-12-31
> **Armithius said:**
> Thanks. A friend of mine was able to help, so I'm all set now.

Thank you everyone.

*[hugs]*

It was worth it to get you on Linux.

---

### Post by PmDematagoda on 2007-12-31
> **Armithius said:**
> Thanks. A friend of mine was able to help, so I'm all set now.

Thank you everyone.

Seems like my hope that you would solve your issue quickly, worked:D.

---

