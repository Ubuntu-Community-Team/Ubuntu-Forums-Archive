---
title: "bluetooth explained, please"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by ghoran on 2008-02-17
Can someone explain to me how bluetooth works?
I followed this [http://ubuntology.com/2007/10/27/access-your-phone-via-bluetooth-with-ubuntu-gutsy/](http://ubuntology.com/2007/10/27/access-your-phone-via-bluetooth-with-ubuntu-gutsy/)
and I have two questions:

1. I cannot see BT Diag
2. BitPim caanot see my phone Samsung SGH-A737. How else can I see the files?

---

### Post by bettlebrox on 2008-02-17
I didn't have to follow all those instructions to access [bluetooth]("http://timony.com/mickzblog/2007/10/09/ubuntu-bluetooth-sd-card/") on my phone (Nokia N73). I just had to install the gnome-vfs-obexftp & bluez-gnome packages to get file transfer working, and then start the Bluetooth File sharing app (see the attached screenshot).

However, to use my phone as a [modem]("http://timony.com/mickzblog/2007/11/16/ubuntu-linux-t-mobile-nokia-n73-as-a-bluetooth-modem/") over bluetooth (so I can surf the web on my laptop using the phone's internet access) I had to a lot of the same procedure.

---

### Post by talsemgeest on 2008-02-17
Make sure your phone is "visible". It varies between phones, but you can usually find it under your bluetooth preferences

---

### Post by steveneddy on 2008-02-17
[Try this]("http://ubuntuforums.org/showthread.php?t=586105")

---

### Post by ghoran on 2008-02-18
Guys,
You are not going to believe this but, I REALLY overcomplicated this.
I had gotten this working before. I remembered that I saw it in a book my dad had. Beginning Ubuntu Linux.
I removed whatever I had previously installed and did and did this from the book:
1. gksu gedit /etc/bluetooth/hcid.conf 
- changed security to auto
- changed the pin
2. sudo /etc/init.d/bluetooth restart 
3. Went to the phone and set that up
4. From synaptic Package Manager installed gnome-bluetooth
5. gksu gedit /etc/rc.local
- before the exit 0 typed: hciconfig hci0 inqmode 0
6. Went to Applications/Accessories/BlueTooth File sharing

All set to transfer files. 
To be honest, it still did not work.
THEN I REALIZED THAT I ONLY HAVE ONE USB 2.0 AND I HAD THE BLUETOOTH IN A USB 1.1

UGH!!! 

Anyway, it now works great. I suspect that it would have worked before if I realized the USB 1.1 vs. USB 2.0

I then created a launcher on the desk top and put in the command gnome-obex-send and I can now drop files on that launcher and they go to the phone.

THANKS FOR ALL YOUR HELP!!!

---

### Post by ghoran on 2008-06-08
Just a note:
I upgraded to Ubuntu 8.04 and this stopped working
I had to do a few things
- Change my passkey (gksu gedit /etc/bluetooth/hcid.conf). I also deleted my entries in the camera and re-searched for the device.
- Right click on BLueTooth file sharing and quit it
- Went to Applications/Accessories/BlueTooth File sharing

---

### Post by lisati on 2008-06-08
> **ghoran said:**
> 
Anyway, it now works great. I suspect that it would have worked before if I realized the USB 1.1 vs. USB 2.0

Been there, done that! I recently moved a PCI card from a computer that is dying to a newer machine to give it a couple of extra USB cards, and then wondered why I was getting warning messages about a couple of peripherals being able to work faster with other USB ports.  I eventually  realised that it was probably set for USB1.1 or something of that nature; swapping around what was connected where removed the warnings.

It's good to hear of success stories.

---

