---
title: "few questions"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by terry_gardener on 2007-08-25
these are properly easy questions for someone to answer but would like to know. 

1. how do you change the default download location because when i download it just goes to the desktop folder and i would like it to goto the downloads folder. 

2. ubuntu gets released every 6 months, does the update manager automatically update it or do you have to download the iso and start again with the different version. 
[INDENT]if you have to start again do you have to backup all the files and settings you have and the copy them to the new version or is there a migration utility app in the install software. [/INDENT]

3. i have a intel core 2 duo 2.66ghz and i installed the i386 version of ubuntu should i have installed the 64bit version and would i see any difference with it. 

thanks

---

### Post by Daveth on 2007-08-25
Hi.
by downloads I assume you mean through your browser? Which one are you using? There is usually a prefs options which sets the file download location and you can point it where you will.
Though there are new Ubuntu releases you do not have to chase them right away- I always wait a bit till the few bugs that always seem to escape squishing get sqiushed.

I always think it is better to start from scratch with a new version. To make this easy you had best make a separate home partition into which all your data, settings, and config files live, then you can just launch the new version over the old and it will find your /home with no problem. There is no, as far as I know, a migration tool- if there is I have been missing out!

I'd play with 64-bit live cds but not install them- I have a Sabayon 64 bit which races along but have not got the courage up to install it next to Ubuntu! This is will probably get howls from the 64 bit crowd here...

---

### Post by Majorix on 2007-08-25
> 
1. how do you change the default download location because when i download it just goes to the desktop folder and i would like it to goto the downloads folder. 


With Firefox you mean? You can change it in edit > preferences. It is in the first window that pops up.

> 
2. ubuntu gets released every 6 months, does the update manager automatically update it or do you have to download the iso and start again with the different version. 


No. You can easily do a
```
sudo apt-get dist-upgrade
```

And you will have the next version of Ubuntu.
> 
3. i have a intel core 2 duo 2.66ghz and i installed the i386 version of ubuntu should i have installed the 64bit version and would i see any difference with it. 

thanks

You should stick with the i386 version I think. Some people will say vice versa probably but 64bit computing is not that well supported as of yet.

---

### Post by pgar23 on 2007-08-25
> **Majorix said:**
> With Firefox you mean? You can change it in edit > preferences. It is in the first window that pops up.



No. You can easily do a
```
sudo apt-get dist-upgrade
```And you will have the next version of Ubuntu.


You should stick with the i386 version I think. Some people will say vice versa probably but 64bit computing is not that well supported as of yet.

Majorix pretty much summed it up perfectly for you.

---

### Post by GMachine_24 on 2007-08-25
> **terry_gardener said:**
> 

1. how do you change the default download location because when i download it just goes to the desktop folder and i would like it to goto the downloads folder. 


Hi. This depends, perhaps, on what program you are using to download. For example, I am using SeaMonkey (f/k/a Mozilla) Web browser and, to change or see the default download file, I open a browser window, choose:

edit->preferences->navigator->downloads

from the upper toolbar menu and there I see, among other things, the path to my default download location which is home/username/Desktop.

The location offers other download options, check it out to see for yourself. [Firefox is edit->preferences->download.]



> **terry_gardener said:**
> 

2. ubuntu gets released every 6 months, does the update manager automatically update it or do you have to download the iso and start again with the different version. 
[INDENT]if you have to start again do you have to backup all the files and settings you have and the copy them to the new version or is there a migration utility app in the install software. [/INDENT]

You are not automatically 'updated' to the new install. However, if you use Synaptic package manager to update your computer, it will show there is a new version of Ubuntu available and there will be a box  next to that note which you check if you want to update your Ubuntu version to the new install. Or you can

sudo apt-get upgrade

on a command line.

Be aware that upgrades of Ubuntu are notoriously problematic; my experience has been that it is best to back up my data files, make a list of all programs I need and then do a clean install of the OS and programs.

> **terry_gardener said:**
> 3. i have a intel core 2 duo 2.66ghz and i installed the i386 version of ubuntu should i have installed the 64bit version and would i see any difference with it. 

thanks

This one I don't know the answer to; but if you do a search I'm sure you will find if that CPU is 32 or 64 bit. However, from a quick search it seems you might be able to run either version. Check it out.

gm

---

### Post by terry_gardener on 2007-08-25
thank you for your quick replies as usual 

i have managed to change the default location i must have missed it the first time i looked.

---

