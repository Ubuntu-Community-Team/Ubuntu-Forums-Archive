---
title: "Wireless Problem"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Bofur on 2007-06-12
Hi, I think I have found the name of my Wireless card, but I don't know how to get it working.```
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)

```
I'm guessing that unknown device is my wireless card. If anyone know how to get it working I'd greatly appreciate it!

---

### Post by Bofur on 2007-06-12
Bump:popcorn:

---

### Post by Bofur on 2007-06-12
I'd also like to mention that I'm using a Dell XPS M1710 Notebook and the WiFi icon on my keyboard is lighting up, and yet I'm not getting any internet.

---

### Post by kittyhawk63 on 2007-06-12
> **Bofur said:**
> I'd also like to mention that I'm using a Dell XPS M1710 Notebook and the WiFi icon on my keyboard is lighting up, and yet I'm not getting any internet.
Borfur,
Rather than making a new post to your thread each time, just "edit" your first post and type "edit:" below your preceding comments. That saves people time reading about your problem through many different messages. You can also delete a message, but not the post, by deleting the words and placing a period "." on the post. That will let people know that you have changed your mind about that particular message. 

I am sorry that I cannot help you with wireless. I just today received a laptop from a friend that has wireless and I no idea "yet" how to use it.

I hope that you get yours working soon.
kh

---

### Post by kittyhawk63 on 2007-06-12
.

---

### Post by wreti on 2007-06-12
This walk through worked very well for me. [http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html)
Though you don't have a 1501, the basic instruction should still help you so long as you use the proper driver for your card. I know others that used this as a guide on many other brands. Hopefully it works for you too!

---

### Post by kittyhawk63 on 2007-06-12
> **wreti said:**
> This walk through worked very well for me. [http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html)
Though you don't have a 1501, the basic instruction should still help you so long as you use the proper driver for your card. I know others that used this as a guide on many other brands. Hopefully it works for you too!

Wreti,
Thanks for the link. If I have any problems with my wireless, I will be able to do some research now. My wireless is already working. Set up by the person who gave me his laptop after he bought a brand new one.
kh

---

### Post by Bofur on 2007-06-12
Well I did everything the instructions told me to do, even downloaded the correct drivers I needed and it still didn't work. Any ideas?

---

### Post by wreti on 2007-06-12
Does this computer have a wired connection, or are you accessing the internet on another machine?

---

### Post by Bofur on 2007-06-12
Yes, I'm on the wired internet right now. It works fine, the wireless doesn't :(.

---

### Post by Bofur on 2007-06-12
Another thing, there are two internet icons next to the time in the corner of my desktop. Theres eth0 which I'm connected to, and then it says I can switch to lo, which sends and recieves packets, but it won't allow me to access the internet. Maybe it has something to do with that?

Edit: Next to lo it says idle.

---

### Post by wreti on 2007-06-12
Just to get a feel for where you're at, you were able to successfully install build essential and linux headers? Under your Network settings, do you have wireless checked and wired connection set to "roaming  mode enabled"?

---

### Post by Bofur on 2007-06-12
Under Network settings it only lists the Modem and the Wired Connection.

I'll change the Wired Internet to roaming too, since it wasn't checked.

---

### Post by wreti on 2007-06-12
There should definitely be a "wireless" option. Check the guide again to ensure all steps were followed. It took me 3 or 4 trys to actually get it going. Every time I went through process, I found missteps I had taken before. Unfortunately, I'm not a pro and can only help based on my recent experiences. Don't get frustrated! It will happen!

---

### Post by Bofur on 2007-06-12
Heres a pic, its not there: [http://img.photobucket.com/albums/v401/Krymeth/Untitled.jpg](http://img.photobucket.com/albums/v401/Krymeth/Untitled.jpg)
Also heres the output when I type ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:15:C5:5B:29:E0  
          inet addr:10.75.0.3  Bcast:10.75.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe5b:29e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1077 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:675988 (660.1 KiB)  TX bytes:169347 (165.3 KiB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:942 (942.0 b)  TX bytes:942 (942.0 b)

```
Here is iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

```

This is my card btw: Intel (R) Wireless WiFi Link 4965AGN

---

### Post by wreti on 2007-06-12
Did a quick search on your card and found that only ndiswrapper 1.45 supports it. Is that the one you installed?

---

### Post by Bofur on 2007-06-12
Thats my problem then. I installed 1.46 lol. I'll try installing 1.45 and keep you updated. Thanks!

---

### Post by wreti on 2007-06-12
I meant to say 1.45 or higher. 1.46 should also work, though reverting to 1.45 is worth a try.

---

### Post by Bofur on 2007-06-13
Could you tell me if I'm doing this part right because I don't think I am:
```
root@ubuntu:/home/justin/.drivers# sudo ndiswrapper -i w29n51.inf
driver w29n51 is already installed
root@ubuntu:/home/justin/.drivers# sudo ndiswrapper -l
bcmwl5 : invalid driver!
netw4k32 : invalid driver!
w29n51 : driver installed
root@ubuntu:/home/justin/.drivers# 

```

---

### Post by wreti on 2007-06-13
As best I can tell (like I said before, I'm not a pro) you have too many drivers installed, though it looks like it's recognizing the correct one. I made similar mistakes and, after many misinstallations, was forced to reinstall Ubuntu to clear the many blunderous errors I'd made. At this point, I can only suggest that as a resolution followed by carefully stepping through the guide I provided earlier once more. That's how I did it. I wish I could provide further assistance to you. 

Hopefully someone with more experience and knowledge will jump in!

---

### Post by Bofur on 2007-06-13
Anyone else have any ideas?

---

