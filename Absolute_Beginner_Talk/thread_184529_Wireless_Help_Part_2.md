---
title: "Wireless Help Part 2"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by Revmann on 2006-05-30
I posted on this forum a couple weeks ago about getting wireless working. Here is the thread for reference [http://www.ubuntuforums.org/showthread.php?p=1017161#post1017161](http://www.ubuntuforums.org/showthread.php?p=1017161#post1017161)

Anyways, I had some serious issues on my laptop that waranted reinstalling. I decided to go ahead and upgrade to Dapper. When I tried to get the wireless working again, I couldn't get it working when following the referenced instructions in the thread. For some reason, it is saying that the driver is not valid. I have tried it a few times and nothing gets better.

kerry@ubuntu:~$ sudo aptitude install ndiswrapper-utils
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
kerry@ubuntu:~$ sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
kerry@ubuntu:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5  invalid driver!
kerry@ubuntu:~$


I didn't proceed because I have gone farther than this and the broadcom internal wireless won't start up. Any clue what to do next?

---

### Post by hw-tph on 2006-05-30
In the same location as the .inf file you will need to have at least the accompanying .sys file, or you will end up with this error. Could this be the problem?


Håkan

---

### Post by Revmann on 2006-05-30
Ok, I extracted the sys file of the same name and when I ran the installation of the hardware, everything worked fine and it shows the drier listed. It won't seem to do anything when I set the wireless up throught the network panel. It won't even allow me to detect any networks in my area. I went so far as to shut down Ubuntu and restart windows so I could verify which position my wireless button was in by watching it light up. I went ahead and removed the driver and started over. The process is below:

kerry@ubuntu:~$ sudo ndiswrapper -e bcmwl5
Password:
kerry@ubuntu:~$ ndiswrapper -l
No drivers installed
kerry@ubuntu:~$ sudo aptitude install ndiswrapper-utils
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
kerry@ubuntu:~$ sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
kerry@ubuntu:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present
kerry@ubuntu:~$ sudo modprobe ndiswrapper
kerry@ubuntu:~$ sudo ndiswrapper -m
modprobe config already contains alias directive

Not sure what the last line means. Could someone clarify that. I am wondering if the modprobe thing is giving me issues because of a screw up last night in trying to do this with the wrong driver. Can anyone give me some insight please?

---

### Post by hw-tph on 2006-05-30
That looks fine. The last line is the response to you trying to add an alias for the module - which has already been done.


Håkan

---

### Post by popkid on 2006-05-30
[QUOTE=hw-tph]That looks fine. The last line is the response to you trying to add an alias for the module - which has already been done.


Håkan[/QUOTE]

Dapper also includes native drivers for your chipset, these conflict with ndiswrapper, so you have 2 choices, you can either stick with ndiswrapper that you are used to and stop the broadcom drivers from loading or use the broadcom drivers and stop ndiswrapper from loading.

if you type in the following

sudo modprobe -r bcm43xx
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

does that help?

pK

---

### Post by Jagot on 2006-05-30
Hi, I replied to your original post a couple of weeks ago.  popkids correct, you'll need to stop the supplied drivers loading that come with Dapper, but you'll also need to blacklist so the module doesn't load on boot.  This is what I do to get mine working:

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

---

### Post by Revmann on 2006-05-30
That got it taken care of. Thanks for tag-teaming my problem, guys. Much appreciated :)

---

