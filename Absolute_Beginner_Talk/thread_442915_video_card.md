---
title: "video card"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by krisfrajer on 2007-05-14
I have latest version ubuntu + amd64 + radeaon 9600xt. I am trying to figure out the installation of this video card. Maybe you have seen my other posts. Here I have a quick specific question. When choosing my drivers from the amd webpage... I have the option of choosing drivers from linux x86 or Linux x86_64 (keep in mind I have ADM64). Then should I go for the drivers with Linux x86_64?

I jist want to make sure this is correct before I proceed with the installation. Thxs,

---

### Post by Zzl1xndd on 2007-05-14
if your using 7.04 then if you go to System > admin > Restricted  driver Manager it should already be listed and just need to be turned on. But if you wanna download from the site if you are using 32bit Ubuntu then use X86 if 64bit then pick 64

---

### Post by irish_flu on 2007-05-14
You can run either 32-bit Ubuntu or 64-bit Ubuntu on a 64-bit AMD; it's the version of Ubuntu you have that will be the deciding factor in which driver you choose to download.

---

### Post by krisfrajer on 2007-05-14
I figure it out:

cristian@NARUTO:~$ uname -a
Linux NARUTO 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 **[COLOR="Red"]x86_64[/COLOR]** GNU/Linux

---

### Post by krisfrajer on 2007-05-14
> **tweakedenigma said:**
> if your using 7.04 then if you go to System > admin > Restricted  driver Manager it should already be listed and just need to be turned on. But if you wanna download from the site if you are using 32bit Ubuntu then use X86 if 64bit then pick 64

I went to the restricted drive manager and there is the ati video card but it is using a standard name **instead** of the radeon 9600XT which is the video card that I have. Furthermore, when I enable it I run into problems. I am trying to install this video card and it has taken me all weekend and I did not got into the solution. Have anybody ever felt like throwing the computer through the window?

---

