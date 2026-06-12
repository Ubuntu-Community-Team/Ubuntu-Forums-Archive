---
title: "[SOLVED] Bluetooth"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by cygnis1 on 2008-04-11
Help.  How do I turn on bluetooth in gutsy?  I have used it before with my Motorola Vxxx, as I can see the laptop listed on the phone.  But I cannot now connect the phone to the computer.  It was working in Hardy.  I tried the obex server and the kde manager but neither one will find the phone.  I think bluetooth is not enabled.
Thanks,
Cygnis1

---

### Post by aeiah on 2008-04-11
have you tried bluetooth-applet? i cant remember what i did to get my bluetooth card working either, but i have that in my start-up applications list, heh.

---

### Post by bt224 on 2008-04-11
I'm not at home, but I remember mine wouldn't find the phone unless I was actually trying to send or recieve something, it never just connected. I don't use it a lot, but I do remember the frustration.

---

### Post by Biggy on 2008-04-11
Blueman is great app 

Download [here]("http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56")

---

### Post by cygnis1 on 2008-04-11
couldn't install it

---

### Post by Biggy on 2008-04-11
Install from synaptic

System > Administration > Synaptic Package Manager > Search Blueman

---

### Post by JoshuaRL on 2008-04-11
If you ever get bluetooth working properly, you should try out [Sabre.](http://www.kde-apps.org/content/show.php/Sabre:+Bluetooth+Proximity+Plugin?content=75746)  It's the coolest.

Proximity plugin that pauses Amarok, shows away in Konversation, and locks your screen.

---

### Post by cygnis1 on 2008-04-11
not in the repositories

---

### Post by JoshuaRL on 2008-04-11
> **cygnis1 said:**
> not in the repositories

You're right, but it's on the KDE site and is highly ranked.  I know the developers and they're good guys.  You can trust this one.  If you check the support forum for Sabre you might recognize the administrators.

I forgot some functionality too.  It will unlock the screen, play AmaroK, and put you back on Konversation when you get back.  And it is really easy on bluetooth for your phone, so it won't eat battery.

---

### Post by cygnis1 on 2008-04-12
Is there a way to configure bluetooth?  I still think that bluetooth is somehow disabled.  Where do I configure it?
Cygnis1

---

### Post by Inxsible on 2008-04-12
> **Biggy said:**
> Blueman is great app 

Download [here]("http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56") +1 for Blueman

> **cygnis1 said:**
> Is there a way to configure bluetooth?  I still think that bluetooth is somehow disabled.  Where do I configure it?
Cygnis1you can restart your bluetooth by issuing```
sudo /etc/init.d/bluetooth restart
``` (I hope it is the same for KDE-- I am a Gnomer)

You can also check to see if you have paired your phone with your computer.
also try```
sudo hcitool scan
``` to see if your phone is within range and visible to the computer

---

### Post by cygnis1 on 2008-04-12
I have discovered that I do indeed have blueman.  However it doesn't seem to be functioning as everything is greyed out.  I tried to restart bluetooth using the above commands, however I can't pair with my phone.  Any more suggestions would be appreciated.
Thanks

---

### Post by Inxsible on 2008-04-12
When you did the hcitool scan, did it see your phone and give you its mac address ?

---

### Post by cygnis1 on 2008-04-12
It says device not available.  no such device.

---

### Post by Inxsible on 2008-04-12
> **cygnis1 said:**
> It says device not available.  no such device.
That's strange ! Do you have bluetooth on your computer and have it switched on ?

I am sorry to go so basic on you...but 'No such device' would mean that you do not have bluetooth on you machine..or at least its not enabled.

---

### Post by cygnis1 on 2008-04-12
I have bluetooth and have paired it with my phone.  In obex it shows the phone, and in my phone it shows the computer.  They will not see each other though.  My phone connects to my headset just fine, and it has connected to the computer in the past.  I tried to restart bluetooth in the terminal and I suppose it is on.  I don't know what the problem is.  I have even disconnected my wireless mouse thinking it might be interfering but that doesn't seem to help

---

### Post by Inxsible on 2008-04-12
> **cygnis1 said:**
> I have bluetooth and have paired it with my phone.  In obex it shows the phone, and in my phone it shows the computer.  They will not see each other though.  My phone connects to my headset just fine, and it has connected to the computer in the past.  I tried to restart bluetooth in the terminal and I suppose it is on.  I don't know what the problem is.  I have even disconnected my wireless mouse thinking it might be interfering but that doesn't seem to helpAre you trying to browse the phone thru nautilus?

and do you get an Obex Error :  Couldn't connect to <mac address>

There is an age old bug with respect to that.  I have a thread open on that as well.

---

### Post by Inxsible on 2008-04-12
From your phone try this, When you search for devices and it sees your computer, select it and enter the passkey which is in your /etc/bluetooth/hcid.conf file.

That will pair your phone to the computer.

---

### Post by cygnis1 on 2008-04-13
I don't know what is wrong.  I DID remember finally that I had a bluetooth dongle from a couple of years back.  I plugged it in and am able to pair with my phone.  When I look at the devices on my phone it shows the the computer as blue z, and not the computer's name.  And blueman DOES rock.
Thanks to all.
Cygnis1

---

