---
title: "Problem with ndiswrapper"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by unrealmstr on 2006-11-12
I have successfully installed ndiswrapper and have loaded the correct driver (it says hardware found)
[[IMG]http://img243.imageshack.us/img243/2848/screenshotdj3.th.png[/IMG]](http://img243.imageshack.us/my.php?image=screenshotdj3.png)
and i connect to a wireless network near me with no encryption to test it, and it says its active. well it doesnt work, and if i close the network configuration and open it again it says its not configured
[[IMG]http://img243.imageshack.us/img243/484/screenshot1lx8.th.png[/IMG]](http://img243.imageshack.us/my.php?image=screenshot1lx8.png)
and third, it says its a ra0 connection?? someone please help!!

---

### Post by TheRingmaster on 2006-11-12
I don't think the forum people want you to post pictures like that. Please post pictures as attachments.

---

### Post by unrealmstr on 2006-11-12
its not stretching the page so i dont see a problem...

---

### Post by TheRingmaster on 2006-11-12
I problem with posting pictures like you did is that it takes a lot of bandwidth to keep it there.

---

### Post by unrealmstr on 2006-11-12
actually its using image shacks bandwidth not ubuntus, but ok i attached them as thumbnails... while your here can you please help me with my problem?

---

### Post by Henry Rayker on 2006-11-13
What version of Ubuntu are you using? If you're using Dapper, I can help you out; if it's Edgy, I still can't get that particular chipset to work.

As for it being called ra0...that's what the driver requests the network interface be called. rt61 chipsets are ra0, rt2570 are called rausb0 and so on.

If you're using Dapper, you can get the drivers to work natively; check out [this link.]("http://ubuntuforums.org/showthread.php?t=240669&page=2")

---

### Post by unrealmstr on 2006-11-13
Well i dont have the internet in ubuntu, i was hoping you could help me with ndiswrapper, it seems its all installed correctly but it wont connect to any networks, it says the SSID of the networks, so that means its working right?

---

### Post by Ramses on 2006-11-13
I think interface name with ndiswrapper should be wlan0 if not configured otherwise. Well that is how it is with my bcm4318 and rt73 chipsets. Ra0 could be interface from ubuntu native driver. Maybe you should blacklist native driver.

---

### Post by Henry Rayker on 2006-11-13
well, you could always download the packages from that thread (there is a link on the first page) and transfer them over on a disk or something.

It's just been my experience that ndiswrapper is buggy (at best); I haven't used it since Breezy, and even then, my connection was rife with errors.

---

### Post by bango on 2006-11-13
Hello!

I installed Ubuntu last week. When I managed to install the ndiswrapper for my wireless card I noticed that it didn't support WPA. So I had to get wpa_supplicant to be able to connect to my access point. It doesn't really sound like this is your problem but it may be worth to notice.

This may be stupid to point out but have you run ifconfig <interface name> up and dhclient (if you use dhcp)?

//bango

---

### Post by DannyG on 2006-11-13
Whats the model number of your wireless card? Where did you get the drivers that ndiswrapper is using?

---

### Post by unrealmstr on 2006-11-13
model number is WMP54G im pretty sure i installed the driver correctly im just hoping i made a simple error that someone can point put :(

---

### Post by thisroadclosed on 2006-11-20
Hey, I've been battling this problem for awhile, and I think I got it working.  After reading this thread, I found a post elsewhere [(go here)]("http://www.thedesignexperience.org/weblog/one-entry?entry_id=98579") that basically said to clear out the junk in your /etc/network/interfaces file (I did so by commenting to keep from deleting something important) and restart your networking services (or your computer).  It came back up, I tinkered with WifiRadar a bit, and I got connected.

---

### Post by thisroadclosed on 2006-11-20
UPDATE: It works with WEP, but I haven't a WPA WAP to try...

---

