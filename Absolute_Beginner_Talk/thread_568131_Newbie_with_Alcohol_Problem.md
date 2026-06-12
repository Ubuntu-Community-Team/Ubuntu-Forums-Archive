---
title: "Newbie with Alcohol Problem"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by mmurray21 on 2007-10-05
I just installed Ubuntu on a machine I am setting up for my kid. I was going to go the dual boot route, but decided to see if wine would give me what I need. To my surprise, without reading a manual I got one of his software programs up a running on the first try. Now I have a more difficult problem that I wanted to ask about before attempting. 

I usually rip his educational games to iso's and run them using alcohol 52%. He is only 4 so I dont want him flipping the disks around. 

Is it possible to run alcohol on wine and run the product that way? Or do I need to find a way to mount the iso natively and then find a way to get wine to recognize it.

For the games that install straight way this isn't an issue, but some games (I spy series) requires the disk to run.

Thanks in advance.

---

### Post by LaRoza on 2007-10-05
If you get a program like Alcohol for Linux, you'd be able to mount the virtual drive. At the moment, I don't know of any such program, because I don't have a need. I will search and report back...

Acetoneiso

[http://www.ubuntugeek.com/mount-and-unmount-isomdfnrg-images-using-acetoneiso-gui-tool.html#more-213](http://www.ubuntugeek.com/mount-and-unmount-isomdfnrg-images-using-acetoneiso-gui-tool.html#more-213)

Download: [http://kde-apps.org/content/show.php?content=44805](http://kde-apps.org/content/show.php?content=44805)

---

### Post by kellemes on 2007-10-05
Can't answer your question I'm afraid..
Just wanted to point out it's maybe interesting to look for GNU/Linux educational software, there is a lot.. [Edubuntu]("http://www.edubuntu.org/") includes a lot out of the box.

---

### Post by mmurray21 on 2007-10-05
Thanks for the tip. I downloaded some of the games already, but have not had a chance to dig into them. Looks like I will busy evaluating software tonight. 

If we pass this test, I am going to try to get my wife to migrate her laptop over.

---

### Post by blazercist on 2007-10-05
yes goto  ubuntuguide.org for a guide on how to mount the iso natively, then just add the mounted iso as a drive under winecfg, it should work just fine

---

### Post by arsenic23 on 2007-10-05
The easiest way to do this is just to have the games mount into a folder every time you boot by modifing your fstab ( /etc/fstab ).  Just add a line like this one to mount your iso (noe I've mounted mine in the /mnt folder so any user can have accesss too it, but you could just as well mount it in your son's home folder, it doesn't matter ) ::

> /home/*******/Games/broodwar.iso /mnt/starcraft  iso9660 ro,loop,auto    0       0

This will mount the iso into a folder, then all you have to do is alt+f2 and type winecfg.  Under the dives tab you can set wine to see any folder you want as a lettered drive.

---

### Post by Niniel on 2007-10-05
The games that require the CD are usually copy protected... how do you deal with those?

---

### Post by LowSky on 2007-10-05
I thought you had a drinking problem.... LOL

If you want try Daemon Tools... I believe there is a linux verison

---

### Post by LowSky on 2007-10-05
> **Niniel said:**
> The games that require the CD are usually copy protected... how do you deal with those?

Just look for sites that deal with cracked EXE files. Then just placed the new EXE where the old one is installed to, and the game should boot.

---

### Post by mmurray21 on 2007-10-06
> **arsenic23 said:**
> The easiest way to do this is just to have the games mount into a folder every time you boot by modifing your fstab ( /etc/fstab ).  Just add a line like this one to mount your iso (noe I've mounted mine in the /mnt folder so any user can have accesss too it, but you could just as well mount it in your son's home folder, it doesn't matter ) ::



This will mount the iso into a folder, then all you have to do is alt+f2 and type winecfg.  Under the dives tab you can set wine to see any folder you want as a lettered drive.
How do I launch the editor using sudu?

---

### Post by bulletxt on 2007-10-07
if you just need to read from a ISO then just do a :

sudo mount -t iso9660 -o loop file.iso $folder


else


if you a need a complete software to manage all type of images like mdf nrg bin img ecc then just install AcetoneISO2 software as it just works great
[www.acetoneteam.org](www.acetoneteam.org)

---

### Post by arsenic23 on 2007-10-07
> **mmurray21 said:**
> How do I launch the editor using sudu?

```
gksudo gedit /etc/fstab
```

---

### Post by HermanAB on 2007-10-07
"Alcohol problem"  Thank you for sharing that.  I think you should try again on the "Backyard" forum...
;)

---

