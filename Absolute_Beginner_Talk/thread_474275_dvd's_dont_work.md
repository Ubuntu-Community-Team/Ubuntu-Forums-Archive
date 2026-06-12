---
title: "dvd's dont work"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Brendan Hart on 2007-06-14
Dvd wont work on my computer , it doesnt understand the format, i did the multimedia install on my computer still doesnt work

---

### Post by netwerx on 2007-06-14
please refer to the following link...
[http://ubuntu-tutorials.com/2006/12/14/how-to-enable-dvd-playback-ubuntu-510-6061-610/](http://ubuntu-tutorials.com/2006/12/14/how-to-enable-dvd-playback-ubuntu-510-6061-610/)

---

### Post by Brendan Hart on 2007-06-14
nup doesnt work one of the files needed in that guide has a 404 error on the page

---

### Post by jfinkels on 2007-06-14
You may want to take a look at this page. Some DVD's are encrypted and require decryption software.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Brendan Hart on 2007-06-14
U guys dont understand, it doesnt even understand the file format

---

### Post by jfinkels on 2007-06-14
> **Brendan Hart said:**
> U guys dont understand, it doesnt even understand the file format

And what is the file format? It may be a corrupted file, or have a file signature problem or something like that....did you make this file yourself? Does it work on another operating system or computer? Did you download it from the internet? The more info the better.

---

### Post by Atomic Dog on 2007-06-14
Probably UDF format disc.  Search the forums on how to deal with mounting UDF formatted discs.  I am not in front of my ubuntu box, but I had to make a change to fstab in order to get it to work.

---

### Post by themis on 2007-06-15
I have the same problem...

Dvd's are not mounted at all,and I get a message "There is probably no media in the drive".

so ..any help really appreciated!!

---

### Post by Brendan Hart on 2007-06-15
nah mine tries to mount says it doesnt support the file type

---

### Post by Nezing on 2007-06-15
Just tried my first dvd on Ubuntu.Yep,it does not work.I tried several disks."File not rercognised" is the message.So after doing some Googling,I found this link,which I'm going to check out.

[http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux](http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux)


RE-LINK.

i tried the correct commands on the site,but in Terminal,it just says,"Command not found"

Back to Google,I guess...

---

### Post by jfinkels on 2007-06-15
> **Nezing said:**
> Just tried my first dvd on Ubuntu.Yep,it does not work.I tried several disks."File not rercognised" is the message.So after doing some Googling,I found this link,which I'm going to check out.

[http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux](http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux)


RE-LINK.

i tried the correct commands on the site,but in Terminal,it just says,"Command not found"

Back to Google,I guess...

You have to type the commands without the dollar sign in the front ($). That's just a marker for your own convenience to signify the command prompt, and to signify that what follows is the command that you should type.

And as for you Brendan Hart...I have no idea. Can you read CD's or other DVDs that you put in the drive? when you put in a disc, what is the output of this command:```
sudo fdisk -l
```

---

### Post by Nezing on 2007-06-15
Cheers jfinkels :D

For anyone else to follow this,go to Terminal,and type:


sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse


Then after the package has loaded,add this in Terminal:


sudo /usr/share/doc/libdvdread3/install-css.sh

For me,my DVD's play as normal.   :popcorn:

---

### Post by jfinkels on 2007-06-15
> **Nezing said:**
> Cheers jfinkels :D

I've done it before, I understand...

---

### Post by meborc on 2007-06-15
> **Nezing said:**
> Cheers jfinkels :D

For anyone else to follow this,go to Terminal,and type:


sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse


Then after the package has loaded,add this in Terminal:


sudo /usr/share/doc/libdvdread3/install-css.sh

For me,my DVD's play as normal.   :popcorn:

exactly... guys, read the **[BIBLE]("http://ubuntuguide.org")** before saying that your dvd's don't play :D ... i almost had a heart attack when inserting my "italian job" dvd right now to test if it works... of course it worked... ohh... i need a cup of hot chocolate now :D

---

### Post by Atomic Dog on 2007-06-18
My problem with some DVD's is that if it's a UDF formatted disc it often is not recognized.  I solved this by changing the line in fstab for the cd/dvd drive from:

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

to

```
/dev/scd0       /media/cdrom0   auto user,noauto     0       0
```

---

### Post by techno-mole on 2007-06-18
i have a similar problem in that if i put a dvd in the dvd drive it doesnt auto mount, if i go to vlc or mplayer etc etc and click open disc i can play the dvd.
note it only does it with films, if i put a data dvd in the drive (game disc, files with pictures on etc etc) it'll auto mount, the cd drive works fine, i can put it a cd-rom or audio disc and they work fine.
this wasnt an issue for me until i updated.

---

