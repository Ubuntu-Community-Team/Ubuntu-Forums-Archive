---
title: "My Screen Goes Black...help Please"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by BETOCORELLA on 2007-07-22
Hi Well I Just Installed Ubuntu 7. O4 N It Asked Me 2 Restart. So I Did N The Screen Starts Turning Tan To Black. Its Been Turning Black 4 A While Now. Almost 4 Hours Now. What Gives? Please Help Me. Im Using My Phone 2 Send This Cuz I Dnt Got Internet. Oh Ya Laptop Is A Compaq Presario 558us Please Help

---

### Post by 67GTA on 2007-07-22
How far does it get into the booting sequence when it turns black? Have you tried rebooting again?

---

### Post by Hobo Joe on 2007-07-22
Can you boot into recovery mode?

If you can, do your best to follow these instructions:

```

sudo aptitude install envy
(I'm pretty sure it's in the repos...)
envy -t

```

Then select the option that says "install <your card manufacturer> drivers"
Then just let it run, and make sure to say YES to the option that asks to configure your xorg

---

### Post by BETOCORELLA on 2007-07-22
It Says Grub 1.5 Stage. Then It Goes Into Tan Screen Then Turns Black

---

### Post by BETOCORELLA on 2007-07-22
Ya I Can Go 2 Recovery Mode, All It Say Is This Aptitude Does Not Have Super Cow Powers.....

---

### Post by 67GTA on 2007-07-22
You can use apt-get instead of aptitude, but the envy script installs 3d graphics drivers for ATI/Nvidia,etc. That should not cause this. Boot into recovery mode, log in, and type "startx". That will attempt to start your xserver(graphical interface), and should give you some kind of error message to help diagnose the problem.

---

### Post by BETOCORELLA on 2007-07-22
Ok First Of All How Do U Log In? Secondly Startx Took Me 2 Dat Tan Then Turning Black Again.  Ok So I Go In Recovery Mode Then What?

---

### Post by BETOCORELLA on 2007-07-22
Ok I Got Into The Log In.

---

### Post by 67GTA on 2007-07-22
When you installed you had to type in a user name and password. When you boot into recovery mode just type your user name and password(password is hidden just type it and hit enter) to log in when it prompts you to do so. Then type "sudo startx". You will have to re-enter your password for sudo to work. If that does not give any error messages then boot back into recovery mode and run "sudo dpkg-reconfigure xserver-xorg". Go through all the steps and make sure your monitor specs are correct(resolution,refresh rates,etc.) Use "vesa" for your graphics driver. Other than that it is probably hardware related. We need more info on your comp for that.

---

### Post by BETOCORELLA on 2007-07-22
When U Reconfigure The Xserver Does It Save By Itself?

---

### Post by BETOCORELLA on 2007-07-23
Ok It Loads A Little Faster But Its Da Same... It Loads The Live Cd Prettyquick Cant I Copy That Configure?

---

### Post by 67GTA on 2007-07-23
It will ask you if you want to save at certain points. Just answer yes, and it will rewrite you xorg.conf file. You can rerun the reconfigure command again if you need to.

---

### Post by 67GTA on 2007-07-23
> **BETOCORELLA said:**
> Ok It Loads A Little Faster But Its Da Same... It Loads The Live Cd Prettyquick Cant I Copy That Configure?

It depends. If the live cd xorg.conf file was correctly setup you can mount your Ubuntu partition, and copy the live cd xorg.conf into the Ubuntu partiton. There should not have been much difference though. Look through them both and see if there is something different with the monitor or graphics card settings. Also look at the modules that are set to boot in the modules section.

---

### Post by BETOCORELLA on 2007-07-23
Ok I Got It Lol Thanx Lol Ok 2 Questions How Do I Make The Gdm Run? The Gnome Display Manager? And How I Activate The Desktop Effects? I Get A White Screen For That

---

### Post by BETOCORELLA on 2007-07-23
Ugh Nevermind I Restarted The Dam Laptop N I Got The Same Crap. It Worked But It Went Back

---

### Post by 67GTA on 2007-07-23
I assume you got everything to boot if your playing with the desktop effects. GDM is where you login. It had to start for you to log in and boot into the desktop. To use desktop effects, you have to have a 3D graphics card that supports it. What graphics card are you running? Almost any will work except for some ATI Radeon cards. Go to SYSTEM>ADMINISTRATION>RESTRICTED DRIVER MANAGER and enable the driver for your card and follow the directions(if supported). After you reboot you should be able to use desktop effects.

---

### Post by BETOCORELLA on 2007-07-23
Ok The Only Way I Can See My Desktop Is If I Go Into Recovery Mode N Reconfigure The Xorg N Then Im In As Root User In Desktop. N I Still Get That Message Saying Im Using A Different Display Manager.....

---

