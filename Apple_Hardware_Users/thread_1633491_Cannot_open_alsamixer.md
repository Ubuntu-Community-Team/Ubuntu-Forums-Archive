---
title: "Cannot open alsamixer"
date: 2010-11-29
forum: Apple Hardware Users
---

### Post by jsiret on 2010-11-29
Hello, I'm running ubuntu on my 27inch iMac and I LOVE it.

However as per most people I've run into a few problems concerning the sound, now I have tried many of the methods in these forums editing alsa config etc... and I did get it to work once... however now I am getting no sound, and no alsamixer.

If I type alsa (tab tab) in terminal

alsa        alsactl     alsamixer   alsa-utils  

I am prompted that these are found.

So I type alsamixer

josh:alsamixer
cannot open mixer: No such file or directory


Previously I managed to unmute the channel this way and now it has disappeared.

a) is this a common problem because I cannot find anything in the forums
b) perhaps I have tried too many things and corrupted/created some incompatibilities

and I don't really know where to start.

many thanks,
Regards
Josh

---

### Post by linuxopjemac on 2010-11-29
maybe it's not installed
```

sudo apt-get install alsa-utils
```

---

### Post by matt_symes on 2010-11-29
Hi

Open a terminal and type

which alsamixer

This will tell you its location. Try the full path or reinstall as suggested by the poster above

Kind regards

---

### Post by jsiret on 2010-11-29
I've found it in usr/bin/ however it  still tells me

"
josh@josh:/usr/bin$ alsamixer
cannot open mixer: No such file or directory
"

and the install tells me:

"
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
"

---

### Post by linuxopjemac on 2010-11-29
weird
```
sudo apt-get remove --purge alsa-utils
sudo apt-get install alsa-utils
```

---

### Post by matt_symes on 2010-11-29
Hi

> **linuxopjemac said:**
> weird
```
sudo apt-get remove --purge alsa-utils
sudo apt-get install alsa-utils
```

Yes that is weird.

Try 

/usr/bin/alsamixer

at the command line. and if that does not work reinstall

Are your paths corrupted?

Type

echo $PATH

to check your paths

Kind regards

---

### Post by jsiret on 2010-11-29
Right I removed, rebooted, installed, rebooted, still cannot find alsamixer.

for the echo

"
joshy@joshy:/usr/bin$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
joshy@joshy:/usr/bin$ echo /usr/bin
/usr/bin
"

I assume that is ok?

Regards,

Josh

---

### Post by linuxopjemac on 2010-11-29
your $PATCH looks fine

Could you try as super user ?
```
sudo alsamixer
```

although it should work as a normal user too...

---

### Post by matt_symes on 2010-11-29
Hi

Your paths look correct. Did you try typing (the whole thing)

/usr/bin/alsamixer

at the terminal?

Kind regards

---

### Post by jsiret on 2010-11-29
joshy@joshy:/usr/bin$ sudo alsamixer
[sudo] password for joshy-squashy: 
cannot open mixer: No such file or directory
joshy@joshy:/usr/bin$ cd
joshy@joshy:~$ /usr/bin/alsamixer
cannot open mixer: No such file or directory

And there is DEFINITELY a file there :/ maybe I'll reformat on Saturday, and start from fresh.

My partitions table is a mess anyway, thank you for all your help, very fast as always.

Regards,

Josh

---

### Post by matt_symes on 2010-11-29
Hi

That is really strange. Might be worth doing a file system check before a full install.

Kind regards

---

### Post by bobaer on 2012-10-20
I know this thread is old... but I had the same problem on Ubuntu 12.10 and found a simple solution

I simply deleted asound.conf

---

