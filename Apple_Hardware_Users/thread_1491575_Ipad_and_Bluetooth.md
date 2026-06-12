---
title: "Ipad and Bluetooth"
date: 2010-05-23
forum: Apple Hardware Users
---

### Post by thinktyler on 2010-05-23
Any possible way of syncing ipad with ubuntu via bluetooth?

I like switching between gimp and ipad. Any help would be great.

---

### Post by Ravernomina on 2010-05-24
> **thinktyler said:**
> Any possible way of syncing ipad with ubuntu via bluetooth?

I like switching between gimp and ipad. Any help would be great.

Nope. Only Solutions are the Following

Dump Linux

Multi-boot With Windows/Mac OS X

Vm Windows/Mac OS X and sync there

---

### Post by thinktyler on 2010-05-24
Not to question you, but to clarify my original post.

Syncing music, photos and video is possible 10.04 through gtkpod, amarok, and rhythmbox.

I find it hard to believe that a standard bluetooth connection is not possible between ubuntu and the iPad.

---

### Post by Tahakki on 2010-05-25
If you can't just connect it via BT and use GTKPod as normal, probably not.

---

### Post by v1ad on 2010-05-25
if there is a will there is a way. think creatively and there will be a solution. i would try it out but i don't have a ipad.

---

### Post by Tahakki on 2010-05-25
It might be possible if you were to jailbreak it.

---

### Post by sha.goyjo on 2010-05-25
There may actually be a solution to whatever problem you are facing, but in order to help you I need you to define the problem. What do you mean, exactly, by "sync". If you can tell me that, I should be able to help you.

If by sync you mean "sync everything in iTunes the way that Apple does it" we may have some trouble

If by sync you mean "sync a couple of programs, and perhaps access programs running on the other computer VIA the iPad" we may be good

Just let me know exactly what you are looking for and I'll see if I can help.

---

### Post by thinktyler on 2010-05-25
The art studio applications has the option to send your easel over bluetooth. When I attempt to transfer my art to ubuntu, ubuntu requests a PIN, in which iPad never gives me this option.

My iPad is jailbroken.

---

### Post by sha.goyjo on 2010-05-25
Ahh, okay. Is the pin you are referring to a bluetooth device pairing pin, or some other pin?

If it is a bluetooth device pairing pin (and not referenced in the documentation for your iPad), I would suggest first trying the standard pairing codes (0000, 1234, 1111, etc), and automatic pairing.

I don't know much about iPads, but if all it is doing is bluetooth obex, you should be able to recieve the file from it. If it is more complex, I'm sure we can find some way to work our way through it.

---

### Post by thinktyler on 2010-05-25
I successfully paired the iPad with ubuntu, but browsing the device or trying to send a file fails. 

According to this wiki:

[https://help.ubuntu.com/community/MacBookPro5-1_5-2/Lucid](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Lucid)

The author writes, "Did not succeed to connect two computers or to browse a device yet!"

Does this mean that bluetooth doesn't work yet under lucid? or, that he hasn't tested this out yet?

Thanks alot for the help.

---

### Post by sha.goyjo on 2010-05-25
....wait, you are trying to access it with a Macbook Pro 5,2? I guess I'm unsure as to your setup. Could you tell us the setup of the system you are trying to sync the iPad with?

---

### Post by thinktyler on 2010-05-26
Ubuntu Lucix Lynx 10.04 
Kernel 2 32
MacBook Pro 5,2

iPad wifi jalbroken

Is that the information you need? 

I tested the bluetooth connection to my friends computer running Snow Leo.

---

### Post by sha.goyjo on 2010-05-27
I think our first concern needs to be attempting to pair the ibook with the lucid system. apparently the author of the mactel support wiki was able to do at least that much under karmic. Can you pair your macbook with the iPad?

If you can pair, maybe we can figure out a way to do obex.

---

### Post by thinktyler on 2010-05-28
I was able to pair with the default bluetooth manager, but only through bluemon (from ubuntu app store) did I finally figure out how to browse the ipad while connected over bluetooth.

The default bluetooth manager would constantly disconnect, without me knowing. 

I'd like to maybe file a bug report, but I'm not sure the proper way of doing so.

---

### Post by sha.goyjo on 2010-05-31
Typically, if apport fails to function, you use [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by Tahakki on 2010-06-01
Just type into a terminal: ubuntu-bug bluetooth

I think. :L

---

