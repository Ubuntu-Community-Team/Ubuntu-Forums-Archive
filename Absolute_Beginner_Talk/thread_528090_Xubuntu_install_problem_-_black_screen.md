---
title: "Xubuntu install problem - black screen"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by kudos1uk on 2007-08-17
Hi all hope you can help, I have been trying without asking but now really stuck.

Trying to put xubuntu onto a sony vaio c1 laptop which is currently running (badly) XP.

I only have a USB cd rom which is not supported at boot.

So I tried to follow this for a HDD install:

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

I did section "The CD approach" but after the menu and I sellect ubuntu I just get a black screen.

I did:

1, Burnt the alterative CD and copied its contents to a new file called ubuntu on the c drive root.
2, Downloaded grub_for_dos-0.4.1pre22.tar.gz and extracted grldr to my c drive root (not sure if I should heve created a file called grldr and put it in there?)
3, added c:\grldr="Install Ubuntu" to the end of boot.ini
4, created a text file with notebook called menu.lst saved to c drive root with the following contents:
title Install Ubuntu
kernel   (hd0,0)/ubuntu/install/vmlinuz root=/dev/ram0 devfs=mount,dall ramdisk_size=17000
initrd   (hd0,0)/ubuntu/install/initrd.gz


I'm sure I have just done something stupid but please can anyone offer any help.


I did also fine this, but not sure if it helps and I dont really understand it, it also migh be my next setback!
[https://answers.launchpad.net/ubuntu/+question/11356](https://answers.launchpad.net/ubuntu/+question/11356)

---

### Post by oilchangeguy on 2007-08-17
please advise your computers specs, and the version of ubuntu you're using.

---

### Post by kudos1uk on 2007-08-17
Thanks,

Xubuntu 6.06.1 Dapper Drake using alternate install

Using the above due to the Vaio spec:

Sony VAIO C1VE PC Notebook
128 MB SDRAM
Processor: Transmeta Crusoe TM5600 600 MHz 
40GB HDD

Thanks Tony

---

### Post by kudos1uk on 2007-08-17
inside c:/ubuntu/install/ is:
mt86plus
readme.sbm
sbm.bin

has that got anything to do with it?

> 4, created a text file with notebook called menu.lst saved to c drive root with the following contents:
title Install Ubuntu
kernel (hd0,0)/ubuntu/install/vmlinuz root=/dev/ram0 devfs=mount,dall ramdisk_size=17000
initrd (hd0,0)/ubuntu/install/initrd.gz

---

### Post by gn2 on 2007-08-17
If you have access to another laptop, you could put the Sony's hard drive into it, install Ubuntu, then put it back in the Sony and run "sudo dpkg-reconfigure -phigh xserver-xorg"

Never tried it myself but I believe it works.

---

### Post by kudos1uk on 2007-08-17
I do have another laptop and a USB enclosure, could you give me some advice on how to go about this, would I be able to keep the dual boot?

Thanks Tony

---

### Post by gn2 on 2007-08-17
Don't attempt using the USB enclosure that will just complicate matters.

Just put the drive in the other laptop and set up a dual-boot, then remove the drive** and put it back in the Sony**, boot into Ubuntu and run the command in my last post. More info on the Hermanzone link in my sig.

Like I said before I've never done it myself but I've read it can be done.

---

### Post by kudos1uk on 2007-08-17
Ah, I'm with you now. So long as I don't allow Windows to boot this should work. 
I will give it a go tomorrow (might have to be Sunday) and report back.

Thanks again.

---

### Post by kudos1uk on 2007-08-17
I gave this a shot tonight.

I got it all going OK but after setting the video I'm getting into a loop a white screen the back to command prompt and after a number of loops it stops for a while then starts again.

I do get a chance to put things righ between these loops but don't know what to do.

Help.

---

### Post by kudos1uk on 2007-08-18
I'm in real trouble now.

I did "sudo dpkg-reconfigure -phigh xserver-xorg" again and chose ATI as it's "ATI Technologies Inc 3D Rage P/M Mobility"

I'm now getting a flashing screen that wont stop 

I can see a desktop in the backgroud but its flashing and scrowling too much to do anything with, I can just make out a mouse pointer.

Please, how can I get out of this.

Edit: I can boot in safe to root but don't really know what to do then?

---

### Post by gn2 on 2007-08-18
> **kudos1uk said:**
> 

Edit: I can boot in safe to root but don't really know what to do then?

Run the reconfigure command again and select "vesa" as the graphics driver.
.
This should get you going until you can install the correct ATI driver.
.
ATI drivers can be problematic.... Don't know how as I don't have any ATI kit.

---

### Post by kudos1uk on 2007-08-18
Many thanks gn2 thats got me started.

I think this might be able to help me with my Sony.

[http://www-jcsu.jesus.cam.ac.uk/~mma29/c1/#graphics](http://www-jcsu.jesus.cam.ac.uk/~mma29/c1/#graphics)

Need to do lots of reading up now.

Thanks for your help.

Tony

---

### Post by gn2 on 2007-08-18
> **kudos1uk said:**
> 

Need to do lots of reading up now.



Indeed, it's time spent learning that's the route to Linux success.

Glad you're sorted :)

---

