---
title: "Booting from a DVD and other newb questions"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Aiello on 2007-06-14
I am going to download Ubuntu 7.04 from the Ubuntu website and I have some newb questions( this is the my first time using any operating system outside of Windows so don't flame!):
1. When I click the download, should I select to open the file or should I save it to my HDD on my computer? I am planing to boot it from a DVD and I don't want to mess up Windows XP.
2. Once I have the .iso burned to a DVD, how do I boot from it? I imagine that I put the DVD in my DVD drive... but I would be lost from there.
3. As long as I boot from the DVD, Ubuntu wont mess with Windows XP, right?

-Thanks!

---

### Post by shae on 2007-06-14
1. Definitely save the file.  It is just like any other file and will not harm XP.

2. Place the DVD in your drive and make sure your DVD drive is the first device in BIOS's boot order.

3.  When running the live CD, no changes will take place on XP unless you choose to install.

---

### Post by Aiello on 2007-06-14
> **shae said:**
> 2. Place the DVD in your drive and make sure your DVD drive is the first device in BIOS's boot order.

Thanks, but, um... How do you change the BIOS's boot order?

---

### Post by Aiello on 2007-06-14
Any thing about the BIOS's?
I guess Windows has held my hand so much I don't even know how to doing anything besides surf the web and download apps!

---

### Post by shae on 2007-06-14
[http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_boot_sequence_in_CMOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_boot_sequence_in_CMOS")

---

### Post by abn91c on 2007-06-14
for the bios reboot and watch the screen it will say press f2, del, f12, esc or some other similar key to enter set up. you can change the boot sequence there to DVD then HDD, it will tell you then to hit usually f10 to save the settings. Put DVD in the drive, reboot and go from there. A good programs to burn DVD, CD ISO's is Active ISO Burner, you can find it at [www.downloads.com](www.downloads.com). It will let you burn an image up to 32x without problems, at least for cdr's. I don't have a DVD burner so I don't know what kind if spreed you can get or how long it takes to burn the image. The program is free, has no file size limits.

---

### Post by Aiello on 2007-06-16
I burned the file I downloaded from Ubuntu.com onto a DVD using InfraRecorder( the .iso burning program Ubuntu.com recommended). When I put the DVD in my DVD/CD and selected the burn option, InfraRecorder said that it detected a DVD and wanted to if it should burn to the DVD media? I selected yes. It seemed to burn the file to the DVD without any problems. I then removed the DVD, restarted my computer, went into the BIO's, and made it so that the DVD/CD drive booted over the HDD. I then saved excited the BIOS's and the computer loaded XP. I inserted the DVD into my DVD/CD drive and rebooted the computer. After about 30 seconds of a black screen, a white flashing under score in the top-left corner, and some odd sounds coming from the computer, the HDD took over and the computer booted XP. I took out the DVD, reinserted it, and restarted the computer again. The same thing happened. In Windows XP, I took out the DVD, reinserted it, but did NOT restart. I went into My Computer to look at how much data was on the DVD. It said there was 0 bytes on the DVD and 0 remaining. Figuring I might have a problem with my DVD/CD drive, I put a game into it but it loaded without a problem.
Does anyone know if I am doing something wrong or have any suggestions? 
Thanks!

---

### Post by Aiello on 2007-06-16
Anything? Por favor?

---

### Post by RichPicker on 2007-06-16
Interesting. Not meaning to be condescending. Make sure the CD is inserted before changing the boot sequence. I'm using a Dell laptop, and with Windows or Ubuntu, I hold down the F2 key and then press the power on button, or the restart button. It boots to a screen where I do the boot sequence changes. Then save the changes, And then when it restarts, it boots from the CD.

---

### Post by Aiello on 2007-06-16
I did what you said to do and set the DVD/CD drive as the main boot (the floppy drive was the main before) and the same thing happened. Do you think I should try re-downloading the .iso and burn that to another DVD, or just use the currents .iso and burn that?

P.S.: This would be my last DVD so if I mess this one up I will be up a creek without a paddle for a bit. Also, when I burnt to the DVD, I just selected the WHOLE thing that I downloaded from Ubuntu.com. Should I have used WinRAR and selected a specific folder inside the downloaded?

Thanks!

---

### Post by forestpixie on 2007-06-16
No you don't need to use winrar - you need to burn the whole file as an .iso as you have. It helps to burn it at a slow speed.

Also you could try checking the hash with a file checker - md5sum I think.

You can find the hash number somewhere on the Ubuntu site. Could be a dodgy download!

---

### Post by forestpixie on 2007-06-16
Found this for you - 

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

hope that helps.

:)

---

### Post by Aiello on 2007-06-16
Ok, I did a hash check and everything turned out ok. I might have just had a bad burn. Hopefully, the next time I go to this website I will be running Ubuntu!

---

### Post by forestpixie on 2007-06-16
Go for it - burn it slow though!

:D

---

