---
title: "Proccessor Overheating On Powerbook"
date: 2006-06-08
forum: Apple PPC Users
---

### Post by n00bWillingToLearn on 2006-06-08
I have been noticing for a while that my powerbook has been running hotter in Ubuntu than OS x. My machine has also been shutting down abruptly fairly often. I finally put 2 and 2 together and realized that my proccessor has been overheating to the point of it being shut down to prevent (more) damage. This is extremely serious as it could actually destroy hardware and as such, unless advised otherwise, I am going to post a thread in a few hours warning anyone using Ubuntu on PPC not to untill this issue has been resolved. I may be over reacting, and if so please tell me, but I don't want people to remember Ubuntu as the OS that melted thier powerbook.

[edit] If anyone knows how to get in contact with an admin, or is one, I would really like advice on what sould be done and I will not post a warning without knowing if this is an isolated issue but I don't just want people saying they aren't having the problem I want proof that I am the only one that is... just somebody post something before I go crazy.

---

### Post by jazzmuzik on 2006-06-08
I'm not an admin, just a guy. 

Perhaps you have some dust buildup around the cpu fan. It's also possible that the heat sink is not properly seated on the cpu. I worked on a computer recently where the heat transfer gel (the silicone stuff between the fan's heat sink and the cpu) got old and hard. It's wasn't transferring the heat and as a result the computer would shut off about two seconds after being turned on. Finally, fans get old. Bearings wear out. Might be time to put in a new one. How old is your powerbook?

---

### Post by n00bWillingToLearn on 2006-06-08
[quote=jazzmuzik]I'm not an admin, just a guy. 

Perhaps you have some dust buildup around the cpu fan. It's also possible that the heat sink is not properly seated on the cpu. I worked on a computer recently where the heat transfer gel (the silicone stuff between the fan's heat sink and the cpu) got old and hard. It's wasn't transferring the heat and as a result the computer would shut off about two seconds after being turned on. Finally, fans get old. Bearings wear out. Might be time to put in a new one. How old is your powerbook?[/quote]

3 years old and never had a problem with overheating in OS x. If this is a hardware problem then I am going to have to yell at someone at apple as I sent it in for repair about a week ago and it was returned with no problems found. And yes I think it is more likely a harware problem and I am definately not going to post a warning. It's just that my warrenty is almost up so now would be a bad time to be having problems.

---

### Post by jazzmuzik on 2006-06-08
Well, I don't have a laptop, but I did recently hear that it's a good idea to put it on something where air can circulate underneath it. You could also try xubuntu version as I understand it doesn't require as much cpu power.

---

### Post by D!mon on 2006-06-08
Btw, there was a program in Windows called CPU Idle (cooling and power management software, [http://www.cpuidle.de/)](http://www.cpuidle.de/)), is there any similar Linux program or Linux is smart enough to keep cpu cool itself?

---

### Post by n00bWillingToLearn on 2006-06-08
I think one possible explanation is that my fans arent spinning in iether OS x or Ubuntu  and I have only been having problems in Ubuntu because, without proprietary video drivers, all 3d is being done on the CPU and so I have been using the CPU more in Ubuntu than OS x.

---

### Post by n00bWillingToLearn on 2006-06-09
Update: My fans are working in OS x but they are not turning on in Ubuntu. I made a quick application in OS x pretty much while(true) Math.random(); and sure enough, my processor got hot and my fans turned on. I have never heard my fans running in ubuntu and although I am not going to do the same test in ubuntu I assure you that they weren't working even in the moments before the computer shut down. So this is a problem with Ubuntu and it is verry important that it be solved.

---

### Post by nkbj on 2006-06-09
Is the thermal control module loaded at boot time in Ubuntu? You can test this by ```
lsmod | grep therm
```

Followup: Maybe you are the victim of this bug? [https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/48271](https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/48271)

Regards,
Niels Kristian

---

### Post by benoitc on 2006-06-09
Does r300 driver use cpu for 3d ?

---

### Post by n00bWillingToLearn on 2006-06-10
lsmod | grep therm gives no output so I assume that it is not being loaded. What can I do to fix this? The person who filed the launchpad report said "Easy fix is to load the module and add it to /etc/modules" so how exactly do I do that?

---

### Post by pvz on 2006-06-10
```
sudo modprobe therm_adt746x
```
to load the module, and than in your favorite texteditor:
```
sudo gedit /etc/modules
``` an add the line
```
therm_adt746x
```save the file.

---

### Post by n00bWillingToLearn on 2006-06-10
[quote=pvz]```
sudo modprobe therm_adt746x
``` to load the module, and than in your favorite texteditor:
```
sudo gedit /etc/modules
``` an add the line
```
therm_adt746x
```save the file.[/quote]

I did the first step but stopped when I got an error
```
 jordan@ubuntu-laptop:~$ sudo modprobe therm_adt746x
Password:
FATAL: Error inserting therm_adt746x (/lib/modules/2.6.15-23-powerpc/kernel/drivers/macintosh/therm_adt746x.ko): No such device
```

---

### Post by electricshoes on 2006-08-24
> **n00bWillingToLearn said:**
> I did the first step but stopped when I got an error
```
 jordan@ubuntu-laptop:~$ sudo modprobe therm_adt746x
Password:
FATAL: Error inserting therm_adt746x (/lib/modules/2.6.15-23-powerpc/kernel/drivers/macintosh/therm_adt746x.ko): No such device
```

Has anyone figured this out? In the Dapper kernel config 'therm_adt746x' is set (M).

modprobe therm_adt746x gives me the same error as is listed above. Does this kernel need to be recompiled so that therm_adt746x is loaded? I went through the process of doing this but couldnt get it working right with Dapper PPC on a powerbook. 

Any help would be appreciated.

---

### Post by davidmaxwaterman on 2006-08-25
> **electricshoes said:**
> Has anyone figured this out? In the Dapper kernel config 'therm_adt746x' is set (M).

modprobe therm_adt746x gives me the same error as is listed above. Does this kernel need to be recompiled so that therm_adt746x is loaded? I went through the process of doing this but couldnt get it working right with Dapper PPC on a powerbook. 

Any help would be appreciated.

It seems that bug was for an iBook. It could be that there is a different one for Powerbook.

For the record, I am pretty sure my Powerbook also overheats - and gets much hotter than when I used to run OS X. So, I don't think you're the only one.

I have a thermochromatic strip stuck to the metal just 'above' the keyboard (where it seemed to get most hot), and it used to sit at around 44 or 46C, but not it often goes up much higher, over 50 in some cases. This proves it's not (just) thermal paste, since the heat sink is conducting the heat to the case.

It could also be that the processor is kept at high speed more often by Ubuntu than it is in OS X, which would cause it to produce more heat. I think I saw a link on /. about making it drop to a lower speed more often.

I have a TiBook G4/800 DVI, also about 3 years old. I'd love to know how to fix it - it's almost burning the skin off my lap.

Max.

---

### Post by electricshoes on 2006-08-25
It was working on an older kernel, I dont think it is working correctly with this kernel, I havnt had a chance to recompile it with therm_adt746x again to see if that would help.

---

### Post by Ephry on 2007-08-27
I'm experiencing a similar problem after loading Edgy and now Feisty. The powerbook is a G4 667MHZ unit and it does heat up, but never this much. I don't hear the fan at all, and at touch it feels like close to 60c than anything. I have loaded the therm_adt746x, and will restart  and see what happens. 


E

---

