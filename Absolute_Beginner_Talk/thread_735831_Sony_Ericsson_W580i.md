---
title: "Sony Ericsson W580i"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by ZOOstation on 2008-03-26
I just bought a Sony Ericsson W580i, and when I connect it via USB to transfer files, the computer doesn't seem to detect it. It's listed in my Preferences >> Hardware Information, but "sudo fdisk -l" doesn't show anything beyond the sda.

I really don't know how to use the phone in conjunction with the laptop. Help not only with getting started but with then loading a song onto the phone would be greatly appreciated.

---

### Post by abhijitvalluri on 2008-03-26
I too have a similar problem. I have Sony Ericsson W700i. I have a lot of important data already stored in my phone. Now I'd like to transfer it to my Gutsy and upload some songs on to it. Please help.

It would be appreciated if you suggest a method where I don't lose my data.
Thanks in advance.

---

### Post by abhijitvalluri on 2008-03-26
Hmm... It seems to be strange. I kept my phone connected for 10-15 mins. to the computer via usb cable. It didn't detect it  for 5 odd mins. But now it seems to detect it perfectly!!! :)
Seems to me that it's because I hooked it up for the first time to my ubuntu box that it took so much time. Anyway, I'll try once again later and see if it takes time or it detects it immediately [ or doesn't detect at all :*( ]

Thanks anyway

---

### Post by kpkeerthi on 2008-03-26
I use [bluetooth]("https://help.ubuntu.com/community/BluetoothSetup") to transfer files to/from my Sony Ericsson Z550i. Its as easy as it can be.

---

### Post by erginemr on 2008-03-26
I have two links your you to try:
[http://thpinfo.com/2006/k700i-linux/](http://thpinfo.com/2006/k700i-linux/)
[http://wammu.eu/](http://wammu.eu/)

The second link, **Wammu **is very promising for Sony-Ericsson phones and it is installable via Synaptic.

---

### Post by pwtico on 2008-05-30
I had the same issue--plugged in my W508i via USB cable and nothing happened.  I rebooted my laptop with the cable plugged in, and then the phone's M2 memory card was mounted and showed up on my desktop labeled "PHONE CARD".  Haven't had any problems since then copying music files onto the phone.

I also installed wammu, which gives some access to the phone information and internal memory.  The enabled features are described on this page: [http://cihar.com/gammu/phonedb/sony-ericsson/900/](http://cihar.com/gammu/phonedb/sony-ericsson/900/) .

---

### Post by strungoutfan78 on 2008-06-20
I don't know if this helps anyone at all but I have been dealing with this issue as well.  I found that my problem was when I plugged in my phone I kept selecting 'File Transfer' mode.  Wrong.  Do not select anything.  This is the only way I was able to get /dev/ttyACM0 and /dev/ttyACM1 to appear.  Since then it connects fine through usb.

My only problem now is that I can't access any info stored on the SIM card.  Only data in the phone's internal memory.

---

### Post by sponsoredwalk on 2008-06-20
try this in a terminal,

mount /media/sdc1

and/or 

mount /media/sdd1

My sony ericsson used to be instantly recognised by my computer but out of the blue it stopped so now i have to hook my phone up to my pc _and wait for it to load up_, type both of the above commands into the terminal, take my phone _out_ again, then put it back in again, It should load up.

---

