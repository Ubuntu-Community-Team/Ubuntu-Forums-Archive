---
title: "Dual Booting With Vista"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by JayDeePlus on 2007-04-10
Hi,

I have recently become aware of ubuntu, which is like a new world coming from just learning about redhat in school (ITT Tech). Very Interesting, so i was wanting to be able to dual boot the feisty version from my machine that already has Vista installed, and do not want to re-partition the hard drive because my computer and shared with my roommate. So, i reently downloaded a Boot Manager and a Partition Manager for the dual boot process, i've burned the ubuntu image to a CD using imgburn, and was going to take a image of my computer and was going to burn to a CD aswell for backup purposes. 

My First question is, i'm not sure if i've downloaded the version of ubuntu i wanted. I went to this site and download what i think is the latest version which i think the 7.0 latest, and i was wanting actually have the feisty version and latest get the beryl package for the cubed desktop. the question is, is 7.0 feisty.

My Next question is can i dual boot using the tools i've listed i have without having to re-partition my hard drive, will the partion manager allow me to edit or "break" a partition down to allow me to to install ubuntu feisty.

also, i have tried running my CD burn i have for ubuntu and it gets to a screen that says uncompressing ubuntu....ok, processing 
kill: kill unable to kill imp "3896": 
int: id "1" load was to fast: disabling for 5 minutes
int: id "2"load was to fast: disabling for 5 minutes
int: id "3" load was to fast: disabling for 5 minutes
int: id "4" load was to fast: disabling for 5 minutes
int: id "5" load was to fast: disabling for 5 minutes
int: id "6" load was to fast: disabling for 5 minutes
int id: there is no more processes in the runlevel.

what does this screen mean.

so altogether is there a tutorial or can anyone direct me the way on dual booting without having to re-partion aleady exsisting hard drive with Vista installed

---

### Post by thefoolisme on 2007-04-10
> **JayDeePlus said:**
> Hi,

I have recently become aware of ubuntu, which is like a new world coming from just learning about redhat in school (ITT Tech). Very Interesting, so i was wanting to be able to dual boot the feisty version from my machine that already has Vista installed, and do not want to re-partition the hard drive because my computer and shared with my roommate. So, i reently downloaded a Boot Manager and a Partition Manager for the dual boot process, i've burned the ubuntu image to a CD using imgburn, and was going to take a image of my computer and was going to burn to a CD aswell for backup purposes. 

My First question is, i'm not sure if i've downloaded the version of ubuntu i wanted. I went to this site and download what i think is the latest version which i think the 7.0 latest, and i was wanting actually have the feisty version and latest get the beryl package for the cubed desktop. the question is, is 7.0 feisty.

My Next question is can i dual boot using the tools i've listed i have without having to re-partition my hard drive, will the partion manager allow me to edit or "break" a partition down to allow me to to install ubuntu feisty.

also, i have tried running my CD burn i have for ubuntu and it gets to a screen that says uncompressing ubuntu....ok, processing 
kill: kill unable to kill imp "3896": 
int: id "1" load was to fast: disabling for 5 minutes
int: id "2"load was to fast: disabling for 5 minutes
int: id "3" load was to fast: disabling for 5 minutes
int: id "4" load was to fast: disabling for 5 minutes
int: id "5" load was to fast: disabling for 5 minutes
int: id "6" load was to fast: disabling for 5 minutes
int id: there is no more processes in the runlevel.

what does this screen mean.

so altogether is there a tutorial or can anyone direct me the way on dual booting without having to re-partion aleady exsisting hard drive with Vista installed

To answer your first question, 7 is fiesty, but it's still in beta until it's official release on the 19th(?).  It's probably pretty stable by now though, although I am using edgy.  

Very good about backing up your stuff before you get started.  It's a pet peeve of mine to see all the posts from those who didn't think about it.  :-)

The install disk comes with a partition program called gparted.  You should have three choices when you install: 1. wipe out windows, 2. resize current partition and then install in allocated space, 3. manually partition.  So to answer your question, yes you have the tools you need. 

Finally, I'm not sure what the errors you posted mean, since I'm still a relative noob, but I do know that if the ISO isn't burned at a VERY slow rate, it will cause errors.  Most recommend 4x for burning.  My drive wouldn't go that low, but I managed a good burn at 12x.  Just remember to verify the checksum for the download, and then take the few minutes to run the "check disk" option on the install menu.  My first disk would run as a live CD, but failed for installation, so I had to create a new one.  Just trying to save you the time. 

There are plenty of tutorials out there and FAQs about dual-booting.  Here's a good place to start:  [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by JayDeePlus on 2007-04-10
i recently found out that i actually have 6.10 edgy. i found out you can upgrade from 6.10 to feisty 7.04. 

does 6.10 have those partitioning options that you was referring to " resize current partition and then install in allocated space" ??

i have ran the " test disk for errors" option and it comes back and advises there are no errors.
what should i do when that error comes back, because it gets to the screen i was telling you about and loops every 5 minutes and do not proceed.

---

### Post by JayDeePlus on 2007-04-10
upping for response.

---

