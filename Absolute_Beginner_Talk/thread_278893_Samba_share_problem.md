---
title: "Samba share problem"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by oliver369 on 2006-10-17
I'm kind of new to the linux world. I would like to mount a windows share via Samba at every startup, I have managed to do so by mounting via the terminal the following command:
sudo mount -t smbfs //mercury/share /home/venus/Desktop/share
this works fine however i would like to know what i should put in the fstab for this to be applied on every startup, so far i have tried a few different methods none of which seem to work...
I would appreciate very much a helping hand:(

---

### Post by caravel on 2006-10-17
I did a search for "samba fstab" and found a few good threads on this.

---

### Post by oliver369 on 2006-10-17
> //lmwire/limewire       /mnt/network/lmwire_smb smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0

i have seen this before and I know it might be a stupid question but is the user and pass in the smbcredentials the pass for the ubuntu machine or the user and pass for the windows machine

---

### Post by Kateikyoushi on 2006-10-17
It should be the username and pass of the machine you are trying to connect to, but you can test it in a minute.

---

### Post by oliver369 on 2006-10-17
I do not have any password or user for the share on the windows computer that is the problem...

---

### Post by TheWizzard on 2006-10-17
alternatively, you can put your (working) mount command in a startup script. 

you need to add youself to the sudoers for the mount command
```
sudo nano /etc/sudoers
```
insert a line withj: 
```
username	ALL=NOPASSWD: /bin/mount,/bin/umount
```

---

### Post by Kateikyoushi on 2006-10-17
Then leave out the credential part.

You can find more examples [here]("http://wiki.colinux.org/wiki/AccessingWindowsDrivesWithSamba").

---

