---
title: "First time user---Kernel Panic frustration!"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by Magnus150 on 2006-08-17
Hello, first time Linux user here. My friend refered me to Ubuntu when I mentioned I wanted to try Linux. I've heard good things and am eager to try it myself...Buut, there is a problem. Before setup even starts, soon after I click the install on the boot menu, I get a Kernel Panic. It is like this for all distros i've tried. I've reburned the ISO twice, checked the CD, and am now considering hardware issues. I run a customized Dell 2350, 1 gig ram, 9200 radeon SE, 2.2g p4. It's not much, but it holds me over. I did not know exactly what to copy down in relation to the kernel error, other then "Kernel Panic - Not Syncing:Fatal Exception in Interrupt." I did however take a shot of the exact error screen I recieve. Any help would be appreciated as I would really love to get out of windows! I have a hard drive seperate from my windows drive and it's all ready. Thanks for the help!

EDIT: Woops!
[http://s77.photobucket.com/albums/j50/magnus150/?action=view&current=100_0891.jpg&refPage=&imgAnch=imgAnch1](http://s77.photobucket.com/albums/j50/magnus150/?action=view&current=100_0891.jpg&refPage=&imgAnch=imgAnch1)

---

### Post by zxee on 2006-08-17
Have you tried running the live cd. I ask that because this could be a kernel bug for some laptops with a sata drive. If that is the case, and I'm not certain it is, you could still install and run from a usb thumb drive. You can look here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) for various install methods. I would recommend trying a live cd if that runs it may be a bug or you might need to use special boot parameters from the installer start screen to get it to install. (use the function keys to see boot options)

---

### Post by Magnus150 on 2006-08-17
I've tried using the live CD, it gives me the same error when trying to boot from memory. Both setup and live give this, as I am using a livecd at this very moment. I'm considering possible hardware incompatibilites. The harddrive is not SATA and the computer is a desktop.

---

### Post by zxee on 2006-08-17
> as I am using a livecd at this very moment
I'm not sure what you mean by that? How and which live cd are you using?
Take a look at boot parameter options (the link is to the knoppix cheatcodes but some of them will work with ubuntu) [http://www.kernel.org/pub/dist/knoppix-dvd/knoppix-cheatcodes.txt](http://www.kernel.org/pub/dist/knoppix-dvd/knoppix-cheatcodes.txt)

---

### Post by confused57 on 2006-08-17
> **zxee said:**
> I'm not sure what you mean by that? How and which live cd are you using?
Take a look at boot parameter options (the link is to the knoppix cheatcodes but some of them will work with ubuntu) [http://www.kernel.org/pub/dist/knoppix-dvd/knoppix-cheatcodes.txt](http://www.kernel.org/pub/dist/knoppix-dvd/knoppix-cheatcodes.txt)

I'm not sure what it does, but I've seen some people use **noapic** as a boot parameter option to correct kernel panic for their system.

---

