---
title: "Network printer. Ubuntu to Ubuntu"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by MockY on 2007-05-08
I have no idea why network printing has to be a major pain in the rear end. I just installed Feisty on my girl's computer and everything works just fine. I share the printer and then try to add it to my laptop. That;s a no go. Before when she had Windows, the printer was automatically found when it scanned the network, but now I have to manually enter the direct path to the shared printer. That is really stupid to be honest and there is absolutely no reason why it wouldn't be possible to be able to scan for available printers on the network. But then again, printing has always been a hassle in Linux and it doesn't seem to change. 

So until then I guess I have to be without a printer on the laptop or install Windows on a computer just so I can print.

---

### Post by kosmic on 2007-05-08
The reason is that the printer manager is not allowed to public is services in the LAN.

Go to -> System -> Administration -> Printers

and then choose (Global Configuration)
and then choose Share Printers (or something like that in this menu) "sorry my menu is in Portuguese.

After that it should be easy to add printers by just searching your network.

Also if you have a Firewall don't forget to open port 631 ;)

Hope it helps

---

### Post by MockY on 2007-05-08
I made sure I did have the global settings active before posting. But via Add Printer on my Laptop, there is no option of scanning the network. Nor is the printer automatically detected.

---

### Post by H.E. Pennypacker on 2007-05-08
Sharing a printer between two Ubuntu computers should take you less than five minutes.  Please see this post:

[http://ubuntuforums.org/showpost.php?p=1525340&postcount=2](http://ubuntuforums.org/showpost.php?p=1525340&postcount=2)

---

### Post by MockY on 2007-05-09
Worked just fine (the command is even stated when adding the printer), however I was wondering why there were no browse function. I mean, wouldn't it make more sense if you had a browse button and every available printer showed up? Entering the path to the printer is not really user friendly (though not specifically hard). So this is something the Ubuntu team should implement in 7.09. It just makes sense that way.

---

