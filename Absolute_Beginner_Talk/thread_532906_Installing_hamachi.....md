---
title: "Installing hamachi...."
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by Ze MoreiRa on 2007-08-23
Please take a look at this:
> giorgi@Gio:~$ cd '/home/giorgi/Desktop/hamachi-0.9.9.9-20-lnx'
giorgi@Gio:~/Desktop/hamachi-0.9.9.9-20-lnx$ ./config
bash: ./config: No such file or directory
giorgi@Gio:~/Desktop/hamachi-0.9.9.9-20-lnx$ make

Copying hamachi into /usr/bin ..
install: cannot create regular file `/usr/bin/hamachi': Permission denied
make: *** [install] Error 1
giorgi@Gio:~/Desktop/hamachi-0.9.9.9-20-lnx$ 

Why is permission denied?
I tried this link: [http://ubuntuforums.org/showthread.php?t=106539](http://ubuntuforums.org/showthread.php?t=106539) but after > install -m 755 hamachi /usr/bin 
it tells me the same thing about permission

---

### Post by Dr Small on 2007-08-23
That needs to be "sudo make", but if you can not get config to work, there isn't much sense of trying make.

Dr Small

---

### Post by Ze MoreiRa on 2007-08-23
I have the same problem with all other software

help [img]http://forum.ge/html/emoticons/help.gif[/img]

---

### Post by qamelian on 2007-08-23
First off, it should be ./configure, not ./config.
Then run make, followed by sudo make install. This is assuming your first attempt where you've extracted the archive to a folder in your home directory.

---

### Post by Dr Small on 2007-08-23
Have you installed build-essential ?
```
sudo apt-get install build-essential
```

Dr Small

---

### Post by Ze MoreiRa on 2007-08-23
> **qamelian said:**
> First off, it should be ./configure, not ./config.
Then run make, followed by sudo make install. This is assuming your first attempt where you've extracted the archive to a folder in your home directory.

yes ./configure 

The same result for that

---

### Post by schorsch on 2007-08-23
The mentioned package "hamachi" contains a README (always a good start to read ;-) ) and when you open this you will see that the application comes as a precompiled binary:
```
Installation

        Hamachi Linux client comes as a single executable binary (hamachi)
        compiled for the platform of your choice. This binary includes the 
        daemon, the control application and the setup utility.

        To install hamachi in /usr/bin run the following command from under
        the root account

                make install
```
So all you have to do is
```
sudo make install
``` and the binary will be copied. If it will run without further configuration .... You will see ...

---

