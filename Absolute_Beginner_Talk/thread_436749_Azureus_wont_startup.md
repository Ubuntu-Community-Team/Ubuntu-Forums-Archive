---
title: "Azureus wont startup"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by XTREEM|RAGE on 2007-05-08
After i installed azureus, without any errors, through synaptic, I cant start the program up :S.
Every time i want to use the program it's up for 1 second and it close it self. How can i fix this :S?
I already removed the program and reinstalled it, but no luck. :(

---

### Post by drowner on 2007-05-08
Is it giving you any errors?

Also, do you have anything else open?

I've had troubles with some programs that make use of sound not wanting to be open with another one... particularly my old totem (i dont use azureus, but i know frostwire can play music)

---

### Post by XTREEM|RAGE on 2007-05-08
tnx for the fast response :D
it dont give me any errors btw i use feisty 7.04 and azureus is an bittorent client ;x
I'm an noob when it comes to linux, just got it up and running for a week :).
But i need bittorent and i really like azureus :D

---

### Post by jiminycricket on 2007-05-08
I think there's a fix coming for this soon.

Otherwise install the azureus binaries from their site for now

---

### Post by PartisanEntity on 2007-05-08
Its a bug, close Azureus and:

Download the latest jar file from here:
[http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)

Then rename it to **Azureus2.jar**

```
sudo cp /usr/share/java/Azureus2.jar /usr/share/java/Azureus2.jar.backup
sudo cp ~/Desktop/Azureus2.jar /usr/share/java/Azureus2.jar
```

This will give you the latest jar file.

---

### Post by XTREEM|RAGE on 2007-05-08
ok i will try that when i get home, i'm @ work now ;x

---

### Post by misfitpierce on 2007-05-08
If you want another great torrent finder you might try Transmission or bittorrent... My personal faves b/c thier simple =P

---

### Post by XTREEM|RAGE on 2007-05-08
> **misfitpierce said:**
> If you want another great torrent finder you might try Transmission or bittorrent... My personal faves b/c thier simple =P

But wich one are you using?
And why? only because they are simpel?

---

### Post by Terl on 2007-05-08
I just use bittorrent myself.  It is simple and gets the job done.  

The others are right though about the bug.  Azureus was doing the same thing for me (opening and closing instantly).  So, if you like azureus, follow their instructions :)

---

### Post by dunkyp on 2007-05-08
thanks this was all really great help

---

### Post by kelvin spratt on 2007-05-08
this again was dealt with thoroughly in another thread please read before posting double threads i can do it
so should you thats what the forum is for people get fed up with answering the same question over and over again

---

### Post by XTREEM|RAGE on 2007-05-08
> **kelvin spratt said:**
> this again was dealt with thoroughly in another thread please read before posting double threads i can do it
so should you thats what the forum is for people get fed up with answering the same question over and over again

then i didnt search correclty, but the fixes i saw, where for edgy so i didnt want to wreck my system and didnt try them out.

---

### Post by PartisanEntity on 2007-05-08
> **kelvin spratt said:**
> this again was dealt with thoroughly in another thread please read before posting double threads i can do it
so should you thats what the forum is for people get fed up with answering the same question over and over again

Easy there, we all do it from time to time :)

---

### Post by misfitpierce on 2007-05-08
I use both, I mainly use transmission on my laptop... which is most of the time what I use!

---

### Post by rub1m on 2007-05-14
> **dunkyp said:**
> thanks this was all really great help

Are you still having trouble running Azureus?? I had the same problem before and I deleted .azureus in your home directory. So log in to your account, and then before starting Azureus, delete ".azureus" folder (or rename it if you want to keep it just in case). Once Azureus starts up, it will run the set up wizard again.

---

### Post by REDISISTone.nl on 2007-05-15
> **PartisanEntity said:**
> Its a bug, close Azureus and:

Download the latest jar file from here:
[http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)

Then rename it to **Azureus2.jar**

```
sudo cp /usr/share/java/Azureus2.jar /usr/share/java/Azureus2.jar.backup
sudo cp ~/Desktop/Azureus2.jar /usr/share/java/Azureus2.jar
```

This will give you the latest jar file.

Hey, I had the same problem (im running feisty)
It worked for me, just download the file... (don't forget to get the path right)

---

### Post by xpod on 2007-05-15
> this again was dealt with thoroughly in another thread please read before posting double threads i can do it..so should you thats what the forum is for people get fed up with answering the same question over and over again

Thank god you were`nt around when I joined up:wink: 
Practically every single question that gets asked in the "beginner talk" section has been asked & answered a thousand times before..

We could put big read banners up forbidding repeat questions but still they`d come pouring in.

EDIT: you could try Deluge or KTorrent.....i was an Azureus fan myself until i come across those two

---

### Post by PartisanEntity on 2007-05-15
I recently came across another way to get Azureus to launch again:

[http://ubuntuforums.org/showpost.php?p=2409963&postcount=3](http://ubuntuforums.org/showpost.php?p=2409963&postcount=3)

---

### Post by whatrucrazy on 2007-05-15
I had the same problem with azureus when reinstalling and upgrading to feisty, but replacing the jar2 file did the trick. I seem to remember doing this in breezy or dapper too about a year or so ago.

ah well, worth the effort, i quite like azureus as a bittorrent client.

---

