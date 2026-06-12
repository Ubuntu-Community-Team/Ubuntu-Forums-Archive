---
title: "[SOLVED] MacBook function keys in Intrepid"
date: 2008-11-20
forum: Apple Hardware Users
---

### Post by regebro on 2008-11-20
The Wiki states you have to installed pommed to get the brightness keys working. This is clearly not the case in Intrepid anymore, as I don't have pommed installed, and it works. ;) I also tried to install pommed, and it didn't seem too do anything.

But I would like to reverse the action of my function keys, so they work as normal function keys without pressing Fn. Can I do this, and if so, should I install pommed again, or is there another way?

---

### Post by x0as on 2008-11-20
My media keys didn't work without pommed, install pommed to reverse the actiond.

---

### Post by bryonak on 2008-11-20
[Here]("http://ubuntuforums.org/showthread.php?t=964224") you go.

In short: edit the /etc/modprobe.d/options file according to that thread.
If you installed Intrepid from scratch, that should do it (rebooting might be necessary). If you upgraded from Hardy, rebuild your init ramdisk, as shown in the thread, with ```
sudo update-initramfs -u -v -k `uname -r`
```

Also note that pommed is deprecated on Macbooks

---

### Post by cyberdork33 on 2008-11-20
> **regebro said:**
> The Wiki states you have to installed pommed to get the brightness keys working. This is clearly not the case in Intrepid anymore, as I don't have pommed installed, and it works. ;) I also tried to install pommed, and it didn't seem too do anything.

But I would like to reverse the action of my function keys, so they work as normal function keys without pressing Fn. Can I do this, and if so, should I install pommed again, or is there another way?
can you link to the wiki you were following so it can be fixed?

---

### Post by regebro on 2008-11-20
It was the SantaRosa page, I've fixed it.

---

### Post by jwhite69 on 2008-12-07
I had installed mouseemu to get my trackpad to work properly (and for some reason mouseemu did not seem to fix the problem).  When I uninstalled mouseemu and rebooted, the function keys works properly on my Macbook pro and with the slim aluminum usb keyboard.

---

### Post by chongzi889 on 2008-12-08
Mud Valve is one of api 6a **[gate valve](http://www.valvesupplier.net/index.htm)**,operated by double actuated thread, and featuring tight structure. The series [gate valve]("http://www.valvesupplier.net/index.htm") had been widely used in oil field, crude exploitation

---

