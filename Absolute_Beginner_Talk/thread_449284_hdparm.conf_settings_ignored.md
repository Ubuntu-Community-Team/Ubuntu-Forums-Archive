---
title: "hdparm.conf settings ignored?"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by sune_cph on 2007-05-20
Hi,

I run a Ubuntu/WindowsXP dual-boot setup with dedicated drives to each OS.

Since i have no need for the XP drive when i run Ubuntu, I pretty much want ubuntu to shutdown the XP drive (/dev/sda)  to reduce noise and power consumption.

Commands like 

hdparm -S12 /dev/sda   
hdparm -y /dev/sda 

works great when I run them from the console, but I want ubuntu to automatically do this for me, so I have tried adding the following to /etc/hdparm.conf:

/dev/sda {
	spindown_time = 12
}

or even

/dev/sda {
	standby
}

but these appear to be  ignored when i boot Ubuntu.

I also tried the command_line { } syntax but to no avail.


Why is this not working? Do I have to "enable" hdparm.conf somewhere?

Hope anyone can help!

thanks

---

### Post by ~SkyBlue~ on 2007-05-20
Not too sure about how hdparm works, but have you tried adding those to .profile ? Or maybe create a shell script like:

```
#!/bin/sh
hdparm -S12 /dev/sda
hdparm -y /dev/sda 
```

and add them to startup program (system->pref->session)

---

### Post by Gen2ly on 2007-05-20
I'm pretty sure /sda drives are SATA drives mostly they self-discover their own settings.  In fact, I've heard instances where hdparm settings can be dangerous.   Be careful!

---

### Post by WakkiTabakki on 2007-05-20
Yes, hdparm is for  PATA-devices, yours seem to be SATA or SCSI (as pointed out).

Furthermore, hdparm must be run as root, so putting it your .profile wouldn't work... The proper way would be to edit /etc/hdparm.conf. When ubuntu starts up, hdparm is run automatically, and it fetches its settings from that file..

And as mr. Gently pointed out you really can wreck havoc with hdparm, so DO be careful!

Cheers
/N

---

### Post by sune_cph on 2007-05-20
Thanks for your response!

The drive in question is plain ATA, and yes I need to use sudo hdparm etc  to make it work.

When I invoke hdparm -y /dev/sda from the console, everything works dandy, the drive spins down and all, but when i transfer the samme settings to hdparm.conf, they're pretty much ignored.

Is there any log file I can check to see if hdparm produce some errors during startup? I tried /var/logs/dmesg but it doesn't seem to include hdparm output.


Thanks again 

Sune

---

### Post by chuvisco on 2007-05-30
Do you have hdparm enabled in System > Administration > Services?

---

### Post by kerry_s on 2007-05-31
try /etc/default/hdparm i did mine from there.

---

### Post by 67GTA on 2007-05-31
If your drive is shown as sda, then it is  SATA and the hdparm settings will be ignored.

---

### Post by bdonkey on 2007-06-04
But if running hdparm from the shell still works on a SATA drive, will it work in the hdparm conf then? Or does Ubuntu simply say "Ah, it's SATA, let's not even check the conf file"?

I've used hdparm to set my SATA hd's power settings, and it works really well for that (stops the constant clicking / parking and all).

---

### Post by 67GTA on 2007-06-05
You can change a few minor settings in the conf file, but the major ones like DMA and I/O settings will be ignored. I'm pretty sure support was not even put in for it. SATA drives will always try to reset their own settings. I have noticed that Windows XP even says  "DMA if possible" with my SATA drive.

---

### Post by Michael Steinberg on 2007-06-28
This is a bump, because the thread raises a real issue and so far there's been no satisfactory answer as far as I can see.

I, too, have an SATA drive, and it's apparently factory-set to spin down after what seems like a few milliseconds of inactivity. Waiting for it to get up to speed every time I want to look at a menu or save a file negates all the speed advantages of SATA and then some. I can set the spindown time to whatever I want through a sudo hdparm command in the terminal, but I've tried editing the hdparm.conf file to run the command automatically with the same lack or results.

There ought to be a simple way to fix this problem. So far I've not had success with shell scripts.

Michael Steinberg

---

### Post by jamesford on 2007-08-23
i found a way to spin down satas after s set interval

first create a script called spindownsata.sh, in it paste
```
#!/bin/sh
hdparm -S241 /dev/sda
hdparm -S241 /dev/sdb
hdparm -S241 /dev/sdc
hdparm -S241 /dev/sdd
#replace with your selected spindown time and your sata drives, 241 = 30 mins
```

then, to install this run
```
sudo cp spindownsata.sh /etc/init.d
update-rc.d spindownsata.sh defaults
cd /etc/init.d
chmod +x spindownsata.sh

```

voila, works, at least for me

---

### Post by Michael Steinberg on 2007-08-28
Thanks for the advice. Unfortunately, the script doesn't seem to work on mine....

---

### Post by rasmusfromdenmark on 2007-10-14
The hdparm.conf is applied when starting hdparm as a system proces:
  
```
sudo /etc/init.d/hdparm start
```

If you want this proces to start at boot time, exec this:

```
sudo update-rc.d hdparm defaults
```

---

