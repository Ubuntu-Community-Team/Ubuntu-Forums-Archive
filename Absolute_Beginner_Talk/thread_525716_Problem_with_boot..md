---
title: "Problem with boot."
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by zeehat on 2007-08-14
I just installed Ubuntu on a 10 GB HD.  I have a 80 GB HD Windows boot, and an 250 GB Storage Drive.  Now nothing boots.  In my bios the Ubuntu is set to master 0, cd rom drive master 1, and my two other drives are master 2,3.  How can I make Ubuntu / Windows boot?

---

### Post by oilchangeguy on 2007-08-14
have you tried to boot the computer by just using one drive a a time? (unplug the windows, or ubuntu drive)

---

### Post by zeehat on 2007-08-14
I think that could be it, but instead I will set one off and the other on. [boot drives]  I figured out the initial problem, and it boots to windows.  I just want to know how to boot to Ubuntu instead of Windows now.

---

### Post by oilchangeguy on 2007-08-14
have you turned off, or unpluged the windows drive to see if ubuntu will boot?

---

### Post by Jimmyfj on 2007-08-14
> **zeehat said:**
> I just installed Ubuntu on a 10 GB HD.  I have a 80 GB HD Windows boot, and an 250 GB Storage Drive.  Now nothing boots.  In my bios the Ubuntu is set to master 0, cd rom drive master 1, and my two other drives are master 2,3.  How can I make Ubuntu / Windows boot?

In your BIOS you should have an option to select which drive is First Boot device. Have you tried switching the two disks Win/Ubuntu Ubuntu/Win on the boot sequence? 

If this doesn't work try: fdisk /fixmbr on your Windows disk and see if it boots up then.

---

### Post by zeehat on 2007-08-14
You are correct Jimmy.  Thank you all for dealing with my silly problems. I'm so happy Ubuntu booted for the first time by itself:D:D:D

---

### Post by oilchangeguy on 2007-08-14
> **Jimmyfj said:**
> In your BIOS you should have an option to select which drive is First Boot device. Have you tried switching the two disks Win/Ubuntu Ubuntu/Win on the boot sequence? 

If this doesn't work try: fdisk /fixmbr on your Windows disk and see if it boots up then.

read post #3. the user states windows will boot.

---

### Post by oilchangeguy on 2007-08-14
> **zeehat said:**
> You are correct Jimmy.  Thank you all for dealing with my silly problems. I'm so happy Ubuntu booted for the first time by itself:D:D:D

great, but you've still got problems. you should not have to manually switch drives. or make bios adjustments each time just to get one, or the other os to start.

---

### Post by zeehat on 2007-08-14
I think it's ok.  Let me explain: I needed to put priority of the drives.  I put Ubuntu in first priority.  When it loads it goes to a black screen asking me if I would like to load the Ubuntu kernel, or "other Operating Systems" - which is Windows.  I simply use my keyboard to search up and down, and click on the OS I want to use.  Works great, I am posting for the first time in my installed Ubuntu.

---

