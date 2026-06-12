---
title: "Sound"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by AKPAKP on 2008-03-29
How do I install an application...in Ubuntu??

I need to install Totem Media Player 
Can I play WMA & MP3???

Help

---

### Post by Inxsible on 2008-03-29
Go to Applications>>Add/Remove and search for Totem and you can select it to install.

You can play mp3 provided you install the proper codecs.

---

### Post by AKPAKP on 2008-03-29
I am not able to connect to the net via Ubuntu

---

### Post by AKPAKP on 2008-03-29
i downloaded the tar.gz file thru the laptop....i burned it on cd 
now how to install from it???

---

### Post by Hutom on 2008-03-29
Go to** System > Administration > Synaptic Package Manager **. Enter password. Then search for **Totem**. You will find Totem Gstreamer. Mark it for installation and then apply. 

You may also install vlc player. Its works better than Totem. At least I think so.

You may also need to install some codec. 

Good luck.

---

### Post by AKPAKP on 2008-03-29
It Says its alredy installed & asks to mark for reinstalling

---

### Post by rajaram_s on 2008-03-29
If you dont have direct internet connection at your place, you can get tar balls ie., .tar.gz packages and install softwares.

If you have a tar ball, first extract it to a folder. The from termnal, navigate to the folder and give the command
./configure

Once, the configure runs successfully, ie., doesnt return any errors, give

make install

This should install the software, if all dependencies are satisfied.

The other and better way to install softwares offline is to use .deb packages of the software. Again, here dependencies are an issue. You can install deb packages, just by double clicking them.

---

### Post by AKPAKP on 2008-03-29
i did what you said

At last it said
configure:errors:Package requirements(gstreamer-plugins-base-0.10)were not met

---

### Post by Inxsible on 2008-03-29
It would be a lot easier, if you had internet on the ubuntu machine.

Why does your internet not work ?

---

### Post by AKPAKP on 2008-03-29
I dont know how to configure it...

I dont know the 
ISP Phone no.

---

### Post by Hutom on 2008-03-29
If it is already installed then you shouldbe able to open Totem. It should be called the **movie player**. Locate it in Applications > Sound and video > Movie Player. Try to open an MP3 file. 

You may also install **vlc player** through Synaptic Package Manager. That should work.

---

### Post by AKPAKP on 2008-03-29
yes it is installed ......but it asks to instal gstreamer plugin to play mp3

---

### Post by AKPAKP on 2008-03-29
there is no vlc player option in synaptic package

---

### Post by Hutom on 2008-03-29
Check 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by AKPAKP on 2008-03-29
i dont have a direct internet connection .....

i saw that page yesterday also...but didnt find any way...

---

### Post by Hutom on 2008-03-29
You don't have internet? Then how are you online?

---

### Post by AKPAKP on 2008-03-29
i'm connected thru my laptop Ubuntu is in my PC

---

### Post by Hutom on 2008-03-29
Try to configure internet in your Ubuntu machine. That will make things easier for you.

---

### Post by AKPAKP on 2008-03-29
How to do that??

---

### Post by Inxsible on 2008-03-29
Which network card does your computer have ? If your computer has an Ethernet port, just plug it in the modem.

---

### Post by Hutom on 2008-03-29
System > Administration > Network

---

### Post by AKPAKP on 2008-03-29
How do I know that...

I have an external ADSL modem....

---

### Post by Inxsible on 2008-03-29
> **AKPAKP said:**
> How do I know that...

I have an external ADSL modem....yes, but does your computer have an ethernet port?

---

### Post by AKPAKP on 2008-03-29
Yes i connect the modem to the LAN port behind the back of the CPU.....that is the ethernet port i guess...

---

### Post by AKPAKP on 2008-03-29
with windows on it i was able to connect...hope tat is helpful to you to know about ethernet port

now i tried to connect in ubuntu but was unsucessful...

---

### Post by AKPAKP on 2008-03-29
Help!!!

---

### Post by Hutom on 2008-03-29
I guess your real problem is to configure internet in Ubuntu. If so then check other threads for that. You may start another thread for that. By the way, what kind of internet connection are you using?

---

### Post by AKPAKP on 2008-03-29
BSNL Broadband

---

### Post by AKPAKP on 2008-03-29
Hey  you are frm delhi ...you can really help me....

---

