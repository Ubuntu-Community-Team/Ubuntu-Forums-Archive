---
title: "Steam - Disk space problem."
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by diablofatt on 2007-06-20
I have steam installed through WINE just fine. When I try and download Counter Strike source wich is a 3743MB download it tells me I only have 120mb free:( I know this isnt true. My Ubuntu is 7.04 and is fairly bare. I know I have the disk space.. what gives?

---

### Post by Cypher on 2007-06-20
You think you have diskspace or you KNOW you have diskspace? Open a terminal and show the output of
```

df -h

```

---

### Post by diablofatt on 2007-06-20
I ran the command 

Filesystem            Size  Used Avail Use% Mounted on
/dev/hdc1              36G   34G  114M 100% /
varrun                506M  100K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M   84K  506M   1% /proc/bus/usb
udev                  506M   84K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/hda              7.6G  7.6G     0 100% /media/cdrom0

---

### Post by Cypher on 2007-06-20
Well there ya go...
**/dev/hdc1 36G 34G 114M 100% /**
That's your root partition nad you have basically used up 34G (Yikes!) and have 114MB free, which is in line with the 120MB that Steam is suggesting.

Since I don't see a "/home" or "/usr" or any other partition, you must just have one 36G partition that contains Ubuntu. I think it's time for some spring (summer?) cleaning before you go any further..

---

### Post by diablofatt on 2007-06-20
I really have very little installed on my machine. I may reinstall? I don't understand how it could fill up so quickly when used so little. Is there any chance this is an error ?

---

### Post by supersonicdarky on 2007-06-20
go to **aplications > accesiories > disk usage analyser** and click **scan filesystem** to see where you space has gone

---

### Post by Cypher on 2007-06-20
Well then that's very strange..there might be some very large files sitting around taking up all the space..

Let's figure out where all your space is going, in a terminal type the following
```

cd /
sudo du -sch * > ~/diskuage.log

```
Once this finishes (expect it take a while). You should have a file that lists ALL the space taken up by all directories on your computer. Now you can see where the space is and figure out what it is..

**Better Yet**, do what supersonicdarky suggested.

---

### Post by diablofatt on 2007-06-20
Thank you for the help.

---

