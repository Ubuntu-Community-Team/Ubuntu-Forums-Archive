---
title: "How to enable visual effects of ubuntu on ATI video card ???"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by guevara on 2008-03-05
Hi guys, I'm new on Ubuntu. I liked Ubuntu. And but i gotta problem like can't enable visual effects.
I'm running Toshiba A135-S2356 laptop and ATI Radeon Xpress 200M. 
i installed my graphics card through restricted drivers manager and everything runs great, but when i go to "system > prefrences > appearance" and then go to "visual effects" and try to enable them, i get a message that says: "The Composite extension is not available" I want to enable visual effects.

Thank you.

---

### Post by wolfen69 on 2008-03-05
i highly doubt that your video card will do 3D well. i have the x300, and it doesnt look good. enjoy linux for what it does well.

---

### Post by CloudFX on 2008-03-05
I too am unable to enable visual effects. I have a Radeon X1270... is this not good enough?

---

### Post by sumeet_sageer on 2008-03-05
HI all,
  I have the same problem here. I have a ATI Radeon 9800 Pro. This option was working but now it is not. If I try to enable Normal or Extra, I get the error message "The Composite extension is not available" I have also tried reinstalling the ATi drivers by using "sudo apt-get install linux-restricted-modules-generic restricted-manager-kde". But no avail. Any help in this would be great. 

Thanks
Sumeet

P.S. I have noticed that Visual effects work with the ATI driver disabled in Restricted Drivers Manager. Seems to be the only temp solution.

---

### Post by MasterJS on 2008-03-05
Have any of you tried installing XGL? Its basically another layer of the XServer that allows compositing but takes away direct rendering. It works great on my ATI card. By the way, mine is the exact same graphics card as the orignial poster.

---

### Post by jw5801 on 2008-03-05
```
sudo apt-get install xorg-driver-fglrx
sudo apt-get install xserver-xgl
```

Then reboot and it should work fine!

---

### Post by CloudFX on 2008-03-06
giving that a go now. the first one was already updated for me, but the second wasn't. Hope it works!

---

### Post by Laughed on 2008-03-06
> **jw5801 said:**
> ```
sudo apt-get install xorg-driver-fglrx
sudo apt-get install xserver-xgl
```

Then reboot and it should work fine!

Will this help ATI users who get a blank screen after start up??? 

I will probably be able to answer my own question in an hour as I am re-installing ubuntu as I type this and I know I am going to be faced with this problem.

---

### Post by CloudFX on 2008-03-06
Don't bother! I got it working, with full capabilites doing what he said! I also have my ATI video card enabled int he restricted drivers.

---

### Post by jw5801 on 2008-03-06
> **Laughed said:**
> Will this help ATI users who get a blank screen after start up??? 

I will probably be able to answer my own question in an hour as I am re-installing ubuntu as I type this and I know I am going to be faced with this problem.

Depends what you mean by blank screen at bootup? Like the splash screen not displaying properly? That's a known bug with gutsy I believe. I think it's linked to using a vga=xxx boot setting, the bug report for which is [here](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910). There is a fix in the comments on that bug report for the blank ttys. I personally don't display the splash screen, so I'm not sure if that will fix it. Installing the driver and Xgl certainly won't though, that will only have an impact once the X session is running, splash screens and the like need to display prior to X starting.

---

### Post by Laughed on 2008-03-06
I've ran those command lines with no success but I seem to have a different issue.

jw5801: I am not sure but it doesn't sound like the aprticular bug you've outlined. What is tty? Ubuntu won't load for me at all. At startup I get 2 lines (something about the kernel loading and its parameters) and then my monitor tells me there is no signal and the pc hangs idle. I get no response from hitting escape or any combination of ctrl, alt, or f1-12 keys. Ive waited as long as an hour with no change.

---

### Post by jw5801 on 2008-03-06
> **Laughed said:**
> I've ran those command lines with no success but I seem to have a different issue.

jw5801: I am not sure but it doesn't sound like the aprticular bug you've outlined. What is tty? Ubuntu won't load for me at all. At startup I get 2 lines (something about the kernel loading and its parameters) and then my monitor tells me there is no signal and the pc hangs idle. I get no response from hitting escape or any combination of ctrl, alt, or f1-12 keys. Ive waited as long as an hour with no change.

Hmm... interesting. tty's are the virtual consoles you get by pressing Ctrl+Alt+F1-6. I think the two issues are linked, they're both to do with non-X graphics displaying.

So when you're trying to boot you get to grub (or to the screen asking you to hit Esc to enter the grub menu), then the kernel attempts to load and aborts? Try booting using the failsafe kernel options (should be the second in the grub menu) and see if it gets you any further. Then we can assess from there. If you could jot down whatever the output when it fails is that would be really helpful too.

---

### Post by Laughed on 2008-03-06
> **jw5801 said:**
> Hmm... interesting. tty's are the virtual consoles you get by pressing Ctrl+Alt+F1-6. I think the two issues are linked, they're both to do with non-X graphics displaying.

So when you're trying to boot you get to grub (or to the screen asking you to hit Esc to enter the grub menu), then the kernel attempts to load and aborts? Try booting using the failsafe kernel options (should be the second in the grub menu) and see if it gets you any further. Then we can assess from there. If you could jot down whatever the output when it fails is that would be really helpful too.

Well, I am not really sure if its aborting as I am not getting an error message. I am not sure how to determine if it is failing, as soon as I try to boot up regularly my screen shuts off. If I turn it back on it times out from the lack of a signal and shuts back off. 

If I run the 2nd option (recovery console) I can get to the root command line with no visible errors and perform various tasks, but my knowledge of Linux consists of:

cd /etc/X11
cp xorg.conf xorg.conf_backup
nano xorg.conf
shutdown -r now or
reboot
dpkg-reconfigure xserver-xorg

As you can see I am very green.

---

### Post by Laughed on 2008-03-06
I did it. I win. I was working off your hunch that my issue was related to the bug you mentioned, and I found this thread: [http://ubuntuforums.org/showthread.php?t=454392](http://ubuntuforums.org/showthread.php?t=454392)
I used the code provided in the second post, and chose vga=ask

It than asked me to chose either a mode or to scan. I chose scan which showed me more options and I went with the second one which was actually (1).

Success. Booted right up. 

Thanks man for putting me on the right path.

/me drops a few thank yous on jw5801

---

### Post by jw5801 on 2008-03-06
That's ok. None of those things are going to help you if you're not getting anywhere near an X session. From your root console, if you run:
```
su <your-user-name> #switch from root to your account
startx
```
You should be able to get into a graphical environment where you're more comfortable. Then I think we need to have a look at grub. So if you could post your /boot/grub/menu.lst here, that would help. Then if we could get outputs from ```
sudo fdisk -l
```
I think that's all that springs to mind at the moment.

---

### Post by Laughed on 2008-03-06
> **jw5801 said:**
> That's ok. None of those things are going to help you if you're not getting anywhere near an X session. From your root console, if you run:
```
su <your-user-name> #switch from root to your account
startx
```
You should be able to get into a graphical environment where you're more comfortable. Then I think we need to have a look at grub. So if you could post your /boot/grub/menu.lst here, that would help. Then if we could get outputs from ```
sudo fdisk -l
```
I think that's all that springs to mind at the moment.

First your right, it didn't fix my problem. I rebooted and was right back to square one.

Your probably not gonna be happy.
I  ran entered "su <myname>" and hit enter
the root hash changed to name@ubuntu:/root$

I entered "startx" and hit enter getting: 
xauth: creating new authority file /home/myname/.serverauth.4574
X: user not authorized to run the X server, aborting.
xinit: Server error.

I entered "sudo fdisk -l" and hit enter
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: oxae4fcad6

Device             Boot     Start                   End                    Blocks           ID         System
/dev/hdc1          *              1                  4665              37471581          83          Linux
/dev/hdc2                    4666                  4870                1646662+         5          Extended
/dev/hdc5                    4666                  4870                1646631          82         Linux swap /  Solaris     

it also shows the parameters for my sata XP drive but I doubt you need that.

I don't know where I went wrong with the startx cmd but I hope the rest helps.

---

### Post by jw5801 on 2008-03-06
Hmm... interesting! I thought one could run an X server as the user. Anyway, if you run startx as root then it'll work. I'd be more inclined to su to yourself and then run "sudo startx". There may also be a way to run gdm (gnome display manager: your graphical login), I'll have a look and get back to you. Other than that, what's the output from:
```
cat /boot/grub/menu.lst
```

EDIT: So it's actually really easy to get to X from a root terminal. Simply run "gdm" and you should get your familiar login screen! (Unless you're running KDE in which case use "kdm"). There might be a few errors, like dbus not running correctly but we should be able to correct those. It's almost certainly an issue in your grub options though, so post the output from above and we'll have a look-see.

---

### Post by robertchahine on 2008-03-09
i put the commands in terminal and rebbot the machine, it works normal and amazing.
thank you jw5801

---

