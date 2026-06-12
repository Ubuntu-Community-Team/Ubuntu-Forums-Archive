---
title: "Problem Loading UBUNTU HEEEEEEEEEEEELP!"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by TheSonOfLiberty on 2008-03-24
Hello! I'm trying for days to install ubuntu 7.10 on my laptop!

I have used the alternative cd because with the normal cd couldn't make a normal installation. 

With the alternative cd the installation completes succesfully but when the linux loading for first time the progress stuck's at this point:

'**Starting BlueTooth Services.**

 I have try the recovery mode with the code **gdm start** and I have succesfully loged in graphical enviroment. There is a submenu that handles services "**services-admin** but when I'm click on it, or writting the command **services-admin** in the terminal, it prompts me for administrator password and then it prompts me that I can't access the services. The password is correct. 

My laptop characteristics are:

Core 2 Duo 1.83 GHz
1GB Ram
80GB HD
Intel 945 Chipset Family
Intel 945GM On Board Graphics with 128 MB sheared Memory.

Please! If there is anyone out there! PLEASE! HELP ME!!!!!!!!

Thanks to everyone who helped me so far!!!!!!

---

### Post by OffAxis on 2008-03-24
Don't multi-post.
If anything name your thread better; neither of your current titles are very descriptive; thus, no one scanning the forum knows what your issue is.

---

### Post by TheSonOfLiberty on 2008-03-24
> **OffAxis said:**
> Don't multi-post.
If anything name your thread better; neither of your current titles are very descriptive; thus, no one scanning the forum knows what your issue is.

Sory just a mistake!! I'm just writting the title and accidentaly I pressed ENTER!:(

---

### Post by forestpixie on 2008-03-24
You accidentally wrote 'Problem Loading UBUNTU' - twice ;)

---

### Post by arochester on 2008-03-24
Does your laptop have a make and model?

---

### Post by Calash on 2008-03-24
How long did you wait for the bluetooth services?  It may take a minute or two before ti continues if it is having problems with the device.

Also, what errors were you getting from the live cd?  It may be an indication that some of the hardware has issues out of the box with Ubuntu.

---

### Post by TheSonOfLiberty on 2008-03-24
> **Calash said:**
> How long did you wait for the bluetooth services?  It may take a minute or two before ti continues if it is having problems with the device.

Also, what errors were you getting from the live cd?  It may be an indication that some of the hardware has issues out of the box with Ubuntu.

UP TO 15 Minutes. Everything stuck's when the bluetooth services startting. With THe LIVE CD the progress bar just stuck at the end when trying to install UBUNTU. I can't istall the ubuntu with the Live Cd.

With the alternative cd the installation is normal but I can't boot. The only way to boot is the recovery mode 
and the menu with the services is not accesible to me! I'm Confused!:confused:

---

### Post by TheSonOfLiberty on 2008-03-24
> **forestpixie said:**
> You accidentally wrote 'Problem Loading UBUNTU' - twice ;)

YEP! Because I'm trying to find similiar posts by writting the title again in the title bar! and ACCIDENTALLY THE ENTER button fall down!:lolflag:

---

### Post by forestpixie on 2008-03-24
Probable best to search then - either the forums or with uboontu - which I use 

[www.uboontu.com](www.uboontu.com) - it uses google and takes some of the pressure of the buntu servers I believe and you can get a toolbar search thingy wotsit.

I had an accidentally falling down enter button once - lost all my files! I'd get your's seen to before it cause a problem

Ok - first result from "turn off blutooth from recovery" search in uboontu gets this 

[http://ubuntuforums.org/showpost.php?p=3861647](http://ubuntuforums.org/showpost.php?p=3861647)

post 9 - 
 > Re: Disable Bluetooth services from terminal plzz
i couldnt do anything of what u all said but thanks anyway
i solved the problem
i booted in recovery mode
than i wrote this code:

[QUOTE]sudo pico /etc/init.d/bluetooth
this opens the bluetooth code so i wrote at the top of the code :
exit 0 and saved reboot and it worked

than i was able to disable blutooth services from desktop and returned the code to what it was

hope this helps anyone who had my problem[/QUOTE]

Hope that is of some use

---

### Post by TheSonOfLiberty on 2008-03-26
> **forestpixie said:**
> Probable best to search then - either the forums or with uboontu - which I use 

[www.uboontu.com](www.uboontu.com) - it uses google and takes some of the pressure of the buntu servers I believe and you can get a toolbar search thingy wotsit.

I had an accidentally falling down enter button once - lost all my files! I'd get your's seen to before it cause a problem

Ok - first result from "turn off blutooth from recovery" search in uboontu gets this 

[http://ubuntuforums.org/showpost.php?p=3861647](http://ubuntuforums.org/showpost.php?p=3861647)

post 9 - 
 

Hope that is of some use

Hello again! Thanks for the bluetooth solution. It worked and bypassed the bluetooth. But there is a problem again! It stucks at **Starting anac(h)ronistic cron anacron**. Can any one help me please?????

---

