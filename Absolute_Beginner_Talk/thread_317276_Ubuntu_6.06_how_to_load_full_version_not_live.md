---
title: "Ubuntu 6.06 how to load full version not live?"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by cheree71 on 2006-12-12
:confused:  I just purchased Ubuntu 6.06 and put it in my pentium 2 , 350/100 mhz, 192mb ram. I put the disc in and Ubuntu came up in orange and the options and I chose start or install Ubuntu and it went thru all that stuff loading drivers and then went to a message saying it was uncompressing Ubuntu and then it went no further](*,) , the screen actually went off and I had to press the space bar to make the screen come back. So, need I say I am a complete novice when it comes to Linux, so any help would be appreciated. Thanks in advance.

---

### Post by hyper_ch on 2006-12-12
When you pressed space bar what did appear then on your screen? Did it look like a GUI environment from where you can use the system, running programs and stuff... or was it completely different?

---

### Post by cheree71 on 2006-12-12
Hi thanks for replying. When I pressed the space bar the same thing came up, saying it was uncompressing Ubuntu.

---

### Post by Bachstelze on 2006-12-12
192 MiB of RAM is not enough for the Live CD, get an Alternate.

---

### Post by HokeyFry on 2006-12-12
download the alternate install cd, you will have a much lesser headache with that (if one at all)


and when you fire it up choose the text install

---

### Post by finferflu on 2006-12-12
Well, before you install it, be sure to backup all your data, it's always safe to do so. And also I suggest you to keep Windows for the time being, and do double booting ;)

---

### Post by cheree71 on 2006-12-12
It is a computer that is completely expendable. I really want to use Linux but wont risk deleting a perfectly good version of XP unless I see it working. I got a live version of another linux product and loved it but that was live, I wanted to see this running first and a duel boot is a good idea. Thanks

---

### Post by Bachstelze on 2006-12-12
Get an Ubuntu Alternate CD, it will work just fine :)

---

### Post by finferflu on 2006-12-12
You can download the alternate CD from this page:  [http://www.ubuntu.com/products/GetUbuntu/download#currentrelease](http://www.ubuntu.com/products/GetUbuntu/download#currentrelease)

Just select the location which is nearer to you, and click on **Other installation options**.
Then choose **ubuntu-6.10-alternate-i386.iso** or **ubuntu-6.10-alternate-i386.iso.torrent** if you prefer using a bittorrent client
Good luck!

---

### Post by hyper_ch on 2006-12-12
Well, to 99.999% it's safe to install linux without breaking your other system.
As suggested, download the alternate installer... with your computer specs I even tend to recommend xubuntu ([http://www.xubuntu.org/get](http://www.xubuntu.org/get))instead of ubuntu...
During the install then you can resize your windows partition (in case you have not done so yet). I assume you have 1 windows partition which is the full hard disk (evtl. a hidden partition for restore)...
In that case resize the current partition with the partition tool... then in the unused space create a new partition (2x the size of your ram) and make it as type "Linux Swap", then - depending on your liking - create one or two other linux partitions (mostly recommend a system/root partition which is 5-10GB [that one will hold all the applications and stuff...] make it as file format EXT3 and as mounting point "/" and the second partition then will be the rest of your diskspace making it as file format EXT3 and mounting point "/home" [in this one all your data, movies, mp3s, docs, ... will be saved]) - you can also just make one linux partition (next to the swap one) which will hold all the diskspace you want to give to linux and it should be EXT3 and mounting point "/".

**[COLOR="Red"]DO MAKE A BACKUP FIRST BEFORE YOU START CHANGING YOUR PARTITION(S)[/COLOR]**

---

### Post by finferflu on 2006-12-12
And don't forget to run the defrag utility on Windows, before resizing it!

---

