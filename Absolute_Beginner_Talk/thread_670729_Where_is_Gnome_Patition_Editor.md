---
title: "Where is Gnome Patition Editor"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-01-17
Okay, I'm sure I'm just missing something here, but here goes. I want to install Tiny XP on a separate partition and I'm sure I could just do it with XP's formatter on the boot part of the CD. I downloaded a program called Gnome Partition Editor. I CAN'T FIND IT! Is it under accessories? NO! is it under Administration? NO! After checking those places, I figured, okay I'll look for it using "Search for Files" N-O-T-H-I-N-G. I checked add/remove programs to make sure I downloaded and installed it. The lil thing is checked so I guess I did. In the update they should make it so that add/remove programs shows you the location path for what you just installed, because i've had this problem before. The only difference is that I actually found what I was looking for before bpplicationsy using "Search for files". So if someone could kindly point me into the direction of finding this app. I would be most appriciative. Untill then I'm going to start with the highest level heiarchy that I'm aloud to access and begin my hunt. Thank you.

---

### Post by dcstar on 2008-01-17
> **whoscheesemine said:**
> Okay, I'm sure I'm just missing something here, but here goes. I want to install Tiny XP on a separate partition and I'm sure I could just do it with XP's formatter on the boot part of the CD. I downloaded a program called Gnome Partition Editor. I CAN'T FIND IT! Is it under accessories? NO! is it under Administration? NO! After checking those places, I figured, okay I'll look for it using "Search for Files" N-O-T-H-I-N-G. I checked add/remove programs to make sure I downloaded and installed it. The lil thing is checked so I guess I did. In the update they should make it so that add/remove programs shows you the location path for what you just installed, because i've had this problem before. The only difference is that I actually found what I was looking for before bpplicationsy using "Search for files". So if someone could kindly point me into the direction of finding this app. I would be most appriciative. Untill then I'm going to start with the highest level heiarchy that I'm aloud to access and begin my hunt. Thank you.

Install the **gparted** package.

---

### Post by whoscheesemine on 2008-01-17
> **dcstar said:**
> Install the **gparted** package.

I'm pretty sure I did, here's a Screen shot.

[http://www.geocities.com/lookin4busstop/Screenshot.jpg](http://www.geocities.com/lookin4busstop/Screenshot.jpg)

---

### Post by p_quarles on 2008-01-17
Run this in the terminal:
```
gksudo gparted
```
Note that you cannot edit mounted drives, so if you're altering the table of the drive on which Ubuntu is installed, you'll need to get the Gparted Live CD.

---

### Post by whoscheesemine on 2008-01-17
> **p_quarles said:**
> Run this in the terminal:
```
gksudo gparted
```
Note that you cannot edit mounted drives, so if you're altering the table of the drive on which Ubuntu is installed, you'll need to get the Gparted Live CD.

okay, i still would like to know how to access this program though.


so are you saying that I should use the gparted off of the Ubuntu CD i have?

....oh i got ya now, how can i edit a partition i'm currently using... that was very dumb of me, i'm goin gto do that now  thanks you, also though for future reference i WOULD like to know where this program is located. this way i may edit a partition that i am currently NOT using.

---

### Post by p_quarles on 2008-01-17
The program is located in your /usr/bin directory (like most programs). 

You can add it to the menu by creating a new launcher, and using the above command in the new item.

---

### Post by jonny5tails on 2008-01-17
On your:lolflag: top panel - System/Administration/Partition Editor...

---

### Post by whoscheesemine on 2008-01-18
> **jonny5tails said:**
> On your:lolflag: top panel - System/Administration/Partition Editor...

yeah.... lol

I've got a new problem now though. It's happened to me about three times now. I'm not sure if I should create a new thread for it or not, but we're kind of on the subject. Feel free to delete this if you'd like (like you need my permission :lolflag: ).

Every single time I set up a new partition for a Windows operating system. Lets say like 10gb. Then I format it with windows (I've done it twice with Windows XP professional and right now I'm dealing with it for Tiny XP). After I reboot my machine windows grabs my boot real quick so that I can't select which operating system I'd like to boot. Well, this time I popped in the live CD and went into the patition manager and saw that the Windows partition was flagged as boot. So I figured, hey perhaps if I change it so that my Ubuntu partition has the flag as boot rather than the Windows partition, I'll get that nifty little menu in the beginning that lets me choose which operating system to boot. So I did that, and then the manager crashes. Come to find out anytime I change the boot flag to any partition it crashes. Yet, still it miraculously has changed the flag for me after the crash. I did it a few times to make sure. I have included a screen shot for better interpretation. By the way I meant the program crashes not the OS. Anyhow, I reboot my laptop hoping that it would work... and what happens? "Operating System not found" uggg, so I tried flagging the swap sector just in case and I get similar messages. My only idea is to back up my /home folder and reinstall Ubuntu like I did the other two times, but this time I'd like to actually understand the problem and know how to fix it with out having to reinstall the system. When it comes to working on computers your number one priority is making sure the data is safe. Plus, I really want to get to know the in's and out's of this operating system. Any help would be greatly appreciated.

[http://www.geocities.com/lookin4busstop/Screenshot654.jpg](http://www.geocities.com/lookin4busstop/Screenshot654.jpg)

---

### Post by nikoPSK on 2008-01-18
> **jonny5tails said:**
> On your:lolflag: top panel - System/Administration/Partition Editor...

hehe, word of advice, just run the command in the terminal if your not sure where the app is located. :)

---

### Post by whoscheesemine on 2008-01-18
> **nikoPSK said:**
> hehe, word of advice, just run the command in the terminal if your not sure where the app is located. :)

What command is that exactly?

Also, love the ghost quote in your sig lol...

*Usage of a stem pack* "ahhh... that's the stuff"

---

### Post by nikoPSK on 2008-01-18
usually, the command is obvious, say for firefox, it's "firefox". To find the command if you don't know it, just drag the shortcut from the menu somewhere right click it, properties, launcher tab then paste the command in. :)

---

### Post by stchman on 2008-01-18
> **whoscheesemine said:**
> Okay, I'm sure I'm just missing something here, but here goes. I want to install Tiny XP on a separate partition and I'm sure I could just do it with XP's formatter on the boot part of the CD. I downloaded a program called Gnome Partition Editor. I CAN'T FIND IT! Is it under accessories? NO! is it under Administration? NO! After checking those places, I figured, okay I'll look for it using "Search for Files" N-O-T-H-I-N-G. I checked add/remove programs to make sure I downloaded and installed it. The lil thing is checked so I guess I did. In the update they should make it so that add/remove programs shows you the location path for what you just installed, because i've had this problem before. The only difference is that I actually found what I was looking for before bpplicationsy using "Search for files". So if someone could kindly point me into the direction of finding this app. I would be most appriciative. Untill then I'm going to start with the highest level heiarchy that I'm aloud to access and begin my hunt. Thank you.

Gparted is included on the LiveCD by default.  When you install Ubuntu it is not installed.  You will need to intall it the following way.

```
sudo apt-get -y install gparted
```

Once this is done you can get to it by going to System--->Administration--->Gnome Partition Editor

---

### Post by mdsmedia on 2008-01-18
> **nikoPSK said:**
> usually, the command is obvious, say for firefox, it's "firefox". To find the command if you don't know it, just drag the shortcut from the menu somewhere right click it, properties, launcher tab then paste the command in. :)
If you have a shortcut in the menu, why would you be looking for the command to use in Terminal? Usually the reason for using the command, as in the OP's situation, is because he can't find it in the menu....a little catch 22??

---

