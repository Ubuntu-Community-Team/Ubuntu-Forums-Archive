---
title: "Amarok MP3 Support"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by mudflap5 on 2007-07-03
I recently installed Kubuntu, and it seems to be working OK, browsing the web, opening files, ect...  Now I would like to play MP3's.
Followed the procedure listed here:

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

When opening an MP3 w/ Amarok it says,

"No MP3 Support"

It there another way to do this, or should I use a different player?

Thanks for any suggestions.

---

### Post by Inxsible on 2007-07-03
> **mudflap5 said:**
> I recently installed Kubuntu, and it seems to be working OK, browsing the web, opening files, ect... Now I would like to play MP3's.
Followed the procedure listed here:
 
[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)
 
When opening an MP3 w/ Amarok it says,
 
"No MP3 Support"
 
It there another way to do this, or should I use a different player?
 
Thanks for any suggestions.
 you will need to install the mp3 codecs for any player to play mp3s. You can do that by adding the medibuntu repos to your sources and then going on from there.
 
Try this link [http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)

---

### Post by cwood06 on 2007-07-03
you need libxine-extracodecs

```
sudo apt-get install libxine-extracodecs 
```

---

### Post by forestpixie on 2007-07-03
I'd look at the multimedia sticky as well

---

### Post by mudflap5 on 2007-07-03
> **cwood06 said:**
> you need libxine-extracodecs

```
sudo apt-get install libxine-extracodecs 
```

That did it!!  Thanks.


I did read thru the multimedia thread, and tried what it said to do, and I just could not get it to work.

Being a TOTAL noob, all this new terminology and ways of doing things differently is going to be a big learning experience. Been reading alot, even purchased a "Ubuntu for Dummies" book, lots more to learn.
Next project is to get Firefox and Thunderbird up and running!!


Thanks again to all those who posted with advise!

---

### Post by naxmul on 2007-07-11
im a noob here to, but when i tired to run amarok it said that MP3 was not supported, and it froze, and getting the extra codecs worked. thanks  a lot =D

amarok is seriously the best music app for linux.

---

### Post by viajador on 2007-07-11
> amarok is seriously the best music app for linux.

I would go further: it's the best music app for any OS.

---

### Post by SilverDragon on 2007-07-11
> **cwood06 said:**
> you need libxine-extracodecs

```
sudo apt-get install libxine-extracodecs 
```

This also fixed my problem. Thank you very much :)

---

### Post by pat3691 on 2007-07-13
> **Inxsible said:**
> you will need to install the mp3 codecs for any player to play mp3s. You can do that by adding the medibuntu repos to your sources and then going on from there.
 
Try this link [http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)

the commands there are not working I get this: 

   [root@patrice apt]# "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free" |sudo tee -a /etc/apt/sources.list
   bash: deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free: No such file or directory

---

### Post by juice_fi on 2007-07-13
> **pat3691 said:**
> the commands there are not working I get this: 

   [root@patrice apt]# "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free" |sudo tee -a /etc/apt/sources.list
   bash: deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free: No such file or directoryYou forgot echo from the beginning, but you really don't need to do that, because using the following command works fine:

```
sudo apt-get install libxine-extracodecs
```

IMO it's much better to edit sources.list with kate, gedit or similar.

---

### Post by wolfen69 on 2007-07-13
try again 1 line at a time

---

### Post by pat3691 on 2007-07-14
> **juice_fi said:**
> You forgot echo from the beginning, but you really don't need to do that, because using the following command works fine:

```
sudo apt-get install libxine-extracodecs
```

IMO it's much better to edit sources.list with kate, gedit or similar.

What a stupid mistake!!!! I feel stupid now.  Could you guess I am a rookie?

Thanks man

---

