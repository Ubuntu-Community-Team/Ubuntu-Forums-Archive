---
title: "Cannot increase screen resolution"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Bubtottle on 2007-07-27
Hello

The screen resolution on my computer has changed to 640x480. I find this very annoying as I am used to a much, much higher resolution. I know that the computer and screen both support much higher resolutions as I used to have them at a high resolution. A lot of guides I have found tell me to edit the xorg file but I am worried to do so as the guides are quite vague about what exactly to change. Any help in increasing my screen's resolution would be very welcome.

I am using an Nvidia graphics' card and fiesty fawn.

---

### Post by jingo811 on 2007-07-27
I had the same Nvidia problem some days ago.....one maoment plz.....	#-o

---

### Post by Smu on 2007-07-27
Try this:

1. Ctrl + Alt + F1
This will open upp a non-graphical session. To get back to the gnome-desktop and your current session -> Ctrl + Alt + F7

2. Login
3. sudo dpkg-reconfigure xserver-xorg
4. fill in the information of your monitor
5. Ctrl + Alt + F7
6. Ctrl + Alt + Backspace (restart x)


Worked for me when I had problems with my resolution...

---

### Post by Wiz74 on 2007-07-27
Yep I have a 8800GTS and have been playing around trying to get 3d working correctly and have had to do what Smu just posted heaps of times tonight alone, however it works everytime :)

---

### Post by vanadium on 2007-07-27
According to a tip I have seen on a Dutch forum, you should first install xresprobe before going ahead. It seems that due to a bug that the graphical installation of Ubuntu does not install xresprobe, which is needed for dpkg-reconfigure to properly recognize the properties of your card. Search the package in synaptic and install it (or issue "sudo apt-get install xresprobe" at the command prompt.

A second command I want to add is, before you go ahead, make a backupcopy of your xorg.conf (actually, I believe that dpkg-reconfigure makes a backup itself with the name xorg.conf.date). If your x-server does not start anymore, then simply copying the backup over to xorg.conf will resolve this situation.

---

### Post by jingo811 on 2007-07-27
Now I'm starting to remember.  Just follow the rabbit.  [COLOR="Red"]You better write them down on paper you won\t be having Desktop when you do them!!!![/COLOR]
_Step 1_
[B]
1.)[/B]
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

**2.)**
```
sudo /etc/init.d/gdm stop
```

**3.)**
Ctrl+ Alt+ F1

**4.)**
User login first!

**5.)**
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

**6.)**
```
sudo /etc/init.d/gdm start
```

IF 
Your keyboard gets all weird and shuffled, then do this to fix it back.
System > Preferences> Keyboard> _Layouts_
ELSE
I'll give you instructions for _Step 2_ and _3_ to further heal your PC.  Just say when!

---

### Post by stinger30au on 2007-07-27
i have a few pc's running thru a KVM switch, one of which is my desktop Ubuntu Fiesty. (have a laptop running it as well)

I have noticed that if i boot it up and dont select it on the KVM till it has fully booted, im limited to 640x480.

If i reboot the machine and leave it selected on the KVM i can get all my screen resolutions as normal.

---

### Post by coffeecat on 2007-07-27
> **stinger30au said:**
> I have noticed that if i boot it up and dont select it on the KVM till it has fully booted, im limited to 640x480.

If i reboot the machine and leave it selected on the KVM i can get all my screen resolutions as normal.

**Bubtottle**, this is important. I'm glad someone mentioned it. Before you try any of the other very helpful suggestions, make sure the monitor is connected as you boot up. This is not necessarily a kvm issue. If you've forgotten to switch the monitor on the same thing will happen. If xorg can't detect a monitor (in Ubuntu - in some other distros this is not so) it will default to 640x480.

This caught me out exactly the same way as stinger30au. Oh, the joys of KVM switches. :( :wink:

---

### Post by Bubtottle on 2007-08-03
vanadium, thanks, I was just wondering, how do I copy the backup over to xorg.conf?

---

### Post by Bubtottle on 2007-08-03
Okay, problem is fixed now but I am confused...

I lost X (hence my question about how to use the backup) and so was waiting for an answer and playing around on the command line (playing music). 

Then the command line changed. Rather than having the normal user@computername thingie that it has, it came up with only >. I pressed Ctrl Alt F7 then Ctrl Alt F1 but it was still the same. I could not do anything at all on this new command line thing and so turned the computer off in the hope that it would help.

When I turned the computer back on, it went straight to the X login screen and now works fine at a good resolution. I am just curious as to why this has happened so suddenly.

One other thing is that the refresh rate of the monitor is 60 Hz and I would like it to be higher (75 would be good). However, if this is too difficult/risky, I'll think I'll stay at 60 Hz.

Thank you to everyone who helped, though.

---

### Post by Bubtottle on 2007-08-03
Actually, I've just found that the computer is not back to normal... nvidia driver is not installed anymore. Can someone please tell me how to safely and easily install it? I can't remember how I did it last time.

---

