---
title: "error during updates"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by Chelives1928 on 2008-02-28
I've just installed 7.10 on my 500 gb partition I have a 30 gb partition for ubuntu and the rest is windows.  I've installed ubuntu with no problems but then when the computer is restarted and I'm finally on the desktop I'll choose to update and that's where the problem is.  I've decided to install all the updates to keep my system ready and after the downloading and about halfway through the installing the computer will automatically restart.  Next when it goes back to the desktop all it shows is the typical orange backround but no icons.  any suggestions?

---

### Post by overdrank on 2008-02-28
> **Chelives1928 said:**
> I've just installed 7.10 on my 500 gb partition I have a 30 gb partition for ubuntu and the rest is windows.  I've installed ubuntu with no problems but then when the computer is restarted and I'm finally on the desktop I'll choose to update and that's where the problem is.  I've decided to install all the updates to keep my system ready and after the downloading and about halfway through the installing the computer will automatically restart.  Next when it goes back to the desktop all it shows is the typical orange backround but no icons.  any suggestions?

HI and you can try and boot into recovery mode which is usually the second choice on the grub and login and update  there (command line)```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
It may ask you to 
```
sudo dpkg --configure -a
or
sudo apt-get install -f 
```

---

### Post by Chelives1928 on 2008-02-28
How long does the whole process take?  I did the commands you told me and it hung up on one for like 20 min.  I don't remember exactly what it was doing but it said it was creating some image.

---

### Post by overdrank on 2008-02-28
> **Chelives1928 said:**
> How long does the whole process take?  I did the commands you told me and it hung up on one for like 20 min.  I don't remember exactly what it was doing but it said it was creating some image.

Hi and when you ran the upgrade command it should ask you to answer y yes or n no. Then you should see a progress on the download of each file.

---

### Post by Chelives1928 on 2008-02-28
the first command i put in was apt update and then it said i couldn't until i configured dpkg so I did the command you gave me for that and that is where it hung up towards the end it was creating some img.

---

### Post by overdrank on 2008-02-28
> **Chelives1928 said:**
> the first command i put in was apt update and then it said i couldn't until i configured dpkg so I did the command you gave me for that and that is where it hung up towards the end it was creating some img.

ok try the command sudo apt-get install -f

---

### Post by Chelives1928 on 2008-02-28
Okay I went back to do the command you told me and now it won't let me get into the recovery console.  When it is loading it halts and has this; Please append a correct "root" here are available options...But I can't choose anything or trype anything.  

It also says Kernal Panic unable to mount root fs on unknown.

---

### Post by overdrank on 2008-02-28
> **Chelives1928 said:**
> Okay I went back to do the command you told me and now it won't let me get into the recovery console.  When it is loading it halts and has this; Please append a correct "root" here are available options...But I can't choose anything or trype anything.  

It also says Kernal Panic unable to mount root fs on unknown.

Ok can you boot normally and then use the keys alt, ctrl, F1 and this will bring you to the virtual terminal and try the updates again. This is strange and did you check the cd for errors before the install?

---

### Post by Chelives1928 on 2008-02-28
yeah i did cuz this happened before so I figured I would check the cd this time but no luck.

---

### Post by overdrank on 2008-02-28
> **Chelives1928 said:**
> yeah i did cuz this happened before so I figured I would check the cd this time but no luck.

Ok then the cd had errors. Then you may try and download from a different location and you may want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 
Before burning and then 
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Chelives1928 on 2008-02-28
okay i'll go ahead and bittorrent the newest ubuntu and try again tomorrow i'll post if i get the same problems.

---

### Post by overdrank on 2008-02-28
> **Chelives1928 said:**
> okay i'll go ahead and bittorrent the newest ubuntu and try again tomorrow i'll post if i get the same problems.

Ok and as I understand it the bittorrent with do the checksum automatically, so it may be a issue when burning the cd.

---

