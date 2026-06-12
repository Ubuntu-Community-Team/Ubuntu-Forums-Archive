---
title: "System Locking up"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by trafferty on 2008-02-05
I have a new Install of 7.1. My system continually locks up after 15 to 20 minutes. Should I reinstall? the boot process seems to take a long while also and I am not able to get NTP installed. I know I'm new to Ubuntu (my first time with a Linux based OS) I would really appreciate some help.

---

### Post by pieisgood4589 on 2008-02-05
What are your computer specs? :lolflag:

---

### Post by trafferty on 2008-02-05
I apologise, I do know better. I have a Dell Latitude 610, Pentium M 1.6, 2gb memory. Do you need more?

---

### Post by oedha on 2008-02-05
hehehe....right....
you have to mention the specification of your computer.
this will be help to check it :==> lshw -short
type it on terminal

---

### Post by trafferty on 2008-02-05
system         Computer
/0                     bus            Motherboard
/0/0                   memory         2027MB System memory
/0/1                   processor      Intel(R) Pentium(R) M processor 1.60GHz
/0/100                 bridge         Mobile 915GM/PM/GMS/910GML Express Process
/0/100/1               bridge         Mobile 915GM/PM Express PCI Express Root P
/0/100/1/0             display        M22 [Mobility Radeon X300]
/0/100/1c              bridge         82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Ex
/0/100/1c/0    eth0    network        NetXtreme BCM5751 Gigabit Ethernet PCI Exp
/0/100/1d              bus            82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UH
/0/100/1d.1            bus            82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UH
/0/100/1d.2            bus            82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UH
/0/100/1d.3            bus            82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UH
/0/100/1d.7            bus            82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 E
/0/100/1e              bridge         82801 Mobile PCI Bridge
/0/100/1e/1            bridge         PCI6515 Cardbus Controller
/0/100/1e/1.5          communication  PCI6515 SmartCard Controller
/0/100/1e/3    eth1    network        PRO/Wireless 2200BG Network Connection
/0/100/1e.2            multimedia     82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 
/0/100/1e.3            communication  82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 
/0/100/1f              bridge         82801FBM (ICH6M) LPC Interface Bridge
/0/100/1f.2            storage        82801FBM (ICH6M) SATA Controller
/0/100/1f.3            bus            82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus 
tom@Ubuntu-laptop:~$ 
Thanks

---

### Post by emarkd on 2008-02-05
You've got plenty of hardware to run Ubuntu.  That's not the issue.  Is there a particular app that may be related to this?  Have you tried running 'top' to see if a particular app is running away with your resources?

PieIsGood:  It's an absolute beginner's forum.  Of course it's full of noobs.  And surely you don't expect people to read the instructions before posting!?! ;) This forum is much better than some I've participated in.  Just take a deep breath. :)

---

### Post by trafferty on 2008-02-05
Thanks emarkd. I was pretty sure the hardware could handle it. I don't know that "top" is though. Today is my first crack at this OS. I do understand Pieisgood though, I hate it when users ask questions and don't include the necessary info to figure out what is going on.

---

### Post by Linux_Man on 2008-02-05
I know this may seem ovious, but you have removed the Live-CD from your computer when you boot it up, because that could lead to the above problems and even I sometimes forget to remove the CD when installing a new distro.

---

### Post by emarkd on 2008-02-05
Top is just that.  In the terminal, run

```
top
```

That will show you how much resources each process on your system is using.  If you can see one process get out of control before the lock-up, you've then got a target to shoot at for a fix.  You could just start it in a terminal and let it sit there and run as you use the system.

---

### Post by trafferty on 2008-02-05
Yes the disk is out. I will say this is the longest time I have been able to without a freeze up. The only thing that is different is I plugged in a usb mouse.

---

### Post by trafferty on 2008-02-05
Thanks again emarkd. I ran it and nothing looked like it was hogging resources. though I'm not have any problems at the moment. I'll keep an eye on it.

---

### Post by Michl on 2008-02-05
I've run Feisty, Gutsy and Heron on a Dell CS610.
If boot-up takes a long time, look at this file:
/etc/usplash.conf

and see if the resolutions match the maximum your monitor can handle.
I found that after a fresh install of Gutsy, this was set too high for
my monitor and that's what slowed down boot-up.  If the xres and
yres settings are wrong, edit the file and then you have to update
usplash.  If this is your problem, holler and I'll give more details.

Michael

---

### Post by Michl on 2008-02-05
> **pieisgood4589 said:**
> ANGRY VERSION-
Holy mother of God, if I see one more comment without all the details (for you, your specs would be nice) I'll disband these forums out of frustration. Read the rules! NOOB

NICE VERSION-
What are your computer specs? :lolflag:

This really is a red herring or just hot air.  You know how many 
problems people have here of this sort, especially with Gutsy and
only a small percentage has to do with the fact that they are running
some old machine that can't handle ubuntu.  Better to ask for more 
detail on what was done when it froze or when exactly does the 
boot-up take a long time and so on.   From my experience, this
forum has always had a friendly tone and I hope this tradition
continues.

---

### Post by trafferty on 2008-02-05
Michael he resolution looks ok I would think x=1248, and y=1024. It may be a bit hight I'll try lowering it .
Thanks

---

### Post by trafferty on 2008-02-05
Michael I was mistaken. the max resolution for this screen is 1024x768. I tried to change that file but was not able to. How do I go about editing this file.

---

### Post by Michl on 2008-02-05
> **trafferty said:**
> Michael I was mistaken. the max resolution for this screen is 1024x768. I tried to change that file but was not able to. How do I go about editing this file.

Ok what you do is this.  You can edit with nano of gedit.  With gedit it
goes like this.  In the terminal enter
```
sudo gedit /etc/usplash.conf
```
You will enter your password.

This is a simple file, but still a good idea to save a back-up.
So then go to File -> Save as and edit the name to 
usplash.conf_backup

After you saved a back_up file, do this again:
```
sudo gedit /etc/usplash.conf
```
and this time edit the resolutions and do not make
any other changes.  xres will be 1024 and yres 768.
Save the file and close gedit.

The in the terminal enter:
```
sudo update-usplash-theme usplash-theme-ubuntu
```

wait for the update to finish.  Next time you reboot, it will go alot
faster assuming you have the wrong resolution now.

---

### Post by trafferty on 2008-02-05
Thank you Michael. I'll reboot and let yo know how it goes.

---

### Post by trafferty on 2008-02-05
WOW that was definitely faster. Thank you very much. I guess I only have one more thing to deal with for the moment. I cannot reset my clock. When I try and try and change from manual to internet time I get a message saying I need to install NTP Support. I try that and nothing happens.

---

### Post by Michl on 2008-02-05
> **trafferty said:**
> WOW that was definitely faster. Thank you very much. I guess I only have one more thing to deal with for the moment. I cannot reset my clock. When I try and try and change from manual to internet time I get a message saying I need to install NTP Support. I try that and nothing happens.

I remember having trouble here too but I can't remember what it was.
So you install NTP and then go to Administration -> Time and Date.  I 
Configure manually, set the time, and synchronize now.  Then
I set it back to the internet server and choose a few.  Then close.  I
think then you need to reboot to have time change in the panel.  I am
guessing here because I stumbled into the right answer.  Maybe
someone will give a better answer.

---

### Post by trafferty on 2008-02-05
I have the Time showing correct now. Thank you all for your help today. I look forward to learning a lot more about this OS.

---

