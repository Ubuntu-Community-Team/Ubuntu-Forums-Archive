---
title: "Disaster with xorg"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by LittleKoy on 2007-12-02
Hello, I've just made a disaster, I think é.è

I have a Radeon 9200SE, and I was dying trying to install drivers, because even a SNES emulator was going so sloooooow... When I found a program, envy. I was crying out of happiness, it did everything and installed the correct drivers with just a click...

But from then, my pc started crashing every 5 minutes. So I uninstalled the driver, thinking it was because of it, but the old driver wasn't back, because now even moving a window was so slow...

I though of uninstalling and reinstalling xorg... Well, actually I uninstalled it, then rebooted... And now installing it is a problem, really -.- Graphical mode and connection won't start, so the only way is from the cd I think... How can I do that?

---

### Post by Dr Small on 2007-12-02
Have you tried reconfiguring xorg ?
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by LittleKoy on 2007-12-02
The problem is that i removed xorg... In fact it says "xserver-xorg not installed"...

---

### Post by Dr Small on 2007-12-02
Reinstall it, and then reconfigure it.

---

### Post by GSF1200S on 2007-12-02
> **Dr Small said:**
> Reinstall it, and then reconfigure it.

sudo apt-get install xserver-xorg

and then 

sudo dpkg-reconfigure xserver-xorg

Just a little assist Dr. :)

---

### Post by LittleKoy on 2007-12-02
That's the problem - how can i reinstall it?

---

### Post by Dr Small on 2007-12-02
> **GSF1200S said:**
> sudo apt-get install xserver-xorg

and then 

sudo dpkg-reconfigure xserver-xorg

Just a little assist Dr. :)
Thanks. I'm getting slow today...........
Anyhow, is it xserver-xorg or just xorg ?? I haven't done it in awhile and forget...

---

### Post by LittleKoy on 2007-12-02
My ubuntu now starts only in text mode, and my connection doesn't start, so I need to install it from the cd... How can i do that?

---

### Post by Dr Small on 2007-12-02
Your connection doesn't start ??
Just because you have no GUI doesn't mean you network doesn't connect and startup..

---

### Post by GSF1200S on 2007-12-02
> **Dr Small said:**
> Thanks. I'm getting slow today...........
Anyhow, is it xserver-xorg or just xorg ?? I haven't done it in awhile and forget...

ohh good call.. im a little rusty today myself- I would think apt would tell him/her if xserver-xorg was right...

---

### Post by LittleKoy on 2007-12-02
Yes, but my wifi card doesn't start...

---

### Post by Dr Small on 2007-12-02
> **LittleKoy said:**
> Yes, but my wifi card doesn't start...
Are you absolutely sure of this ? Have you tried reinstalling xorg ?
Your Wifi card should start at startup. It doesn't need a GUI to run, it runs in the background.

Dr Small

---

### Post by GSF1200S on 2007-12-02
When the text mode comes up, try the follow command:

sudo apt-get update


If it says "Err, failed to fetch" or something like that a bunch of times, you dont have a network. If it says "hit" a bunch of times, than your network works and you can run those commands to try and get xorg back online.. You cant really install a package from a live cd, except for maybe downloading an xorg .deb package and saving it to /home, but then youd need to use apt to gather the dependencies anyways..

I can help you get a network connection from the command line and we can get this xorg issue sorted :)

---

### Post by Dr Small on 2007-12-02
> **GSF1200S said:**
> When the text mode comes up, try the follow command:

sudo apt-get update


If it says "Err, failed to fetch" or something like that a bunch of times, you dont have a network. If it says "hit" a bunch of times, than your network works and you can run those commands to try and get xorg back online.. You cant really install a package from a live cd, except for maybe downloading an xorg .deb package and saving it to /home, but then youd need to use apt to gather the dependencies anyways..

I can help you get a network connection from the command line and we can get this xorg issue sorted :)
I think you can install xorg if you have an alternate cd, and apt will search the cd (if it is uncommented in sources.list) and install it from the cd.

---

### Post by LittleKoy on 2007-12-02
No network, it fails to fetch...

---

### Post by LittleKoy on 2007-12-02
I have the Ubuntu CD... But when I do apt-get, it doesn't find it

---

### Post by Dr Small on 2007-12-02
> **LittleKoy said:**
> I have the Ubuntu CD... But when I do apt-get, it doesn't find it
It only works with the alternate cd.

---

### Post by LittleKoy on 2007-12-02
Isn't there a way to install from the Official/live CD?

---

### Post by GSF1200S on 2007-12-02
> **LittleKoy said:**
> I have the Ubuntu CD... But when I do apt-get, it doesn't find it

**EDIT** Wrong thread :)

---

### Post by Dr Small on 2007-12-02
You can't use the livecd as a package manager (or repository) for apt, if it is the livecd. It has to be the alternate cd, because it is built to be used as a repository.

By the way, I thought GSF1200S was going to stop by and help you with your Wifi via the command line.... :S

Dr Small

---

### Post by GSF1200S on 2007-12-02
Ive never had to use the alternate cd for stuff like this.. it should be easy to do it from the command line.

When you type:

iwlist scanning

do you return any results (your network is wireless right)? If so, then note which interface returns results (ath0, eth1, etc...). Then input that interface in the following commands- for example, well say ath0 is your wireless interface:

sudo iwconfig ath0 essid networkname

sudo iwconfig ath0 key yourwepkeyifyouhaveone

sudo dhclient ath0


and thats it! Then try an apt-get update again to make sure your connecting to the net..

If when you type that, you get something like the following:

eth1: scanning not supported
eth0: scanning not supported
ath0: no scan results

Then try this command before doing the above:

sudo ifdown ath0
sudo ifup ath0

I dont know how to use apt from the alternate cd. Everytime I tried it told me it couldnt fetched, even though it tried reading the CD.

---

### Post by GSF1200S on 2007-12-02
> **Dr Small said:**
> You can't use the livecd as a package manager (or repository) for apt, if it is the livecd. It has to be the alternate cd, because it is built to be used as a repository.

By the way, I thought GSF1200S was going to stop by and help you with your Wifi via the command line.... :S

Dr Small

Hehe, im trying to do 2 threads at once, and its getting a little involved.. sorry if it took a little while :)

---

### Post by Dr Small on 2007-12-02
You have to uncomment the cdrom entry in /etc/apt/sources.list and comment the rest out, so it will read the cdrom only. Then try installing something with apt-get, and it should try to install it off the cdrom (alternate cd).

---

### Post by GSF1200S on 2007-12-02
> **Dr Small said:**
> You have to uncomment the cdrom entry in /etc/apt/sources.list and comment the rest out, so it will read the cdrom only. Then try installing something with apt-get, and it should try to install it off the cdrom (alternate cd).

Ohhh wow.. good stuff to know. Well, i mainly needed apt off the cd when I did a command line install of 7.10 and installed kdecore from there. I also had a problem with it NEEDING the cdrom even when i was on the net, and I fixed that by commenting out the cdrom in sources.list. This should have clued me in to doing the opposite to have only the CD used. 

Do you know if it matters what the update status is of apt? For instance, lets say I install ubuntu from the alt cd ( a full system). Everything goes good, and I do an apt-get update and upgrade. Now, two weeks go by and my xorg crashes, and i try to use the alt cd to reinstall it. If apt has been updated to a newer version of xorg, will trying to use the CD even work? Id be curious to know this one... :)

---

### Post by Dr Small on 2007-12-02
> **GSF1200S said:**
> Ohhh wow.. good stuff to know. Well, i mainly needed apt off the cd when I did a command line install of 7.10 and installed kdecore from there. I also had a problem with it NEEDING the cdrom even when i was on the net, and I fixed that by commenting out the cdrom in sources.list. This should have clued me in to doing the opposite to have only the CD used. 

Do you know if it matters what the update status is of apt? For instance, lets say I install ubuntu from the alt cd ( a full system). Everything goes good, and I do an apt-get update and upgrade. Now, two weeks go by and my xorg crashes, and i try to use the alt cd to reinstall it. If apt has been updated to a newer version of xorg, will trying to use the CD even work? Id be curious to know this one... :)
That, I have no clue. It shouldn't matter, I wouldn't think, even if you have upgraded with apt. Apt only upgrades things which are in need of upgrade. So if xorg would crash and mess up and you wanted to reinstall it from the alternate cd, I don't see why it wouldn't work.

of course, the alternate cd is the hard way, unless you don't have a network connection. Then it would become useful :)

---

