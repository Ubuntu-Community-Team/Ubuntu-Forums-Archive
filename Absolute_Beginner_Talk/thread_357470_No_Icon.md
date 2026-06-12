---
title: "No Icon"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by heatrag on 2007-02-09
My usb memory card reader worked plug and play fine, and now it dosn't, where should I look and why. Due to my ineptitude a memory card was the only way I could connect, and now that's denied me. :( Thanks

---

### Post by neilp85 on 2007-02-09
Run the following command and then plug in your USB memory card reader:
```
tail -f /var/log/messages
```
When you plug it in you should see some messages about where it is mounted. This will most likely be something like /dev/sr0. When you figure out where it is mounted you next want to run this command:
```
sudo mount /dev/<mount point> <path to where you want files mounted>
```
Now you should have access to your files.

---

### Post by heatrag on 2007-02-10
Thanks for that. I did what you said but I didn't know how to refer to the desktop. So you'll be horrified as to how I resolved the problem, I rebooted the whole system. It had a glitch with the shut down comand anyway and as I've been only up and running with it a couple of days had nothing to loose. Seems ok now. I've an aufull lot to learn I think.

---

### Post by neilp85 on 2007-02-11
If you make your mount point /media/<some name> nautilus should automatically add an icon to your desktop with a link to the files.

---

