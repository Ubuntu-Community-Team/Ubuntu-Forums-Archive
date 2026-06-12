---
title: "Problems with installing drivers for Linux"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by Sparkl on 2006-12-04
So, I have installed Windows XP. From there I've downloaded Linux drivers for my Ati graphic card. But i don't know how to install it! Can please somebody help me?

---

### Post by Tomosaur on 2006-12-04
What's the extension of the file you downloaded?

---

### Post by Josh1 on 2006-12-04
Why would you need linux drivers for windows xp?

---

### Post by Tomosaur on 2006-12-04
> **Josh1 said:**
> Why would you need linux drivers for windows xp?

He hasn't, he just used WinXP to download them.

---

### Post by Sparkl on 2006-12-04
No, I'm using it to download drivers for Ati graphic card.

So, i have downloaded it with extension .run

---

### Post by Tomosaur on 2006-12-04
1) Open up the terminal.
2) Change to the directory where the downloaded file is (using the cd command).
3) Let's say your download is called 'atiDriver.run'. You would type 'chmod +x atiDriver.run'. This makes the file executable.
4) Type './atiDriver.run' to run the file. From there on it should explain everything for you.

---

### Post by Sparkl on 2006-12-04
Lol, this question will definetly be VERY n00bish...

I'm a beginner with Linux, so I must ask you - how to change the directory? and where?

---

### Post by Tomosaur on 2006-12-04
Well, technically you don't need to even touch the command line here, you just need to know where the file downloaded to. It's most likely that it will be either in your home directory, or on your desktop. If you can see it on your desktop, you need to right-click it, then click 'Properties', then 'Permissions'. You then need to check the 'Execute' box near the bottom. Click apply/ok, then just double click the file. If you get a message asking you what to do, click 'run in terminal', or just 'run'.

If it's not on your desktop, click 'Places' then 'Home Folder'. You need to go hunting :P Once you've found it you can follow the same procedure as above.

---

### Post by Sparkl on 2006-12-04
hmmm, I forgot to mention - I didn't install Linux yet, cos I must install those drivers first, becouse theyre "blocking" me the instalation - that's how my friend told me...](*,) 

Can I even install those driverse on XP, or do I have to do it in Linux?

---

### Post by Tomosaur on 2006-12-04
Uhhh, no. To install linux drivers, linux needs to be installed. Your friend has no idea what he's talking about. What exactly is the problem with your installation?

---

### Post by Sparkl on 2006-12-04
I had a thread about this before, but I still didn't solve the problem. SO, the problem is: When I boot the CD (original copy of 64bit 6.06LTS Linux Ubuntu), I click on the option Start or install Ubuntu. The first step is completed, but then, it shows me na error about server X (my graphical interface). It says, that it might be not configured coretcly, and before I proceed with the instalation, I must configure this server... But I don't know how... So, I went to the nearby computer shop, and they told me, that I need to install drivers for Linux, and it should be instalated normally... So, that's the story why am I trying to install those damn drivers...:-D

---

### Post by Henry Rayker on 2006-12-04
Which ATI card are you using? I have never heard of this problem, despite seeing many many users with ATI cards.

I have a couple words of advice. First, I wouldn't install the 64bit version, as there is very little, application-wise, available for it. You'll end up doing a lot of work getting the 32b versions of apps to run in the 64bit version than is really necessary. Second, I would consider trying the alternate cd. I believe this one gives you more options as well as feedback during your installation.

One last thing is...if you can run the live cd, it displays the desktop fine and everything, your problem probably (99%) isn't the drivers.

---

### Post by Tomosaur on 2006-12-04
Haha, well unfortunately you cannot install the drivers if linux is not already installed. You could try installing Ubuntu and THEN installing the drivers. Either way, I assume you want to keep Windows, in which case your best bet it to set up your partitions from within Windows, and then booth the linux CD to install.

---

### Post by Sparkl on 2006-12-04
So...

I have the Ati Radeon X800RX

But the problem about the 64 bit version is, that I have the 32bit version, but it is 5.04... And if I would try to download the 32bit version of ubuntu 6.06 or 6.10, it would take weeks.... I have very slow internet, you know...:-|

---

### Post by Sparkl on 2006-12-04
I don't want to keep Windows... Becouse it has became boring...:-D 

I already have two partitions formated in FAT32 sistem, but it's no use...:-| :-|

---

### Post by Tomosaur on 2006-12-04
Ah well, you'll either need to download 32 bit dapper or edgy and try those out. You got any friends with broadband who'll let you use their connection? I think canonical still does shipit, but again they'll take weeks to come to, so it's just a matter of biting the bullet and picking a method :) Linux with low-speed internet is a pain in the neck really.

---

### Post by Henry Rayker on 2006-12-04
Well, to be honest, I think you're going to need the alternate cd, regardless. They don't ship that version of the cd, so you may be out of luck. If you can't install the OS first, you can't install the drivers. If the OS refuses to install because of an Xserver problem, then you have a big problem.

---

### Post by Sparkl on 2006-12-04
My conection is 256kb/64kb, but I would like to switch to VDSL... But still it will take too long to download Linux... I think...

---

### Post by Sparkl on 2006-12-04
> **Henry Rayker said:**
> Well, to be honest, I think you're going to need the alternate cd, regardless. They don't ship that version of the cd, so you may be out of luck. If you can't install the OS first, you can't install the drivers. If the OS refuses to install because of an Xserver problem, then you have a big problem.

Hmmm... What kind of a big problem? I have been trying to solve it but it's no use... 

Well, I've been thinking, my schoolmate told me, that Nvidia has better support for Linux... Is it maybe something wrong with my graphic card? Otherwise, I will sell this graphic card and buy Nvidia... What do you think?

---

### Post by Tomosaur on 2006-12-04
nVidia is more likely to work with the live CD, yes, but that means you're spending money on linux (noooooooooooooooo :P). Anyway, you can switch graphics cards and give it a go, sure. I still say you may aswell just stick one of the later versions on to download and give it a whirl. It won't take THAT long.

---

### Post by Sparkl on 2006-12-04
Heh, you're right...

But I'm still concered about Henry Rayker's post... What kind of a big problem? It looks like it's big, cos nobody has ever heard of that kind of problem...

Arrgghhh... Why meeee...:confused: :confused: :confused:

---

### Post by Tomosaur on 2006-12-04
Well, the liveCD is designed to be compatible with tons of hardware configurations. If you can't get the GUI to work with the liveCD, you may well not be able to get it working even if you manage to get Ubuntu working. However, you ARE using an older version of Ubuntu LiveCD, which is why you should get a later version and see if that works.

---

### Post by Sparkl on 2006-12-04
hmmm... I've found a Linux version 32bit 5.04 for Intelx86...

When I try to install that version, it doesn't shows me any error about serverX... Now it's trying to tell me that "no partitionable media was found, and that I must check if a hard disk is attached on the computer"...Wtf??!!!!?:confused: :confused: 

What can I do now???

Maybe should I try to download 6.10 version?

---

### Post by Henry Rayker on 2006-12-04
Well, the thing is, your live cd will boot to desktop, right? This means your graphics card is just fine. It works okay with the video driver that the live cd defaulted to.

Before you do anything else, I think you need to try the alternate cd installation. It should ask you some questions (such as who makes your video card, etc).

I have read about some people having issues with things working in the live cd but not working at boot (usually wireless cards, though), so you may be facing an issue like that (live cd sees that you have the ati card, loads the proper driver; installation sees that you have an ati card and it isn't compatible with the default driver and throws a flag)...but that's all speculation.


EDIT:
As for the new error, did you say you wanted to set up your partitions yourself, or let it do it? If you chose the latter, it may have seen that you have partitions on your entire disk and it can't create a new partition.

---

### Post by Sparkl on 2006-12-04
hmmm, I'lll try to do that...

About the Live CD... That is the problem too... When i try to launch the Live CD version 6.06 it loads me the needed things, and then the screen shuts down, like if computer would go to sleep mode... I'm beginning more and more concered, that maybe it's the graphic card, which is not running properly...

---

### Post by Henry Rayker on 2006-12-04
Wait...I thought you said the live CD booted to the desktop and when you tried to install (via double-clicking install), it cleared the first portion, but crashed after that...

---

### Post by Sparkl on 2006-12-04
No... I was trying to tell you, that I boot the instalation CD, and then I install Linux (just like Windows...)... And then it shows me that error... And the same way is with Live CD, only that the screen shuts down.

---

### Post by Henry Rayker on 2006-12-04
Ohhhhh. Okay. I'm sorry. I completely misunderstood. This changes a little, but if 5.04 will get past the Xserver config, then your card isn't at issue, it's the 6.06 version of Ubuntu and your system.

---

