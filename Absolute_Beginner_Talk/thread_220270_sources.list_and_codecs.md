---
title: "sources.list and codecs"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by Alain1 on 2006-07-21
Hi,
I'm a newbie in Linux. I wanted to install the w32codecs. So I followed the guide for using source-o-matic. 
So, I still have an error. I have no idea what I did wrong. 
Installing Mplayer was not a problem
Installing the codecs give me an error
Can someone gove me a tip plse..?
Tx;)

---

### Post by OpsVentus on 2006-07-21
Installing the w32codecs for MPlayer shouldn't be that hard to do.
You need to download the file's and put them in the right place.
So tell us, what did you do and what is your error?
Where did you put the file's?

Cheers,
Bart.

---

### Post by basilwatson on 2006-07-21
same boat 

except I couldnt get mplayer ..have downloaded xmme ,and the [addon cd]("http://www.ubuntuforums.org/showthread.php?t=183933&highlight=addon+cd") ,,,

other than that I am stuck

Stephen

---

### Post by Alain1 on 2006-07-21
Well, I loaded source-o-matic and pasted the text in kate-editor. 
When I do the following in Terminal, I receive this :
alain@alain-desktop:~$ sudo apt-get install w32codecs
Password:
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
Pakket w32codecs is niet beschikbaar, hoewel er naar verwezen wordt door
een ander pakket. Mogelijk betekent dit dat het pakket ontbreekt,
verouderd is, of enkel beschikbaar is van een andere bron
E: Pakket w32codecs heeft geen installeerbare kandidaat
alain@alain-desktop:~$

---

### Post by OpsVentus on 2006-07-21
Ik schrijf toch maar in het engels anders begrijpt de rest die dit leest het niet ;)

The w32codes aren't in the repository's of Ubuntu. So you have to download them from MPlayer's website. ([http://www.mplayerhq.hu/design7/codecs.html](http://www.mplayerhq.hu/design7/codecs.html))
Download the "essential-20060611"
There are instructions there how to do this. It's just a case of unpack and put it the correct directory.

Good luck,
Bart.

---

### Post by Alain1 on 2006-07-21
OK, can you also tell me in which directory I have to put it and how i can do this?
Thank you

---

### Post by OpsVentus on 2006-07-21
I'm not on a Linux computer at the moment so forgive me if I make a mistake.

Download the file to your home directory.
Right click it and unpack.
Open a terminal and type:
#cd [dir]     *Where [dir] is the directory you have unpacked the file's*
#sudo mkdir /usr/local/lib/codecs/
#sudo cp * /usr/local/lib/codecs/

Then try to open an wmv3 file.

Cheers,
Bart.

---

### Post by Alain1 on 2006-07-21
> **OpsVentus said:**
> I'm not on a Linux computer at the moment so forgive me if I make a mistake.

Download the file to your home directory.
Right click it and unpack.
Open a terminal and type:
#cd [dir]     *Where [dir] is the directory you have unpacked the file's*
#sudo mkdir /usr/local/lib/codecs/
#sudo cp * /usr/local/lib/codecs/

Then try to open an wmv3 file.

Cheers,
Bart.

I can not copy it. I receive the message entry denied in /usr/local/lib/codecs

---

### Post by OpsVentus on 2006-07-21
Sorry, there's the first mistake. Leave out the endslash.
Like:
#sudo cp * /usr/local/lib/codecs

Does that work?

Cheers,
Bart.

---

### Post by Alain1 on 2006-07-21
no it doesn't

---

### Post by OpsVentus on 2006-07-21
Does the directory exist?
#cd /usr/local/lib/codecs

---

### Post by Alain1 on 2006-07-21
> **OpsVentus said:**
> Does the directory exist?
#cd /usr/local/lib/codecs

I think so
alain@alain-desktop:~$ cd /usr/local/lib/codecs
alain@alain-desktop:/usr/local/lib/codecs$ ls
alain@alain-desktop:/usr/local/lib/codecs$

---

### Post by Alain1 on 2006-07-22
I did some terrible things wrong in KDE. So a few people told me to delete KDE and reinstall it. So I did choose for Ubuntu! 
Thanks for helping

---

### Post by patrick295767 on 2006-07-22
> **Alain1 said:**
> I did some terrible things wrong in KDE. So a few people told me to delete KDE and reinstall it. So I did choose for Ubuntu! 
Thanks for helping
[http://www.ubuntuforums.org/showthread.php?t=160070](http://www.ubuntuforums.org/showthread.php?t=160070)

---

### Post by OpsVentus on 2006-07-22
Or try the other directory '/usr/lib/win32'. That's where I've got my codecs.
In terminal go:
#cd [dir] where [dir] is the dir you've got the codecs
#sudo mkdir /usr/lib/win32
#sudo cp * /usr/lib/win32

Should work.

Cheers,
Bart.

---

