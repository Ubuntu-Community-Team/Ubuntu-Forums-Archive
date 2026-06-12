---
title: "Removing and merging a windows 7 partition?"
date: 2012-01-13
forum: Any Other OS
---

### Post by UncleMonty on 2012-01-13
I am currently dual booting windows 7 and linux mint 12 on a laptop. I wish to get rid of windows 7 and merge the windows partition into linux mint. How can I do this?

---

### Post by Double.J on 2012-01-14
Hi there!

Before anything else, backup... I'd recommend doing a full image backup with start up disk in win7, so if you change your mind it's easy to get back :) Also make double sure you've not left anything on that partition?

To do this, you'd do this using a live cd; boot it up, choosing try not install, and open up gparted. Right click the windows partition(s) and click delete, then apply. Then right click the ubuntu partition(s), this time choose resize/move and use the slider to expand the partition(s) to the left and click apply.

Then update grub, either with boot repair (graphical tool):
```

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

```
or through the terminal: 
```

mkdir /fix [COLOR="Green"]name doesnt matter[/COLOR]
mount /dev/sda[COLOR="Red"]X[/COLOR] /fix [COLOR="red"]X is the number of the ubuntu partition as shown in gparted[/COLOR]
mount -o bind /dev /fix/dev 
mount -o bind /proc /fix/proc 
chroot /fix bash 
sudo update-grub 

```

hope it's useful :) bare in mind it may just be worth shrinking the windows partition and growing ubuntu.. I've been using linux and freebsd for 3 years and still keep an up to date windows... just my tuppence!

---

### Post by carl4926 on 2012-01-14
Consider too. It is wise to make a backup of all your important data, even that in Mint. Just in case.

If something goes south, which it could. You'll be happy you made a backup.

What you propose will change the partitions and the device map will need to be changed too.

Personally, if you are able to back up to an external source, I'd consider starting out with a clean install.

Making a restore set for windows could be useful, more so if you decide to sell the machine.

---

