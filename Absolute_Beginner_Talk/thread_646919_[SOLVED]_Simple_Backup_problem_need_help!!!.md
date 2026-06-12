---
title: "[SOLVED] Simple Backup problem need help!!!"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by Repent on 2007-12-21
Hi I have somehow used up 51.5 GB totaling 511 items in my var/backup folder using up all my hard drive space, how in the heck can I delete them? The Simple Backup config has a option for it but it does not seem to be working I need help.

Thanks for any help.

---

### Post by Dr Small on 2007-12-21
Log into Nautilus as root:
```
gksudo nautilus
```

Browse to */var/backup* and delete the big files to free up some space.

---

### Post by Repent on 2007-12-21
Thank you I deleted all the unwanted backup files but my hard drive still says it's full, here is a list of folders and files and how much room they, use it just does not add up.** Edit: I have 71.9 GB of space on my hard drive and it says it's all being used I don't get it.**

bin  4.4 mb
boot  71.3 mb 
cdrom  0
dev  2.3 KB
etc 7.4 mb
home 5.7 GB
initrd 0
lib 495 mb
lost & found  0
media 18.0 KB
mnt 0
opt  6.7 mb
Proc 511 mb
root 4.0 KB
sbin  6.8 mb
srv  0
sys 237.5 mb
temp  21.2 KB
usr  8.8 GB
var 413.4 mb
initid.img 6.9 mb
initid.img old 6.6 mb
vmlinuz 1.7 mb
vmlinuz old 1.7 mb.

My CPU is running at 98% all the time now I can't even retrieve my e-mail it says I don't have the space, hell I can't even shutdown now I have to do it manually.

Please someone I neeed help.

---

### Post by spiderbatdad on 2007-12-21
what processes are running?

---

### Post by Repent on 2007-12-21
Thanks for your reply but I think the main problem here is my hard drive I just don't understand what it's doing.

---

### Post by blueridgedog on 2007-12-21
Try posting the output of the commands df and sudo du --max-depth=1.  Also, the comment about processes has merit, what process are running that are using up the CPU?

---

### Post by Repent on 2007-12-21
Here's the output for df.

joe203@joe203-desktop:~$ df
Filesystem                 1K-blocks      Used Available Use% Mounted on
/dev/sda1                  75434976  71777844         0 100% /
varrun                       257792       224    257568   1% /var/run
varlock                      257792         0    257792   0% /var/lock
udev                         257792        92    257700   1% /dev
devshm                    257792         0    257792   0% /dev/shm
lrm                           257792     16488    241304   7% /lib/modules/2.6.22-14-generic/volatile
overflow                   1024        36       988   4% /tmp




Here's the output for sudo du --max-depth=1.


[sudo] password for joe203:
16      ./.critter
1680    ./.gconf
80      ./.gconfd
1456    ./.gnome2
8       ./.gnome2_private
704     ./.gstreamer-0.10
912     ./.nautilus
8       ./.qt
627832  ./Desktop
152     ./.kde
4       ./.update-notifier
708     ./.metacity
12      ./.Trash
16      ./.gnome
8       ./.update-manager
268620  ./.evolution
73468   ./.mozilla
412     ./.fontconfig
8       ./.update-manager-core
148     ./.config
8       ./.cups
66464   ./.thumbnails
716     ./.gimp-2.2
2384    ./.openoffice.org2
640     ./.themes
12804   ./.icons
8       ./.glchess
547724  ./ThinkTanks
36      ./.btrl_demo
460     ./.gglokisetup
5696    ./.bravetree
2768    ./.macromedia
28      ./.VirtualBox
132     ./.ut2004
572     ./.loki
1280    ./.local
17940   ./.java
4       ./.tsclient
25452   ./Think Tanks install program
716812  ./btrl_demo
4       ./.xine
1336    ./Various
1580    ./.nvu
16      ./.comments
4       ./.wapi
428     ./.dvdcss
108     ./.emerald
318816  ./vmware-distrib
16      ./.lgames
8       ./.scim
432     ./.file_store_32
60      ./.automatix
16      ./.mplayer
200     ./.dvdrip
4       ./dvdrip-data
56      ./.gxine
8       ./.serpentine
28      ./.gnucash
4       ./Templates
45652   ./.googleearth
28      ./.gftp
4       ./.jamin
745616  ./ThinkTanksDemo
16      ./.tomboy
40      ./.subversion
44256   ./.jagex_cache_32
4       ./.bitrock
20308   ./MGTGames
16      ./.mcop
41892   ./MarbleBlastGold
56      ./.maxgaming
476     ./.garagegames
8       ./.PS2E
14008   ./TT 2
20      ./.ppracer
660     ./.tremulous
102284  ./tremulous
8       ./.fgfs
8       ./.emilia
36      ./.scorched3d
1732    ./.codered
472160  ./alienarena2007
398004  ./2007-12-11--07.38.09
4       ./Public
18308   ./yoda_soccer_073
14008   ./RepsTT
664     ./.xmoto
2380    ./Christmas Clipart
6652    ./SolitareStudio-1.0
8       ./.SolitareStudio-1.0
100     ./Documents
27516   ./TorqueDemoLinux-1.4.2
4       ./Music
4       ./Pictures
4       ./Videos
61328   ./.cache
4       ./.w3m
4       ./untitled 
460     ./.gimp-2.4
43408   ./.wine
81764   ./picasa
106196  ./.picasa
16      ./PicasaDocuments
5632    ./winetrickscache
52      ./eschalon_b1_saved_games
82260   ./Eschalon Book I Demo
6911220 .


And the only processes running are, evolution data server and gnome system - monitor.

---

### Post by Repent on 2007-12-22
Come on guys I really need help here!!

---

### Post by blueridgedog on 2007-12-22
My apologies, I was not clear as to the command, the sudo du --max-depth=1 needs to be run from /, so the commands would be:
```

cd /
sudo du --max-depth=1
```

We can get it working don't fear.

---

### Post by Repent on 2007-12-22
Here you go.

joe203@joe203-desktop:~$ cd /
joe203@joe203-desktop:/$ sudo du --max-depth=1
[sudo] password for joe203:
48      ./lost+found
464732  ./var
12384   ./etc
20      ./media
4776    ./bin
73352   ./boot
108     ./dev
6910812 ./home
4       ./initrd
537812  ./lib
4       ./mnt
6924    ./opt
0       ./proc
54065708        ./root
6736    ./sbin
4       ./srv
0       ./sys
48      ./tmp
9576928 ./usr
71660404        .
joe203@joe203-desktop:/$ 

Thanks for the help.

---

### Post by blueridgedog on 2007-12-22
> **Repent said:**
> Here you go.

54065708        ./root


You have 54 gigs of stuff in /root.  

Lets see what is in there with

```
sudo du /root --max-depth=1
```

---

### Post by Repent on 2007-12-22
Wow it's all in the trash, thats all the backup files I deleted. How can I empty this trash bin it doesn't show up in the root folder?


joe203@joe203-desktop:~$ sudo du /root --max-depth=1
[sudo] password for joe203:
4       /root/.wapi
572     /root/.synaptic
44      /root/.gnome2
4       /root/.gnome2_private
104     /root/.gconf
8       /root/.gconfd
4       /root/.aptitude
376     /root/.loki
72      /root/.gnupg
12      /root/.nautilus
4       /root/Desktop
54062136        /root/.Trash
54065140        /root
joe203@joe203-desktop:~$

---

### Post by blueridgedog on 2007-12-22
Alternatively, now that you know where the problem lies, you could launch nautilus per Dr Small's suggestion of gksudo nautilus and go look into /root using the graphical tool, but I would rather you post what you see via the du so that perhaps we can lend some advice as to what is wheat and what is chaff.

---

### Post by blueridgedog on 2007-12-22
Well, it would not hurt to simply do:

sudo rm /root/.Trash/*

or you could look at the tips here:

[http://www.ubuntugeek.com/how-to-empty-root-trash.html](http://www.ubuntugeek.com/how-to-empty-root-trash.html)

---

### Post by Repent on 2007-12-22
Thank you that did the trick.

---

### Post by blueridgedog on 2007-12-22
I must admin, that after a career in IT, doing "linux tech support" in serial installments is a challenge, but fun.  I am glad you are back up and running.

---

