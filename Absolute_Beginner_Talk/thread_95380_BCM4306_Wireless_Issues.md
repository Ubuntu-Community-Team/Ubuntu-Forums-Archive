---
title: "BCM4306 Wireless Issues"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by j0sh3rs on 2005-11-26
I just installed Ubuntu 5.10 onto my Gateway 7320GZ notebook, and I'm getting a couple of different issues.  Keep in mind, I'm a quick learner, but I don't know anything about Ubuntu.

So, I have no wlan0 in my ifconfig.  I've got lo and eth0.  That's it.  I took a look at this after viewing other parts of these here forums.

My bios says it's active, my light's on, Device Manager shows that i've got a Boradcom BCM4306 adapter, but doesn't assign it a device type or capabilities.  Really the only way I can get online with this laptop is via a wireless connection.  I'm on my Windows Desktop now, and can transfer files easily.

Also, I'm not getting any sound, though it shows the system has already identified my audio controller.

Any suggestions?

---

### Post by ShakingSpirit on 2005-11-26
First, install the wireless driver 'wrapper', which will let you use your windows drivers under linux (It's on the CD :)) (All lines beginning with '$' should be typed into Applications -> Accessories -> Terminal. Not insulting your intelligence, just makling sure you understand what I'm getting at ;))
```
$ apt-get install ndiswrapper-utils
```

Then make a folder to keep the drivers in
```
$ sudo mkdir /opt/wireless
```

You say you have a notebook, which probably means you don't actually have the CD with the drivers on >_< Try looking at the manufacturer's website for them; you'll need the .inf file and the .sys file (and sometimes a .bin too, but that's not required).
If you DO have a cd, mount it, find where they're hiding, and copy them to the folder. 
```
$ sudo cp /media/cdrom/your/wireless/drivers/driver.inf /opt/wireless/
$ sudo cp /media/cdrom/wireless/drivers/driver.sys /opt/wireless/
```

If not, put them in your home folder (/home/yourusername/, or you can get to it from Places -> Home Folder), and do
```
$ sudo cp /home/yourusername/driver.inf /opt/wireless/
$ sudo cp /home/yourusername/driver.sys /opt/wireless/
```

That's the hard part done :)
Next, run
```
$ sudo ndiswrapper -i /opt/wireless/driver.inf
```

Hopefully, that shouldn't give any errors :) Check that it's working by typing:
```
$ ndiswrapper -l
```
It should give you an output saying that 'driver present, hardware present'

If that's all good, you can run;
```
$ sudo ndiswrapper -m
```

This will tell the kernel that ndiswrapper is all how you want it, and ready to be loaded on your command. That command is;

```
$ sudo modprobe ndiswrapper
```

If all goes well, you should now have a wlan0 device under System -> Administration -> Network.
If you encountered a problem (which is much more likely due to my frequent typos and forgetfulness :(), post with as much detail as you can and we'll try and sort it :)

Sound is a differant issue >_< Wireless first, sound later :)

---

### Post by j0sh3rs on 2005-11-27
Wireless works great! You're amazing.  Thanks a ton.

Now, the sound? Any ideas?

Thanks again.

---

