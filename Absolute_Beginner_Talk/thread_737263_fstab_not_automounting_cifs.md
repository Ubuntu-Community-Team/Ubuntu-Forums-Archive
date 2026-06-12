---
title: "fstab not automounting cifs"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Nythain on 2008-03-27
ok, so i've googled and searched and everything, and aparently the only solution is still my problem...

fstab wont automount a cifs share... i havent had this problem before, even using the same release (gutsy)... so im hoping someone has a solution...

first my fstab entry
```

//192.168.2.138/Stuff /data     cifs    auto,user,rw,noperm,credentials=/home/rune/.cifscredentials,iocharset=utf8,file_mode=0777,dir_mode=0777  0 0

```

i have tried it with and without auto, with and without user,  i have the mountpoint owned by me, and chmod 777, so i know its not a write permission of some sort...

it mounts fine if i manually mount it, but i need it to mount at boot as i keep all my themes and images and etc. on the share

the only solution ive found so far is to add an entry into rc.local to mount the share with a 30 second sleep, as to make sure the network is up and running first...

any suggestions beyond this work around??? any clue why it might be taking so long for the network to come up??? this is the first time i've encountered this problem on gutsy (out of like a billion different gutsy installs) and im really confused whats so different this time

---

### Post by spych102 on 2008-03-27
Is the server network address fixed?

---

### Post by Nythain on 2008-03-27
yeah... it mounts just fine manually... and it mounts ok with the rc.local work around, wich i guess im stuck with... dont know why it takes so long for network connection, or why now, its happening after mounting the filesystem, but i guess ill live with it... so far no harm no foul, except i have to copy any wallpapers i want to use over to this machine, because now the share mounts after/during gnome load, so it cant grab the wallpaper

---

### Post by spych102 on 2008-03-27
By the way, it would be a good idea to put your credentials file in /root so that only root can read it. Sorry I haven't helped you with your actual question though.

---

