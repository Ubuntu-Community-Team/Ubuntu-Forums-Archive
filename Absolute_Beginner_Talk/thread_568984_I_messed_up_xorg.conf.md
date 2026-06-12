---
title: "I messed up xorg.conf"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by cobolt01 on 2007-10-06
I messed up my xorg.conf file by trying to add the resolution 1280x1024 to the Display subsection. When restarting X server won't start and I can access the terminal. I've tried removing the changes using Vim and tried running the command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
I went through the configuration and tried to enter the most accurate information I could. X still won't run on startup. Please, please help me, there is a lot of important information on that computer and it needs to be running soon again. Once again please. Thanks in advance.:(
Feisty BTW with an ATI Raden X1200 graphics chip onboard.

---

### Post by finer recliner on 2007-10-06
try taking out the -phigh flag. i believe that flag changes what questions it will ask when reconfiguring the device (xorg in your case).

it should auto-detect most of your settings for you.

---

### Post by FuturePilot on 2007-10-06
> **finer recliner said:**
> try taking out the -phigh flag. i believe that flag changes what questions it will ask when reconfiguring the device (xorg in your case).

it should auto-detect most of your settings for you.
-phigh will autodetect everything. It only asks you what driver and resolution you want. It's much easier than going through all the steps.

---

### Post by cobolt01 on 2007-10-06
I tried running it with *-phigh* and it asked a lot of questions. I just ran it without *-phigh* and it made no diffrence to the amount of questions. X still doesn't start. There are even questions on keyboard config. Any ideas? Please! I'm desperate!

---

### Post by taurus on 2007-10-06
Do you have a Ubuntu LiveCD and can you boot/run from it?  Maybe you just need to copy xorg.conf from the LiveCD to your harddrive and see if you can X running again from your harddrive.

---

### Post by derred on 2007-10-06
Try moving the file xorg.conf to a safe location (i.e make a backup folder)
Run the "sudo dpkg -reconfigure xserver-xorg" command again.
It should atempt to build the file like it was the first time without attempting to use any old settings.
Tell us if that helps.

---

### Post by cobolt01 on 2007-10-06
yes, I do, but I've already tried editing the file to what it was with Vim text editor and it's probibaly been overwriten by the reconfigure utility. When I edit the file It did save and I'm sure the file is correct to how it was. Should I still try using the live CD?

---

### Post by cobolt01 on 2007-10-06
> **derred said:**
> Try moving the file xorg.conf to a safe location (i.e make a backup folder)
Run the "sudo dpkg -reconfigure xserver-xorg" command again.
It should atempt to build the file like it was the first time without attempting to use any old settings.
Tell us if that helps.

I'll try that, sorry I missed it because I didnt refresh intime. What is the command for move, I only know the copy command

---

### Post by derred on 2007-10-06
> **cobolt01 said:**
> I'll try that, sorry I missed it because I didnt refresh intime. What is the command for move, I only know the copy command
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

---

### Post by gigaferz on 2007-10-06
this last month i messed it up too,,,,after trying this or that....and tired of nothing working i did this...

i found out the path of  the file. restarted in safe mode  and deleted the file , I rebooted the computer and log in as usual... and it worked...... and even better cause it got me the resolution i wanted...

---

### Post by cobolt01 on 2007-10-06
I moved the xorg.conf file and ran the reconfigure command and It only asked for display resolution and card manufacturer, but X STILL won't start. This is a big problem. What could possibly be wrong? Maybe although my card is ATI it should be set as something diffrent? that's about the only diffrent option I have and it still doesn't configure it properly.

---

### Post by jingo811 on 2007-10-06
[COLOR="Sienna"][SIZE="4"]1.[/SIZE][/COLOR]
$ **nano /etc/X11/xorg.conf**

[COLOR="Sienna"][SIZE="4"]2.[/SIZE][/COLOR]
In Nano editor
**Ctrl+w** ,  
[COLOR="Sienna"]
[SIZE="4"]3.[/SIZE][/COLOR]
type in this when it asks for Search:
**section "device"**
press ENTER.

[COLOR="Sienna"][SIZE="4"]4.[/SIZE][/COLOR]
Then you should see something like this replace value for Driver into "vesa" instead of "ati".
**"vesa"**

```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection
```

[COLOR="Sienna"][SIZE="4"]5.[/SIZE][/COLOR]
**Ctrl+x**, and save your change.

[COLOR="Sienna"][SIZE="4"]6.[/SIZE][/COLOR]
Then reboot
**sudo shutdown -r now**

See what happens.

---

### Post by cobolt01 on 2007-10-06
thank you so much! That fixed it. For others reading this thread, can you tell me what *vesa* is? Is it an ati generic?

---

### Post by jingo811 on 2007-10-06
Nah VESA is the fossil of all graphics.

[http://en.wikipedia.org/wiki/Vesa](http://en.wikipedia.org/wiki/Vesa)
> The Video Electronics Standards Association (VESA) is an international body, founded in the late 1980s by NEC Home Electronics and eight other video display adapter manufacturers. The initial goal was to produce a standard for 800x600 SVGA resolution video displays. Since then VESA has issued a number of standards, mostly relating to the function of video peripherals in IBM PC compatible computers.




Try this guide to make things more specific to your graphics card.
[http://virtualseafarer.com/renaissance/allsparks/chapter6.html#ch6](http://virtualseafarer.com/renaissance/allsparks/chapter6.html#ch6)

---

### Post by derred on 2007-10-06
I just assumed he was using fglrx. Shows how little I thought  ahead.](*,)](*,)](*,)

---

