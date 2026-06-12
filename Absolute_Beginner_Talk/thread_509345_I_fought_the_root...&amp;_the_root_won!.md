---
title: "I fought the root...&amp; the root won!"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by victor9098 on 2007-07-25
Hello All,

I have been a proud Ubuntu user for about a week now. Have had several issues which you have all helped me through, my lack of ability when it comes to terminal commands being the weakest leak in the chain.

Now I plugged in (mounted?) my external hd (called "Norton Ghost Backup Disk"), no prizes for guessing what it was used for! It is NTFS but I had no problems looking around inside until I tried to access anything, root was the owner and only group. I have looked at 4 other threads that dealt with this issue, followed the commands until I mounted the external hd and was told it was now unreadable. It seems I have managed to call it something which has a symbol in the title!

It has a back-up of my previous OS on it and my entire music collection. Though I prepared to burn those bridge down (re-format or something?) can I ensure I will be the owner?

Also, I have a similar problem when I insert DVD-RW, root is owner etc...

Thank you!

---

### Post by frodon on 2007-07-25
Don't worry this is just a question of mount command, nothing should be lost.

First by default ntfs has only read support under linux, if you wish to have write support you will need to install and configure ntfs-3g which is another ntfs driver which allow you to write on ntfs.
All about ntfs-3g is here (see part 3 manual configuration) :
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Then if your want to run your custom mount command automatically when you plug your drive look here (post 3 is an easy way to do it) :
[http://ubuntuforums.org/showthread.php?t=502864](http://ubuntuforums.org/showthread.php?t=502864)

About you DVD-RW drive you just need to add a line about it in your fstab file to solve the problem. So tell us the name of your DVD-RW device and we will tell you what line to add in your fstab file so you will be done forever, it should be something like /dev/hdb or /dev/hdc.

---

### Post by victor9098 on 2007-07-25
Thank you very much!

I will try all of the above and update later...hopefully to say this is solved!

---

### Post by victor9098 on 2007-07-26
Hello again,

Good news, the first part went fine. I found the application with synaptic package manager and installed.

Bad news, no matter which set of advice I use I still keep getting the following error:

Cannot mount volume.
Unable to mount the volume "Norton Ghost Backup Disk".
Details
mount_point cannot contain the following characters:
newline, G_DIR_SEPARATOR (usually /)

PLEASE can anybody help me out with this! Maybe I am inputting the commands wrong? The 3rd paragraph, how do I access the root when the drive will not mount? I have inputted the commands in the first paragraph, then I "Justified" them and exited saying Yes I wanted to keep the changes. But I keep getting the above.

---

### Post by victor9098 on 2007-07-26
Sorry,

Ignore the last post. The properties box for the external hd is now available to click. Deleted the incorrect text and now it is mounting to the system.

Now how do I change the ownership of the external hd? Root is still in command. I obviously did it very wrong on my first attempt...but I thought I was following the instructions.

Advice and guidance is most welcome, thank you.

---

### Post by fatfranko on 2007-07-26
ok, im a total newb, so this might be the blind leading the blind but i think i had a similar issue and i opened the terminal and put: gksudo nautilus
entered my password and went to my ext drive in /media, right clicked on it, went to properties, and went to permissions tab.

---

### Post by Inxsible on 2007-07-26
you can assume ownership by

```
sudo chown -R <your username>:<your group> <path to where you mounted the drive>
```

your group is generally the same as your username....unless you specifically changed something.

Hope that helps !!

---

### Post by codebitch on 2007-07-26
i had the same problem with my external hd i solved the problem by using alt+f2 then just tell it to run in terminal then type sudo and the path to your hd then you can change perrmissions by right clicking on the icon in the folder that it is in (should be /media) you have to tell the run command box to run in terminal so that you can put in your password for sudo. once you get to the perrmissions area for that media just set it so group and others can read&write and that should do it

---

### Post by victor9098 on 2007-07-26
Thank You

Thank You

&

Thank You

I have done it, I now own my external HD once again. Now to get rid of those 30GB of old OS backups and start backing up my new OS!!!

---

### Post by codebitch on 2007-07-28
**[COLOR="Blue"]High Five!!!!!!!!![/COLOR]**

---

### Post by DBStevens on 2007-07-28
You need to change the post to insert [solved} Victor 1 Root 0 was ;-)

---

