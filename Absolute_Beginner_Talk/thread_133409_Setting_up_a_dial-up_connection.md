---
title: "Setting up a dial-up connection"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by kagi_chan on 2006-02-20
Hey guys,

I'm new to Ubuntu but I've been able to use Red Hat and Mandrake before.  Not much though.  Anyways, I still consider myself a beginner and am in dire need of your help...  

I have been hoping to set up my PC using Ubuntu but I don't know how to set up the dial-up internet... Any ideas how I can do this?  Any help would be very much appreciated...

Thanks...


kagi

---

### Post by bjweeks on 2006-02-20
What modem do you have?

---

### Post by kagi_chan on 2006-02-21
I'll check the box.. hehe :)  I'll let you know tomorrow.. is that ok? :)

---

### Post by bjweeks on 2006-02-21
Sure but if its a winmodem you might be SOL. I am not sure myself as I use cable.

---

### Post by kagi_chan on 2006-02-21
[QUOTE=bjweeks]Sure but if its a winmodem you might be SOL. I am not sure myself as I use cable.[/QUOTE]

How do i know if the modem is a winmodem?  I'm sorry if i sound so ignorant, I'm really new to this... :( :???:

---

### Post by MadL on 2006-02-21
The Ubuntu wiki has some info on winmodems and setting up dial-up connections [here]("https://wiki.ubuntu.com/DialupModemHowto"). If it's an internal modem, there's pretty good odds it's a winmodem. The other major type of modem is a hardware modem, which is usually external.

---

### Post by CameronCalver on 2006-02-24
Hey i got ubuntu recently and i have a old 28k dial up external modem can  u tell me how to set it up

---

### Post by StefanoCole on 2006-02-24
CameronCalver, as stated by MadL there is a very good wiki at: [https://wiki.ubuntu.com/DialupModemHowto]("https://wiki.ubuntu.com/DialupModemHowto")
read carefully the sections: Hardware modems and Configuring the dialup connection to your provider

Stefano

---

### Post by CameronCalver on 2006-02-24
Hey Stefano well i red it but i do not no wat com port the modem is and it does not auto detect then when i go to mozilla it doesnt try to dial how do i get it to dial

---

### Post by kagi_chan on 2006-02-27
[QUOTE=MadL]The Ubuntu wiki has some info on winmodems and setting up dial-up connections [here]("https://wiki.ubuntu.com/DialupModemHowto"). If it's an internal modem, there's pretty good odds it's a winmodem. The other major type of modem is a hardware modem, which is usually external.[/QUOTE]

Hey there, I was wondering you'd know if it's a Winmodem or a LinModem?
Is it the brand?

I'm currently using an internal modem which i bought just recently.  It's a PCI brand...  Are PCI brands Winmodems or Linmodems?  thanks..,..

I still have to go look for the box.. grrr...

---

### Post by cheezit on 2006-02-27
I can tell you how I can see my modem in Device Manager:

The tool bar - top left on your screen: System>Administration>Device Manager.  In Device Manager, there should be a list of devices Ubuntu recognizes in your computer.  Left click (highlight) on your Modem.  The "Device" tab should show you your modem "Vendor" and "Device" type.

After I found the "Vendor" I searched their web pages for "linux drivers" and was able to find the appropriate driver.

Interestingly enough after I learned to install the modem driver, make a connection, and get on the web -- I ran the "Update Manager" which modified the Linux Kernal from 2.6.12-9-386 to 2.6.12-10-386.  My modem quit working.  I had to "uninstall" my first modem driver and "install" another one

---

