---
title: "USB device problems"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by Yadda on 2007-12-24
Hello there, I am a new user of Ubuntu and so far everything has been very smooth, The only hitch I've hit so far is that I can't seem to get non-drive USB devices to work. Specifically my iPod and my Ti-89 ti. When I plug either in nothing happens, I've tried disk mode for the iPod. I have GTKPod installed but no luck there I also have TiLP (synching for Ti calculators) installed. Given that both of these aren't working and that everything is in place I'm thinking that I'm missing something quite basic with regards to how USB works under linux. Any help would be greatly appreciated.

Thanks

---

### Post by spydon on 2007-12-24
Try ```
lsusb
``` in the terminal when you have the devices plugged in just to see if they show up.

---

### Post by deadgobby on 2007-12-24
[https://help.ubuntu.com/community/PortableDevices/iPod?action=show&redirect=IPodHowto](https://help.ubuntu.com/community/PortableDevices/iPod?action=show&redirect=IPodHowto)

---

### Post by Yadda on 2007-12-24
Hey there, thanks for the help. I'm feeling pretty retarded at the moment. The trick to getting the iPod to mount was to put it in disk mode first and *then* plug it in to the computer. I was doing it the other way... The calculator is still a no-go though. Using lsusb I was able to see that the computer does see that the calculator is plugged in but TiLP doesn't see the calculator. The documentation for TiLP says something about permissions but I circumvented that (I think) by running the program as root.

Thanks!

---

