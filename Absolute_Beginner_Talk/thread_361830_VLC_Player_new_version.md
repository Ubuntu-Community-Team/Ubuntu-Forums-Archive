---
title: "VLC Player new version"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by philip360 on 2007-02-14
I want to update the version of vlc player I have from version 0.8.4 to the latest 0.8.6
I understand that I should uninstall the old version before I install the new. Can anybody check my commands before I foul something up Please?

Original Install process as per Vlc web page

Command line way

You need to check that you have a "universe" mirror in your /etc/apt/sources.list.

   % sudo apt-get update
   % sudo apt-get install vlc vlc-plugin-esd

To install libdvdcss2 (DVD region free software) add "deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free" to your /etc/apt/sources.list file and run:

  % sudo apt-get install libdvdcss2

Proposed Removal Commands:

$ sudo apt-get update && uninstall vlc vlc-plugin-esd
$sudo apt-get uninstall llibdvdcss2

Then follow the original process for the new version.

Thanks for any help. Philip

---

### Post by pay on 2007-02-14
Just update it and the old version will be removed automatcailly

---

### Post by philip360 on 2007-02-14
Hi Pay thanks for the reply, I will follow your suggestion. 
In order to learn something, would my commands work? P

---

### Post by pay on 2007-02-14
Everything but > uninstall vlc vlc-plugin-esdshould work. You can use aptitude to remove things aswell (I think it removes dependencies aswell, but I haven't used Ubuntu for a few months) ```
sudo aptitude purge vlc
```

Anyway goodluck.

---

### Post by kinson on 2007-02-14
> **pay said:**
> Everything but should work. You can use aptitude to remove things aswell (I think it removes dependencies aswell, but I haven't used Ubuntu for a few months) ```
sudo aptitude purge vlc
```


I think aptitude only removes the dependencies if they were installed using aptitude itself. (Correct me if I'm wrong).

Cheers,
Kinson

---

### Post by Maestro23 on 2007-02-14
> **kinson said:**
> I think aptitude only removes the rependencies if they were installed using aptitude itself. (Correct me if I'm wrong).

Cheers,
Kinson


According to psychocats, your are correct: [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by kinson on 2007-02-14
> **Maestro23 said:**
> According to psychocats, your are correct: [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)


Lol, I said that based on my memory of what I read in that page :oops: 

Anyways, whatever helps :p

Cheers,
Kinson

---

### Post by philip360 on 2007-02-14
Thanks for the replys! I learned something new about how linux works...the adventure continues. P

---

