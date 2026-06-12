---
title: "Cant get internet to work on my desktop"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by garrettstarnes on 2008-04-18
Hi guys,
I just got internet hooked up today, and it works fine on my laptop.  On my desktop however, firefox keeps saying 'server not found'.  I have ubuntu 7.10.  Any suggestions?

thanks.

---

### Post by Dr Small on 2008-04-18
Have you tried connecting to the network?
How are you connected, by wireless or ethernet?

---

### Post by sam_delta on 2008-04-18
which network hardware do you use?, has worked before?

---

### Post by garrettstarnes on 2008-04-18
i am using a cable modem with an ethernet cable (the modem also came with a usb a to b cable), I clicked on network connections on the bottom taskbar, and clicked properties.  I selected lo, and everything else to tryto get it to work.  I also went into system, administration, network, and wired connections.  The wierd thing to me is, when i watch to connection properties,  I see packets sent and recieved.  I don't understand that.  All i do is switch the ethernet cable from my desktop to my laptop and it works.  But not my desktop.  I have never connected my desktop to the internet.  But i hope to soon!
thanks guys.

---

### Post by Dr Small on 2008-04-18
Well, "lo" is the loopback interface. You won't get a connection that way. If you are in the Network Connection Thingy majig where you can see the connection speed / pecentage, in the box, change that to eth0 to see if anything happens.

By the way, how old is this desktop? If it is old, then perhaps it has a bad RJ-45 jack on it.

Dr Small

---

### Post by garrettstarnes on 2008-04-18
When I change it to 'eth0:avahi', the status says 'error'.  I then click on the configure button, and then I get a dialog box that says 'The interface does not exist'.

---

### Post by garrettstarnes on 2008-04-18
And also,  It is a pretty old computer.

---

### Post by Dr Small on 2008-04-18
Could you please post the output of:
```
cat /etc/network/interfaces
```

---

### Post by superprash2003 on 2008-04-18
are you using DHCP? go to the terminal and type ifconfig and post results here

---

### Post by garrettstarnes on 2008-04-18
user@StarnesFamilyComputer:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback







iface eth0 inet dhcp

auto eth0
user@StarnesFamilyComputer:~$

---

### Post by erlyrisa on 2008-04-18
I think the problem may actually simpler than me may think.....


you mean when you click the firefox icon on the Panel - firefox don't start!.....

... in that case it's just a "broken link"

-delete/fix/replace the shortcut.

--To see if firefox actually starts press "alt F2" and type firefox.

---

### Post by garrettstarnes on 2008-04-20
I haven't heard back from anyone.  any suggegstions?

---

### Post by Darkdelusions on 2008-04-20
This is going to sound like a silly question but when you switched your cable modem over from you laptop two your pc did you power cycle your cable modem.

The cable modem is only able to remember one mac address at a time there for when you switch from computer to computer you must power cycle the cable modem. 

(From what I have read so far your not using a router)

Also after you power cycling your cable modem do a 


```
sudo /etc/init.d/networking restart
```

then 

```
ifconfig
```
 
and make sure eth0 is up. 

if eth0 is not up do

```
sudo ifup eth0 or sudo ifconfig eth0 up
```

---

### Post by garrettstarnes on 2008-05-02
that did it!!  I just cycled power on the modem and i'm in business!! thanx so much yall!

---

