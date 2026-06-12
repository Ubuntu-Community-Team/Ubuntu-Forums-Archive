---
title: "Check Cd - Error"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Bikespot on 2008-01-30
I put the Ubuntu server 7.10 on a cd and booted up my computer.

Click on Check Cd for defects

It ran the test and it came up with this

[COLOR="Red"][!] Configuring Cd-rom-checker-menu [/COLOR]

The
./pool/main/l/lnux-source-2.6.22/linux-headers-2.6.22-14_2.6.22-14.46-all.deb file failed the MD5 checksum verification.
Your cd-rom or this file may have been corrupted



What went wrong? Possibly something when burning the cd?

---

### Post by taurus on 2008-01-30
How fast did you burn the ISO image?  If you set it to burn at a default, try burning it again except at a slower speed like 4x if you can.

---

### Post by bumanie on 2008-01-30
the md5 checksum is a goup of numbers and letters attached to a file, if the downloaded file's md5 checksum is different to the md5 checksum on the download site, it shows that that the download was corrupted for some reason.

---

### Post by bumanie on 2008-01-30
Go here for more information
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by RedSquirrel on 2008-01-30
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

I recommend you check the md5 sum of the iso file before burning again.

---

### Post by Bikespot on 2008-01-30
I checked the

md5 sum

and the numbers match. 

Must be when i burned the file. I used some other burn program before.

Now i'm using infrarecorder.

Here is what i get when i click Actions - Burn image 

Then i selected the server image.

Is this right? 

[http://img168.imageshack.us/my.php?image=burnscreenje5.png](http://img168.imageshack.us/my.php?image=burnscreenje5.png)

If so i will continue.

---

### Post by taurus on 2008-01-30
See if you can get the write speed down to the lowest setting.

---

### Post by Bikespot on 2008-01-30
> **taurus said:**
> See if you can get the write speed down to the lowest setting.

I checked what speeds there is

-Maximum
-40x

Should i do 40x?

---

### Post by bumanie on 2008-01-30
The slower you burn the cd , the less likely it is to have errors. Many suggest burning as slow as 4x to ensure an error free burn.

---

### Post by Bikespot on 2008-01-30
> **bumanie said:**
> The slower you burn the cd , the less likely it is to have errors. Many suggest burning as slow as 4x to ensure an error free burn.

Alright i will burn it at 4x

What about Write method.

Its set on Session-at-once  is that fine?

---

### Post by bumanie on 2008-01-30
Honestly have never heard of the term "Session at once", so i can only say, "Try it and see what happens." I assume it really means single seesion rather than a multi-session disc.

---

### Post by Bikespot on 2008-01-30
I will give it a try.

Then i will run the Cd check.

---

### Post by Bikespot on 2008-01-30
I burned the cd , then rebooted and check the cd.

It worked, no errors this time.

:) Thanks for all those who helped.

Just need to wait for my 2.0 Usb port and i will install ubuntu.

---

