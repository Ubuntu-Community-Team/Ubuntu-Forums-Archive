---
title: "how do I access my digital camera?"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by travm on 2007-10-14
This kind of sucks, My install of ubuntu broke my xp installation, which is kind of ok because i didnt have anything on it, and all my perhipherals work, except my camera.  
it is a canon powershot a410.  
i connect it, it does nothing.  Do I need to install something to make it work?
Here is my output from lsusb
```
Bus 004 Device 002: ID 0ace:1211 ZyDAS 802.11b/g USB2 WiFi
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 04a9:30f9 Canon, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```
Also, i checked what was mounting, and I did soemthing that might be bad,
I typed
```
sudo mount /dev/sda3 /media
```
where apparently /dev/sda3 is my / drive, so now inside the media folder I have another copy of my entire hdd, at least my linux partition.  will that fix itself when I reboot?

---

### Post by Daveth on 2007-10-14
should be recognised, according to this

[http://www.gphoto.org/proj/libgphoto2/support.php](http://www.gphoto.org/proj/libgphoto2/support.php)

though you will have to alter the way the camera's usb connection works - set to PTP mode within the camera's menu setup.

---

### Post by travm on 2007-10-14
That doesnt seem to help, but thanks.  There is no option for ptp mode in my camera, although it supports it, I am going to have to say that it is the default and only option for file transfer.  I am installing gthumb at the moment as I have read about people using it to transfer photos, also this all seems to reference gphoto2 and the related libraries, which at the moment are not installed on my system (Xubuntu fiesty).  I guess its uber usefull programs like that not being included that allow Xubuntu to call itself "light weight".  We will see.  Its too bad I made a bad burn of my Ubuntu fiesty live cd while I had high speed.  Otherwise I would have installed it instead of Xubuntu, which I had an alternative install cd of, which ended up nuking my windows partion on resize and is lacking any real usefull programs.  
I guess its advantageous to have to learn how to set all this stuff up, but since it killed my "it just works" Windows XP install it is agrivating that i need to install so much stuff just to get this machine back to where it was.

slowly getting there though, this camera dealio might be the last hurdle in the race to stop me from reinstalling XP :)

---

### Post by travm on 2007-10-14
Installing Gthumb allowed me to import the pictures from my camera with no setup outside of selecting the program in synaptic.  I would still like to have it pop up on my desktop so I could do it without the need of running another program to capture my images, but this is workable, and it is acceptable.  I would also like it if gthumb opened and automatically went to the import images dialog when i plugged in my camera, but like i said, this works.

---

