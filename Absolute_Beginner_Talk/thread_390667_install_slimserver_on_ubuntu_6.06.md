---
title: "install slimserver on ubuntu 6.06"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by thoeng on 2007-03-22
Hi,

By using sudo nano i am now managed to install slimserver

But i am having other problem which ... slimser server unable to detect my music folder .. it says Oops - "/media/hda6/music" doesn't seem to be a valid directory. Try again.


Help !

my HD is divided to 3 which last is my music folder (NTFS)

---

### Post by crispy_420 on 2007-03-22
Did you install NTFS drivers?

Can you read/write to that partition in normal desktop use?

---

### Post by ubuntujonez on 2007-04-14
I&#8217;m running 6.10 and had no problem installing slimserver with: ```
sudo apt-get install slimserver
``` from the command line.

I did have to edit the file: **/etc/default/slimserver** and comment out this line to connect from other machines on the network: 
#HTTP_ADDR=127.0.0.1

Since this is the n00b forum I&#8217;ll add that commenting out means putting a # at the start of a line. I also had to restart via the command: ```
sudo /etc/init.d/slimserver restart
```

Slimserver looks great since the last time I installed it! (2 years).

Cheers.

---

