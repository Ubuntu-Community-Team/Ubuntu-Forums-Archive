---
title: "Apt-move HOWTO help"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by s26c.sayan on 2007-02-09
Hi!!
I have been trying to create a repository on a CD from my deb-s in /var/cache/apt/archives, so that I can add the CD by 'apt-cdrom add' in future installations. 
I tried to use apt-move command following this guide [ HERE]("https://help.ubuntu.com/community/AptMoveHowto"),  just changing dapper to edgy whenever  applicable.
But its not working!! :(

Whenever I issue the command 
```
apt-ftparchive packages pool/main/ \
  | gzip -9c > dists/edgy/main/binary-i386/Packages.gz
```as per the above HowTo, I get this error messege:
```
 bash: dists/edgy/main/binary-i386/Packages.gz: No such file or directory
```

I have followed every instruction in the HowTo so far, but still cant get it to work!! I have no idea about what may have gone wrong! Any help anyone??

---

### Post by tears.of.angels on 2007-12-10
hey, i don't know if you still need help with this, seeing as it was so long ago,
but i was looking for a solution to this as well.

i think i found it, and there's one of 2 ways of doing it.

1) i got 'permission denied' when i didn't do:

sudo -s -H

i was a little wary about "becoming root", so i held off, but that seemed to be what fixed it.

2) an even better way of doing it i have found is to put all of the code into a bash script, then run it like that:

here's mine:

cd /var/www/mirrors/debian
apt-ftparchive packages pool/free/ \
  | gzip -9c > dists/gutsy/free/binary-i386/Packages.gz
apt-ftparchive packages pool/restricted/ \
  | gzip -9c > dists/gutsy/restricted/binary-i386/Packages.gz
apt-ftparchive packages pool/main/ \
  | gzip -9c > dists/gutsy/main/binary-i386/Packages.gz
apt-ftparchive packages pool/multiverse/ \
  | gzip -9c > dists/gutsy/multiverse/binary-i386/Packages.gz
apt-ftparchive packages pool/universe/ \
  | gzip -9c > dists/gutsy/universe/binary-i386/Packages.gz

---------------

mine's been changed for use with gutsy.
once this is run as sudo (sudo ./apt in my case) then it works like a charm.

like i said, don't know if you still needed this info or not, just thought i'd throw it out there for anyone who needs it.

---

