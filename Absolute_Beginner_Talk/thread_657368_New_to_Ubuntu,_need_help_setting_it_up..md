---
title: "New to Ubuntu, need help setting it up."
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by Zivix on 2008-01-03
Now that I have Ubuntu on a CD, is there anywhere I can find a guide on how to set up and enter Linux mode from start up with the CD in my disk drive?

(I currently use Windows XP)

A friend who uses VISTA told me to press F12 to go into Linux on start up, but when I do.. It'll either do nothing and start up Windows XP up, or _rarely_ give me this message:


Windows could not start because the following file is missing or corrupt:
<windows>/system32/ntokrnl.exe
please re-install a copy of the above file


I'm not sure what that means, or what to do to fix that and get Ubuntu up and running.


Any help will be much appriciated :)

---

### Post by Kzin on 2008-01-03
> **Zivix said:**
> Now that I have Ubuntu on a CD, is there anywhere I can find a guide on how to set up and enter Linux mode from start up with the CD in my disk drive?

(I currently use Windows XP)

A friend who uses VISA told me to press F12 to go into Linux on start up, but when I do.. It'll either do nothing and start up Windows XP up, or _rarely_ give me this message:


Windows could not start because the following file is missing or corrupt:
<windows>/system32/ntokrnl.exe
please re-install a copy of the above file


I'm not sure what that means, or what to do to fix that and get Ubuntu up and running.


Any help will be much appriciated :)

Hey there, need to know what you want in the end and how far you've made it.  Do you want to completely remove windows?  Have you been able to boot from the Ubuntu CD?

---

### Post by LaRoza on 2008-01-03
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

---

### Post by Zivix on 2008-01-03
I'm wanting to keep Windows XP, but am wanting to make it to where I can boot up and enter Ubuntu Linux from the Dvd/CD when I need or want to.

I havn't been able to boot from the CD yet.
My friend  has Ubuntu  working like that for him now, but he uses a VISTA instead of XP.

---

### Post by PeterJS on 2008-01-03
> **Zivix said:**
> He reccomended Ubuntu to me for many reasons, mostley to increase computer performance speed for gaming.

There are lots of good reasons to install Ubuntu, security, desktop bling, oss love. But gaming performance isn't one of them. Things running under wine are only able to use up to DX8, so things may run faster but that's only because you're limited to low res textures and reduced effects.

As to booting the liveCD the trick is that you have to change the boot order of the devices on your system so that it trys to boot from the CD before the hard drive. This varies from system to system the F12 that your friend recommended is the most commonly used key for bringing up the boot order menu. When your system first starts, before loading windows, at the bottom of your screen it should list a couple of the F keys for boot options, you're looking for the boot order option, or setup to permanently change the boot order.

---

### Post by Zivix on 2008-01-03
I think Dual-Booting from a CD is what I'm looking to do.

---

### Post by PeterJS on 2008-01-03
Generally people don't dual boot from a CD, it's doable and won't make any permanent to the system, but most people use the live CD to test hardware and install to a second partition to dual boot from the hard drive.

That said, have you gotten the CD to boot yet?

---

### Post by insertAlias on 2008-01-03
On my machine, if you hold F2 immediately when boot you will get into the BIOS setup.  There you can change the boot order.  F12 gives you a one-time boot device selection list.  But it sounds like it is different on your machine, so on the boot splash screen does have any text?  It may be along the bottom or at the top left or right.  It may say something like boot options, or options, or BIOS setup or anything.

---

### Post by Kzin on 2008-01-03
> **Zivix said:**
> Windows could not start because the following file is missing or corrupt:
<windows>/system32/ntokrnl.exe
please re-install a copy of the above file


Have you already installed Ubuntu and are now having trouble booting your XP normally?

---

### Post by Zivix on 2008-01-03
I couldn't figure out why Ubuntu wouldn't work for me off the CD. So I downloaded it from the main page of Ubuntu's website. Afterwards I turned off my PC, turned it back on and I still get nothing trying to bring up the Boot Menu.  


What do I do next after downloading it?



Also, does anyone know which specific key brings boot menu for Windows XP?

---

### Post by Sef on 2008-01-03
> I couldn't figure out why Ubuntu wouldn't work for me off the CD. So I downloaded it from the main page of Ubuntu's website. Afterwards I turned off my PC, turned it back on and I still get nothing trying to bring up the Boot Menu.


1) Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the download? (To check it is good.)

2) Did you burn the iso as an iso and at 4x or less? (Faster can corrupt the burn.)

---

### Post by Xavieran on 2008-01-03
> **PeterJS said:**
> There are lots of good reasons to install Ubuntu, security, desktop bling, oss love. But gaming performance isn't one of them. Things running under wine are only able to use up to DX8, so things may run faster but that's only because you're limited to low res textures and reduced effects.
.
You should see Quake 4 under Linux :)...your gaming will be great if you use mainly Linux games...and there are plenty of OSS games out there...try Sauerbraten...

XP doesn't have a boot menu...
But as said before when you first boot up there should be a splash screen that says to "Press this key to access startup menu" or something along those lines...press that key and choose CDROM first...

---

### Post by RRS on 2008-01-03
> **Zivix said:**
> What do I do next after downloading it?

Also, does anyone know which specific key brings boot menu for Windows XP?
After downloading you need to write the ISO image to a cd. Follow the instructions [here]("http://psychocats.net/ubuntu/iso#burning"). This is a section of the site that LaRoza linked to in his post above which contains a lot of other usefull information also.

The "boot menu" referred to is in the computers Bios and needs to be accessed before windows begins to boot. The specific key needed is according to the hardware installed and doesn't matter what operating system or other software is being used.

When you turn your computer on the first screen seen is usually the mfg's logo; Dell, HP, etc. or maybe the name of the company that made the motherboard.

It's here that you'll usually see something such as "F12 for setup" which will open the Bios setup pages instead of booting to windows. After finding the appropriate page you need to select "cd" or maybe cdrom as the first boot device.

I hope this makes things a bit clearer for you and I'd recommend you review [Aysui's]("http://psychocats.net/ubuntu/index") site a bit in case I've left anything out. And don't hesitate to ask if you have more questions.

---

### Post by Zivix on 2008-01-03
Cool, by the way.. Is there a way I can slow down or stop the boot up screens/menus from moving so fast that I can read them a little easier and make sure I don't miss any messages?

---

### Post by PeterJS on 2008-01-04
> **Xavieran said:**
> You should see Quake 4 under Linux :)...your gaming will be great if you use mainly Linux games...and there are plenty of OSS games out there...try Sauerbraten...


I know, but that's more the exception than the rule. I've got native UT2k4 installed, and it's very pretty. And I love running it windowed and bending it around the corner of my desktop cube just because I can, it's hard to play when you can only see half the screen at a time, but it sure is fun to brag about.

> **Zivix said:**
> Cool, by the way.. Is there a way I can slow down or stop the boot up screens/menus from moving so fast that I can read them a little easier and make sure I don't miss any messages?

Do you mean the bios messages about boot options? because those settings are burned in to the motherboard when it was manufactured and there's not much that can be done about it. The ubuntu boot messages on the other hand can be tweaked with after the install is done.

---

