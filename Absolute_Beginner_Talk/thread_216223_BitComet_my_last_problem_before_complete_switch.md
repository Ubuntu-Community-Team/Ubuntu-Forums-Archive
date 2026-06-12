---
title: "BitComet my last problem before complete switch"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by KarmaKing on 2006-07-15
Hello all,

I am almost read for the complete dump of Windows, but I have one last program to sort out.  As the title of the thread states that prgram is Bitcomet.  I have tries every BitTorrent available for Windows and Linux and found this to be the best and my favorite.  It is this program that is keeping me on Windows. I am far from home and do a great deal of download to keep in touch and keep entertained.

I have installed Wine and installed Bitcomet, but is gave me an error asking me to ugrade Explorer to 6.0 or install MSXML 3.  I installed the MSMXL3 with WINE as well, but I still get this error.

Now, I have read some of the threads pertaining to what wine is capable of and what it is not.  And I understand that certain programs require explorer to be installed for some reason that eludes me.

I know there are many experienced people here and even some programers and I would like to ask some help on this.There must be a  way. I have full confidence that somone here has the knowledge.

please:)

Thanks in advance

---

### Post by truantology on 2006-07-15
I used WineTools to install the latest IE and MSXML...worked fine!  you can get it here: [http://www.von-thadden.de/Joachim/WineTools/index.html#download](http://www.von-thadden.de/Joachim/WineTools/index.html#download)

---

### Post by KarmaKing on 2006-07-15
Thanks I will try the wine tools.

---

### Post by KarmaKing on 2006-07-16
man I just can't get the tar installed. 

I thought we could just double click and it will install

I extracted the tar to a temp faolder and tried to execute the sh, but nothing

can someone give me a hand

---

### Post by orb9220 on 2006-07-16
I think to make the sh script run you have to right click properties and toogle the execute flag to make it executable for user.

---

### Post by KarmaKing on 2006-07-16
Ok I got the winetools installed by using root and the sh command.  However, now the IE6 exe file tells me iot can't connect to the internet.

---

### Post by h2gofast on 2006-07-16
[http://appdb.winehq.org/appview.php?iAppId=2275](http://appdb.winehq.org/appview.php?iAppId=2275)
[www.google.com/linux](www.google.com/linux) is your friend

have you tried azureus?  I know it's a java, but I've been happy with it under Linux.

---

### Post by gwwfps on 2006-07-17
I had the exact same problem, turns out I just needed to make a native override for msxml3, don't know if that will solve your problem.

By the way, if you are going to use BitComet, 0.50 seems to be the last version that's stable in wine, for me at least.

---

### Post by grogger13 on 2007-02-23
I am using crossover, i dont know if it makes a difference.
Okay, i tried took get bitcomet to work by installing ie6 and msxml and pretty much the only difference i had was that the file name was msxml6.msi, but it didn't seem like it should matter.

Now after both installed igot the latest stable realese and on the website it says its .84 and after instal when i click on the icon i just got an error about it not working.

---

### Post by xpod on 2007-02-23
I have BitComet on an XP VM compliments of Vitualbox which works fine but i also have azureus on my Ubuntu which i actually use most of the time as it works a lot better:)

EDIT:[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by nudnik on 2007-02-23
> **xpod said:**
> I have BitComet on an XP VM compliments of Vitualbox which works fine but i also have azureus on my Ubuntu which i actually use most of the time as it works a lot better:)

EDIT:[http://www.virtualbox.org/](http://www.virtualbox.org/)

Are you using the Windows version of Azureus? If not, how did you get the Linux version to function properly? :shock:

---

### Post by nonewmsgs on 2007-02-23
azurus for linux is available under applications add/remove - internet.

i have used many bittorrent apps and they all seem about the same to me except for a feature here or there, like i liked the checkmark the files you dont want thing in bitcomet.  so can you point out to a fellow n00b the major differences?

---

### Post by nudnik on 2007-02-23
> **nonewmsgs said:**
> azurus for linux is available under applications add/remove - internet.

i have used many bittorrent apps and they all seem about the same to me except for a feature here or there, like i liked the checkmark the files you dont want thing in bitcomet.  so can you point out to a fellow n00b the major differences?

The link you described allows you to install Azureus, however, it is not an officially supported application, and I have never been able to get it to run properly on any system on which I attempted an install. The latest Java RTE from Sun, linked properly, etc. doesnt seem to help, a number of very irritating and potentially damaging errors always manifest. These would include 100% CPU usage during file checks, mysterious stalling after a certain period of time etc. 

The default Bittorrent client doesnt work very well on many systems either. Ktorrent works better than Azureus, and is very similar to Azureus, but it too often stalls after a period of time, and leaves chunks of data out on certain systems. Bittornado is the only torrent app that has provided reliable, quality results in every instance. Unfortunately, it will only download one file at a time, which makes it inefficient, but at least it works.

---

