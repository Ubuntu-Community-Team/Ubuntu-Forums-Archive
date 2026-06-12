---
title: "[SOLVED] Screem/Bluefish etc upload to my new server?"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by nowhere@cox.net on 2007-10-19
Hi all,

I installed Ubuntu server on a machine and stuck it in a closet so I dont have to listen to it. Everything works fine, apache, php mysql, phpmyadmin, ftp samba everything!

I have my desktop machine running Ubuntu Gutsy Desktop and I have screem and bluefish to try out. What is the best way to set up my server ftp so that these packages can upload to the correct folder? If I log in as any user, I can't get above that user's home dir to get to /var/www. I tried putting a symbolic link in the user's home folder but screem complains that that is not a directory.

I tried just using useradd to make a new user with the /var/www/username folder as it's home but I cannot ssh into the server and log in as that user. It says permission denied. I obviously don't know the useradd command well enough...
sudo useradd -G users --home /var/www/dauser --password dapasswoid dauser

Thanks for any help!
Eric

---

### Post by nowhere@cox.net on 2007-10-23
Bump...

Anyone help with the best know procedure?

Thanks!

---

### Post by nowhere@cox.net on 2007-10-25
My interim solution is to give root dir access to the user uploading the web files. I'm guessing this isn't the ideal solultion...

Thanks,
Eric

---

### Post by mayonaise15 on 2007-10-27
I have a server running in a virtual machine on my Gutsy Desktop using VMWare Server.  What I do is create a system link by going to Places > Connect to Server...  I use SSH to remote into the machine.  I login to this server as root and have it open up in /var/www.  Then I can just open up that link in Bluefish, and I can save files directly to the server as well.  It works just as well with FTP.

---

### Post by nowhere@cox.net on 2007-10-29
Thanks Mayo,

You are opening my eyes to a whole new world of connectivity. Got the whole connect to server thing going now. Just have to figure out how to get bluefish to look there. Gonna play with it for a little while right now.

Thanks so far!

Eric

---

