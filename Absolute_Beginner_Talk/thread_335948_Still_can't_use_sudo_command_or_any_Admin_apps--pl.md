---
title: "Still can't use sudo command or any Admin apps--please help!!"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-01-11
I am still having problem trying to use the sudo command. All I get now when I enter sudo is " sudo: unable to lookup (none) via gethostbyname ()". Does anyone know why this is happening?? Originally I was trying to set up my network and was advised to delete some settings. Guess I deleted the wrong ones and now I get this when typing in sudo. Also I cannot run any admin applications (Synaptic Package Manager-Network Manager and so on). I was advised to try vi or nano, but being a real nubie to the nth power when it comes to linux I didn't have a clue what either one of these programs were talking about. Any help will reallllly be appreciated. Specific entries especially!! Thanks in advance.

---

### Post by Sef on 2007-01-11
Copy and post your sources list here.  From the terminal (Applications > Accessories > Terminal): cat /etc/apt/sources.list.

---

### Post by StickyStyle on 2007-01-11
Did any of the suggestions you received involve editing your /etc/hosts file?  They symptom you describe sounds like an messed up hosts file.

To fix this, since you cant do anything in a full multiuser run level, so you need to boot into single user mode or 'recovery mode'.  When your machine is booting you have the option to press the ecape key for the grub menu, press the esc key and select the kernal that looks like...
Ubuntu, kernel 2.6.17-10-generic (recovery mode)
(your version may be different, but 'recovery mode' is the important part)

Now from here you eventually get dropped to a root prompt (~#) when the machine is fully booted.  Now run ```
#nano /etc/hosts
```, the first line of the file should be...
```
127.0.0.1 localhost
```If you dont have a 'localhost' entry like the above in your file, add one.  Now save the file by pressing ctrl+o (write out file) and exit with ctrl+x.  Now reboot by typing 'reboot'.

Hopefully if this was your problem you should now be able run sudo.

---

### Post by StickyStyle on 2007-01-11
Oh and since you mentioned it, nano and vi are both text editors, but run in on the terminal rather than with a GUI.  I suggest you get your feet wet nano when you are having problems then practice with vi when your system is not having issues as you don't need more frustration that can occur with newbies + vi.

---

### Post by jerrynewt on 2007-01-11
Ok since I am away from home on my laptop (dual boot XP and Ubuntu) I will have to restart and try these suggestions. Be back in a minute with results. Thanks for the quick reply!!

---

### Post by StickyStyle on 2007-01-11
Doing some quick searching you may want to also make sure that the file /etc/hostname has your computers name in it, and nothing else.

Also you may (by reading other peoples suggestions) want to add your hostname to that line in the /etc/hosts file so it looks like this
```
127.0.0.1       localhost.localdomain   localhost    yourcomputername
```

---

### Post by jpkotta on 2007-01-11
This bug has been reported many times.  How do we get the attention of someone to fix it?

[https://launchpad.net/ubuntu/+source/rescue/+bug/19553](https://launchpad.net/ubuntu/+source/rescue/+bug/19553)
[https://launchpad.net/ubuntu/+source/netcfg/+bug/19775](https://launchpad.net/ubuntu/+source/netcfg/+bug/19775)
[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906)

---

### Post by jerrynewt on 2007-01-11
Ok I'm back (finally). I kept getting errors and no information with the entries you suggested, so I just reinstalled Ubuntu OS again (still dual boot with XP) and I am back to my happy self again--everything working like it is supposed to, smooth as silk. Even with the small problems I have encountered I think it won't be long before I am Windoz free!! I didn't configure my network connections as my T-Mobile broadband card isn't linux friendly. As soon as I get back to the house in a few days I will connect to the internet via ethernet and get everything configured and up to date. This is a great forum for beginners--every question I have had has been answered fast and accurately. Thanks again for all of your help.

---

