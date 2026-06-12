---
title: "Upgrading to Firefox 2.0, RealPlayer10,"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by mhenriday on 2006-12-09
As a new user of Ubuntu (6.06) who found himself hurled into the OS, sink or swim, I've been doing my best to learn a set of new techniques rather different from those I used in Windows. One of the things with which I've been having difficulty is downloading and installing upgrades that are not found in the Package Manager. I am used to using Firefox 2.0, which I find superior to earlier versions, like 1.5.0.8, which came preinstalled on my dapper CD, as my browser. To my dismay I have found that installing FF 2.0 on my computer is not as easy as I had imagined - downloading the programme to my desktop was a cinch, but installing and using it in Ubuntu has me completely stymied ! Synaptic does not find the firefox-2.0.tar.gz files on my desktop, and none of my attempts to open them have succeeded. I'm experiencing the same difficulties with RealPlayer10Gold, which I also downloaded to my desktop. Is there anyone who could explain to me wherein my difficulties lie (I've read through the documentation but was unable to find any help I could use there) and walk me through the installation procedure (I'm not adverse to downloading the programmes again, but would very much like to know how to get the previous downloads off my desktop), step-by-step ? I should be ever so grateful !...

Henri

---

### Post by smile_sunshine on 2006-12-09
Hi,
found specific instructions about firefox 2.0 [here]("http://wizah.blogspot.com/2006/11/debian-how-to-update-firefox.html").
[this]("http://www.monkeyblog.org/ubuntu/installing/") and [this]("http://www.psychocats.net/ubuntu/installingsoftware") are very good for information about installing software more generally. 

Was trying to look for a .deb package for firefox 2.0 because that could be easier but couldnt find one yet. 

Hope that helps a bit at least 

:)

---

### Post by mhenriday on 2006-12-11
Dear smile_sunshine

Thanks for your speedy reply ! If I've not been quite as quick in responding, it is due to the fact that I went to Techno Wizah's blog and tried to install FF 2.0 according to the procedure outline there, not once but several times. Unfortunately, I failed to do so, whereby I forwarded the following letter, which explains my attempts, to the thread :

[INDENT]I tried to use the instructions to upgrade the FF 1.5.0.8 bundled with Ubuntu 6.06 to FF 2.0, which I am used to using with Windows, with the following result :

mkdir -p ~apps
mhenriday@mhenriday-desktop:~$ tar zxf firefox-2.0.tar.gz ~/apps/
tar: /home/mhenriday/apps: Not found in the archive

But under '/mhenriday/', I did find a folder called 'apps'

Being an utter novice in Unix/Linux systems, I interpreted all this to mean that the commands had not succeeded in placing 'firefox-2.0.tar.gz' in the right folder. I had, however, no difficulty in drawing 'firefox-2.0.tar.gz' to '/home/mhenriday/apps/'. But how to open the zipped folder ? I right-clicked on it and choose the alternative 'Extract with the archive manager' which produced a new folder, 'Firefox', containing 10 folders and 27 files, but nothing I could run to install FF 2.0. Where do I go from here ? Do I have to reinstall Windows Xp to get FF 2.0 ?... [/INDENT]

As you see, I remain at a loss as to how to update FF 1.5.0.8 to FF 2.0. If you have any further ideas that a Ubuntu novice could be expected to carry out, I should be most happy to hear (read) them !...

Thanks in advance !

Henri

---

### Post by matchstich on 2006-12-11
ok i followed all instructions. message said 2.0 is installed on my system.
i closed all firefox windows and restarted firefoz ,but i am still on 1.5. 
dont understand what happened to 2.0? 
thanks

ok, it worked. i got 2.0 using the cats link . yea, this is twice now i got something to work on here. 
time to try the printer again

---

### Post by mhenriday on 2006-12-13
I finessed the upgrade to **FF 2.0** by upgrading instead from **Ubuntu 6.06** to **6.10**, which comes with FF 2.0 pre-installed. So much for that problem ! But I have a much bigger one : my sudden immersion in **Ubuntu** waters was due to the fact that when I installed the OS, I inadvertently lost my **Windows XP**, despite my attempt to follow Jason Faulkner's [instructions]("http://www.pcmech.com/show/os/903/") to the letter (I didn't succeed in manually editing my partition table, and when I went back and told the **Ubuntu** to do it, the result was that **Windows XP** disappeared). Now I'm confronted with what I'm told is a far more daunting task, *viz*, installing Windows on a **Ubuntu** setup, without losing **Ubuntu**. If anyone has any ideas how this may successfully be done, I should be very happy to hear from him or her. What I need is a step-by-step walk through of the procedure to be followed. I'm working with an old but upgraded Pentium III with 498 MHz clock speed, 512 MB RAM, and two hard discs of 19.5 and 129.5 GB capacity, respectively. Under the present configuration, my system monitor informs me that I have a total of 145.3 GiB in /dev/hda1 /, of which 4.1 GiB or 3 % is being used, with 141.2 GiB 'free' and 133.8 GiB 'available' (where the other 7.4 GiB have gone, I have no idea). In any event, there should be plenty of room to add even such resource hogs as **Windows XP** and **MS Office**....

Henri

---

### Post by barrack on 2006-12-17
> **matchstich said:**
> ok, it worked. i got 2.0 using the cats link . yea, this is twice now i got something to work on here. 

Hey, I'm also tyring to upgrade to FF2. I used the script included on the psychocats page, but it didn't work for me. This is message that I got.

```

Extracting the downloaded Firefox archive

tar: /opt: Cannot chdir: No such file or directory
tar: Error is not recoverable: exiting now
Previous command did not complete successfully. Exiting.
```

Any clue as to what's going on or maybe a better way to install it?

---

### Post by indigoshift on 2006-12-23
Same thing happened to me.  Tried installing it manually, and got that error.  Ran the script as well, got the same error.

---

### Post by haiku99 on 2006-12-23
not sure about FF, but Automatix2 installed RP10 for me w/o any problems....

---

### Post by mhenriday on 2006-12-24
Dear **Indigoshift** and **Barrack**,

If you only need to install **FF 2**, then you can finess the issue in the same manner I did, *viz*, by going to this [site]("http://www.ubuntu.com/products/GetUbuntu/download#currentrelease"), choosing the mirror nearest you, and downloading an update to **Ubuntu 6.10**. Since both of you already have **6.06**, downloading **6.10**, which includes **FF 2**, should go very smoothly, as it did for me. But I am more interested in the general question - what procedure can one use to install the Linux downloads that one has found on the net to one's machine ? Can anyone recommend a good tutorial on the subject that walks the novice through the procedure, step by step ?...

Henri

---

### Post by indigoshift on 2006-12-24
An interesting solution, but I'm not sure I want to upgrade the whole OS just because a web browser I hardly use is out of date.  Seems like that would be pounding a nail with a jackhammer.  ;)

---

### Post by mhenriday on 2006-12-26
> **indigoshift said:**
> ...  Seems like that would be pounding a nail with a jackhammer.  ;)

Well, the finesse did work ! But I agree with you ; as I mentioned in my earlier posting, what I'd really like to have is a tutorial which would help me to do the compiling that needs to be done to download interesting programmes and updates myself, without waiting for some over-worked volunteer to compile a **Ubuntu** version. A [tutorial on the Linux command line]("http://linuxcommand.org/index.php") which I've found on the net may help, but I've not come quite that far in it as yet. If any reader knows of other relevant tutorials which address this problem, than I (and presumably **indigoshift** as well) should be very interested in hearing from him or her....

---

