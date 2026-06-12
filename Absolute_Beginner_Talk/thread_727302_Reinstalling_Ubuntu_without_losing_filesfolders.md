---
title: "Reinstalling Ubuntu without losing files/folders"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by Hookheathen on 2008-03-17
Hello,

My laptop has failed to open Ubuntu after the login screen and despite extremely helpful advice from contributors to this forum, their efforts failed. I have now been advised to do reinstall. HOWEVER, I am unsure how to do this without losing data - not only my files but also drivers (I have an IBM Thinkpad X40 and I had problems downloading the right WiFi driver).

So my question is how do I do this? Thanks.

---

### Post by jan quark on 2008-03-17
if you have a separate home partitions you can move your files there 

and during the installation process you just do not select the home partition for reformating

concerning your drivers and such I do not know if there will be present after a reinstallation

---

### Post by Duck2006 on 2008-03-17
Can you boot up in recover mode?

---

### Post by Hookheathen on 2008-03-17
> **jan quark said:**
> if you have a separate home partitions you can move your files there 

and during the installation process you just do not select the home partition for reformating

concerning your drivers and such I do not know if there will be present after a reinstallation

No I do not have a home partition, just the normal dual boot Win XP system. I presume I boot up from the CD, which option should I use? If going that route is there a way to backup before reinstalling?

---

### Post by jan quark on 2008-03-17
if you have a live CD just boot into the live session and you should be able to move your data either to a usb stick or an external drive or burn it to cd/dvd

---

### Post by Hookheathen on 2008-03-17
> **Duck2006 said:**
> Can you boot up in recover mode?

Regrettably no. I had great support from one contributor who tried every option known, including removing offending code and reinstalling. But after many hours success evaded us and he had to admit he was stumped. To save any more time he suggested the last resort - reinstall!!

---

### Post by Duck2006 on 2008-03-17
Use manual when it comes to partitioning when doing the install. Make your / partition, your swap partition and then your home partition.

---

### Post by Hookheathen on 2008-03-17
> **jan quark said:**
> if you have a live CD just boot into the live session and you should be able to move your data either to a usb stick or an external drive or burn it to cd/dvd

Stupid question, but where is my data stored? Can i select what data I move to a USB stick, or do I  have to go for the whole lot (in case my stick has insufficient space)?

---

### Post by Duck2006 on 2008-03-17
In your home folder/your username.

---

### Post by Oldsoldier2003 on 2008-03-17
> **Hookheathen said:**
> Stupid question, but where is my data stored? Can i select what data I move to a USB stick, or do I  have to go for the whole lot (in case my stick has insufficient space)?
well unless you've taken to storing data in a special place saving your /home/<username> is the folder to grab

---

### Post by Hookheathen on 2008-03-17
> **Oldsoldier2003 said:**
> well unless you've taken to storing data in a special place saving your /home/<username> is the folder to grab

Thank you Duck and Oldsoldier, will get to grips with this tomorrow and keep you posted.:)

---

### Post by mikeypc2006 on 2008-03-17
Why not boot into Windows XP (you said you dual booted, so I assume that Windows still works?), download the software to read ext2 partitions (will also read ext3 partitions), copy your /home folder over to the Windows partition, do what you need to, to back it up and reinstall Ubuntu?

---

### Post by Pijits_1 on 2008-03-17
It might be just when upgrading but I think that you can select your home directory during the install steps on the live cd.

 Again I only upgraded form 7.04 to 7.10 and did this which as far as i remember saved everything for me.

---

### Post by Duck2006 on 2008-03-17
> **mikeypc2006 said:**
> Why not boot into Windows XP (you said you dual booted, so I assume that Windows still works?), download the software to read ext2 partitions (will also read ext3 partitions), copy your /home folder over to the Windows partition, do what you need to, to back it up and reinstall Ubuntu?

If you are dual booting this may be the easy to do it.

---

### Post by roccity1 on 2008-03-17
can you boot into a terminal?like if you press ctl alt f2? If you ca nso this do you have interent access?

---

### Post by Hookheathen on 2008-03-18
> **mikeypc2006 said:**
> Why not boot into Windows XP (you said you dual booted, so I assume that Windows still works?), download the software to read ext2 partitions (will also read ext3 partitions), copy your /home folder over to the Windows partition, do what you need to, to back it up and reinstall Ubuntu?

XP still works. Your approach sounds most logical, as I am not risking wiping out data when exploring/using the live CD. What download software are you referring to for reading ext2 partition?

---

### Post by Mad_Duck on 2008-03-19
The ext2, ext3 reading software he might mean is called ext2ifs from: [http://www.fs-driver.org/]("http://www.fs-driver.org/"). it's donation-ware & seems to work fine, with the exception that for me XP writes a recycle bin & AVG tank on my linux partition. use at your own risk.

---

