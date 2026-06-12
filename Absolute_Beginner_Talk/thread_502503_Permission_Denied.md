---
title: "Permission Denied"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by KingKenny04 on 2007-07-16
Hello all.  So i'm trying to install aircrack-ng.  I've followed the commands that the tutorial on the site ( [http://www.aircrack-ng.org/doku.php?id=install_aircrack](http://www.aircrack-ng.org/doku.php?id=install_aircrack) ) says to enter into the terminal:
> 
wget [http://download.aircrack-ng.org/aircrack-ng-0.9.1.tar.gz](http://download.aircrack-ng.org/aircrack-ng-0.9.1.tar.gz)
 tar -zxvf aircrack-ng-0.9.1.tar.gz
 cd aircrack-ng-0.9.1
 make
 make install

but when i get to 'make install', I recieve the following errors:
> 
install: cannot create regular file `/usr/local/bin/aircrack-ng': Permission denied
install: cannot create regular file `/usr/local/bin/airdecap-ng': Permission denied
install: cannot create regular file `/usr/local/bin/packetforge-ng': Permission denied
install: cannot create regular file `/usr/local/bin/ivstools': Permission denied
install: cannot create regular file `/usr/local/bin/kstats': Permission denied
make: *** [install_userland] Error 1


What have I missed?  Thanks!

---

### Post by testube_babies on 2007-07-16
use ```
sudo make install
```

[More Info]("https://help.ubuntu.com/community/RootSudo")

---

### Post by KingKenny04 on 2007-07-16
so sudo is how i get it to ask me for a password?

---

### Post by testube_babies on 2007-07-16
sudo allows you to do an operation using superuser privileges and permissions:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by KingKenny04 on 2007-07-16
okay, it worked, but now i have another problem, how do i run this program?  its not on my applications list.  Do i have to run it from the terminal?  Sorry, still learning ubuntu.

---

### Post by Majorix on 2007-07-16
Try typing in aircrack-ng in the terminal. Apparently it placed an executable file in your /usr/local/bin called aircrack-ng. By default that folder should be in your $PATH. If it works, then don't worry about what I just said.

---

### Post by Majorix on 2007-07-16
BTW, if you want to have it in your applications menu follow this:
1. Run alacarte:
```
sudo alacarte
```
2. Go to Games (it is a game right?)
3. Click New Item.
4. In the menu that pops up type in "Aircrack-NG" for name.
5. Then /usr/local/bin/aircrack-ng for command.
6. Whatever you find fit for comment. It will show up when you hover your mouse over the icon for the game.

Enjoy :)

---

### Post by Al3xK3aton on 2007-07-16
I advise creating and using a root account so that you don't have to sudo every time.

---

### Post by Majorix on 2007-07-16
Using a root account for daily tasks is not the smartest idea. Because you can then crack your system mistakenly. Typing sudo whenever necessary is ok I think, thats how I do things.

---

### Post by KingKenny04 on 2007-07-16
> **Majorix said:**
> BTW, if you want to have it in your applications menu follow this:
1. Run alacarte:
```
sudo alacarte
```
2. Go to Games (it is a game right?)
3. Click New Item.
4. In the menu that pops up type in "Aircrack-NG" for name.
5. Then /usr/local/bin/aircrack-ng for command.
6. Whatever you find fit for comment. It will show up when you hover your mouse over the icon for the game.

Enjoy :)

no, its a program for cracking WEP keys for breaking into wireless networks.

---

### Post by Majorix on 2007-07-16
??? Are you out of your mind?

---

### Post by testube_babies on 2007-07-16
> **Al3xK3aton said:**
> I advise creating and using a root account so that you don't have to sudo every time.

That's definitely NOT recommended for the average user.  Sudo is a great way of avoiding accidents, and in most cases, setting a root password isn't necessary.  (hey, you can always sudo -s)

---

### Post by rne1223 on 2007-08-22
Ok... I installed aircrack-ng. Now what do I have to use to be able to crack into networks? I mean, been reading and stuff and it seems that I'm going to have to download some type of patch for ipw3945. I want to use aircrack but I'm afraid of losing connection with my wireless card. Do you guys know some type of guide that will help me get use aircrack? Do I need to download some extra patches? Please help...


Thanks in advance

---

### Post by StooJ on 2007-08-22
> 
From [Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")

6. Adult Content/Violence/Illegal Activity: Messages containing sexually oriented/violent/illegal dialogue, images, content, or links to these things will be deleted. Messages with links to or suggesting illegal activity will also be deleted. Posting or linking to any of these could result in a ban.

Breaking into other people's networks is illegal. You won't find help for illegal stuff here.

---

