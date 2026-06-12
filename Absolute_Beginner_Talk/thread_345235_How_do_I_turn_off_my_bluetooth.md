---
title: "How do I turn off my bluetooth"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2007-01-24
My buddy was messing around with his phone and I found out that my laptop is "showing" itself when you do a local bluetooth scan.  How do hide my bluetooth status? Or shut it off altogether?  

I have a HP laptop with built in wireless abg w/bluetooth

---

### Post by mrgrapefruit on 2007-01-24
I would suspect you would go to System > Administration > Services and uncheck "Bluetooth". If that doesn't work you could try stopping the blued daemon running with something like

```
sudo /etc/init.d/bluetooth stop
```

then edit /etc/bluetooth/hcid.conf to stop it from running at startup, but i'm not too sure about that part.

good luck

---

### Post by ardchoille42 on 2007-01-24
You can also:

```

sudo apt-get install sysv-rc-conf

```

Then, at the command line, run sysv-rc-conf:

```

sudo sysv-rc-conf

```

sysv-rc-conf will allow you to set things up to run or not run in the different run levels.

---

### Post by charles.g.moore on 2007-01-24
If I shut down the bluetooth services will it impact my wireless card since I'm assuming they are one in the same...Or are they?

I installed sysv-rc-conf but which process do I shut down and at what level?
bluemon 2,3,4,5 or
bluez-util 2,3,4,5 or 
both

---

### Post by seshomaru samma on 2007-01-25
i dont have bluetooth but i think that if you install BUM
```
sudo apt-get install bum
```
you can stop bluetooth services from running on boot

---

### Post by valkarin on 2007-01-25
With sysv-rc-conf you stop bluez-util 2,3,4,5.  I don't know what the other one is.  You should check out what it is first.  A good place to look and a great guide for sysv-rc-conf is at [http://doc.gwos.org/index.php/Speed_up_boot]("http://doc.gwos.org/index.php/Speed_up_boot").

It walks you through someone elses system, so there will be things on there that aren't on yours and vice versa, but is still a good guide.

---

### Post by Ehnvis on 2007-01-30
I've been looking for a solution on this matter myself for the last few hours and after reading how the config file is setup I think I have a solution. It works on my laptop anyway.

```
sudo gedit /etc/bluetooth/hcid.conf
```

Find the line that says ```
discovto 0
``` and change from 0 to 1. This is the amount of time it's discoverable for a search after boot/restart of the service. My laptop doesn't show up on a scan now anyway. Still possible to send stuff to and from it as I want it to.

---

