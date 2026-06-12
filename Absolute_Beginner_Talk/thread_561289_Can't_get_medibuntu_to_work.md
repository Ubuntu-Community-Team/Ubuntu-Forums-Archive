---
title: "Can't get medibuntu to work"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by ruialexbarbosa on 2007-09-27
Hi,

I followed the medibuntu installation procedures on this page: 

[http://medibuntu.sos-sts.com/repository-old.php](http://medibuntu.sos-sts.com/repository-old.php)

And when I try to  "sudo apt-get update" I get the following error:

E: Type ‘wget’ is not known on line 49 in source list /etc/apt/sources.list

Can someone please help me on this? My main goal was to get my laptop playing comercial dvd's, but now I'm worried with this error.

Thanksb

---

### Post by overkillm on 2007-09-27
Could you post your sources.list here?  I don't think it should contain a wget command anywhere... of course I'm not at my Ubuntu machine so I can't take a look at my own sources.list.

---

### Post by por100pre1 on 2007-09-27
The previous poster is right.

```
cat /etc/apt/sources.list
```

post the results...

---

### Post by Jussi01 on 2007-09-28
It sounds like you added the line on that page to your sources list, not ran it from the terminal. go get rid of the line in you sources, and run it from terminal.

---

### Post by hyper_ch on 2007-09-28
Or you could try the current "howto":

[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

---

### Post by ruialexbarbosa on 2007-09-28
Thanks guys, I had these lines in my .../sources.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O-

sudo apt-key add - && sudo apt-get update
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free


I just removed them and will try again, the system seems ok now.

Thanks again

---

### Post by Seisen on 2007-09-28
Those are the directions to add the medibuntu repository to your source list and how to add the GPG key.

---

### Post by Bablefish on 2007-09-28
Why don't you try the easier way through the terminal, enter the command below (by the way the same command can be found at the offical Medibuntu site) 

sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

---

