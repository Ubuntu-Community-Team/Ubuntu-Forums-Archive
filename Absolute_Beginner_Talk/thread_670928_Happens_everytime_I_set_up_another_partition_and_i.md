---
title: "Happens everytime I set up another partition and install Windows..."
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-01-18
Every single time I set up a new partition for a Windows operating system. Lets say like 10gb. Then I format it with windows (I've done it twice with Windows XP professional and right now I'm dealing with it for Tiny XP). After I reboot my machine windows grabs my boot real quick so that I can't select which operating system I'd like to boot. Well, this time I popped in the live CD and went into the partition manager and saw that the Windows partition was flagged as boot. So I figured, hey perhaps if I change it so that my Ubuntu partition has the flag as boot rather than the Windows partition, I'll get that nifty little menu in the beginning that lets me choose which operating system to boot. So I did that, and then the manager crashes. Come to find out anytime I change the boot flag to any partition it crashes. Yet, still it miraculously has changed the flag for me after the crash. I did it a few times to make sure. I have included a screen shot for better interpretation. By the way I meant the program crashes not the OS. Anyhow, I reboot my laptop hoping that it would work... and what happens? "Operating System not found" uggg, so I tried flagging the swap sector just in case and I get similar messages. My only idea is to back up my /home folder and reinstall Ubuntu like I did the other two times, but this time I'd like to actually understand the problem and know how to fix it with out having to reinstall the system. When it comes to working on computers your number one priority is making sure the data is safe. Plus, I really want to get to know the in's and out's of this operating system. Any help would be greatly appreciated.

[http://www.geocities.com/lookin4busstop/Screenshot654.jpg](http://www.geocities.com/lookin4busstop/Screenshot654.jpg)

EDIT: For the Moderators: Your spell check is telling me that the word "Every" is spelled wrong and it offers no spelling suggestions. Just thought you'd like to know as this is an open source community and all.

---

### Post by jleaker01z on 2008-01-18
Rather than a dual boot, have you considered installing Windows into a virtual machine within Ubuntu?  If you have decent enough hardware it might simplify matters for you somewhat.

---

### Post by whoscheesemine on 2008-01-18
That is a very good idea, but I'm looking to not take such a toll on my System resources, especially since the main reason I'm portioning for XP is for gaming. Very good idea, and if I had the dream machine I wish I had I'd go along with that. Nonetheless, I still would like to further understand my current problem as well as learn a solution for future reference.

---

### Post by x02flash on 2008-01-18
> **whoscheesemine said:**
> Every single time I set up a new partition for a Windows operating system. Lets say like 10gb. Then I format it with windows (I've done it twice with Windows XP professional and right now I'm dealing with it for Tiny XP). After I reboot my machine windows grabs my boot real quick so that I can't select which operating system I'd like to boot. Well, this time I popped in the live CD and went into the partition manager and saw that the Windows partition was flagged as boot. So I figured, hey perhaps if I change it so that my Ubuntu partition has the flag as boot rather than the Windows partition, I'll get that nifty little menu in the beginning that lets me choose which operating system to boot. So I did that, and then the manager crashes. Come to find out anytime I change the boot flag to any partition it crashes. Yet, still it miraculously has changed the flag for me after the crash. I did it a few times to make sure. I have included a screen shot for better interpretation. By the way I meant the program crashes not the OS. Anyhow, I reboot my laptop hoping that it would work... and what happens? "Operating System not found" uggg, so I tried flagging the swap sector just in case and I get similar messages. My only idea is to back up my /home folder and reinstall Ubuntu like I did the other two times, but this time I'd like to actually understand the problem and know how to fix it with out having to reinstall the system. When it comes to working on computers your number one priority is making sure the data is safe. Plus, I really want to get to know the in's and out's of this operating system. Any help would be greatly appreciated.


As far as selecting what to boot from, you may have a quick boot system, especially if your laptop is a Toshiba, like mine.  So next time, instead of changing the flagging, hold F12 (check the manual if for the key if it's a quickboot) as soon as the system starts up and you should be able to choose the right partition that way, at least that's how it worked for me until I went single OS with linux

---

### Post by whoscheesemine on 2008-01-18
Well, I'll try the f12 thing right now, but I already turned off quick boot in my BIOS. I have a Dell Latitude D520. Also, even if it is quick boot, when I set the boot flag to XP it boots XP, but when I set the boot flag to Ubuntu, it says operating system not found. I don't beleive the problem is related to quick boot. Still looking for a solution to the problem not an alternative,

---

### Post by jleaker01z on 2008-01-18
Ah well, I dont have the experience there to help.  I switched about 8 months ago just to rid myself of windows.  I just accepted the restrictions on my gaming to whatever works with Wine or Cedega, or Linux native games.  Good luck .I'm sure there will be someone along shortly that can answer your questions.

---

### Post by lordofchaos1984 on 2008-01-18
WINDOWS MUST BE INSTALLED FIRST FR A SUCCESSFUL DUAL-BOOT. Ubuntu's boot manager (GRUB) can automatically detect Windows and set itself up properly to boot both

---

### Post by whoscheesemine on 2008-01-18
> **lordofchaos1984 said:**
> WINDOWS MUST BE INSTALLED FIRST FR A SUCCESSFUL DUAL-BOOT. Ubuntu's boot manager (GRUB) can automatically detect Windows and set itself up properly to boot both

Ah that's a bummer, so is there a method I can take to fix my issue, or am I doing to have to reinstall Ubuntu? Although I was thinking about trying Kubuntu, it seems cooler, and alot of the applications I was installing were from the KDE package, plus I'd like to try another desktop environment. It will also give me some cross knowledge, I know this is off the subject and I'll create another thread to answer this one as well, but what are all the major differences between Kubuntu and Ubuntu....

My main question is still the priority though, is there any method I can take to successfully dual boot now, or am I going to be forced to reinstall Ubuntu..?

My third tiny question is if I back up my /home folder in Ubuntu, am I going to be able to replace it with the home folder in Kubuntu? If not what folders do I need to back up to replace in Kubuntu?

---

### Post by whoscheesemine on 2008-01-18
> **x02flash said:**
> As far as selecting what to boot from, you may have a quick boot system, especially if your laptop is a Toshiba, like mine.  So next time, instead of changing the flagging, hold F12 (check the manual if for the key if it's a quickboot) as soon as the system starts up and you should be able to choose the right partition that way, at least that's how it worked for me until I went single OS with linux

Yeah my BIOS is set for a thorough boot, btw, f2 for me brings me to my BIOS and f12 brings up a boot menu, not the boot menu i want though, this one just lets me select cd drive or hd or netboot and the such...

---

