---
title: "Permissons problem."
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2008-03-01
Ive got 2 machines. 

Machine 1 is owned by user A with NFS shares:
/home/userA/share1
/home/userA/share2

Machine 2 is owned by user B but cannot mount the shares.

I have tried creating a group called fileaccess and have chowned the shares to 

userA:fileaccess

then set the chmod to rwx for both owner and group.

but im still getting permission denied on the mount -a

what am i doing worng??

---

### Post by yabbadabbadont on 2008-03-01
It has been many years since I last used NFS, but don't you have to add your shares to /etc/exports (or similar) on the source machine before any other can mount them?

Edit: Found this too: [http://www.faqs.org/docs/securing/chap5sec33.html](http://www.faqs.org/docs/securing/chap5sec33.html)

---

### Post by saxuntu on 2008-03-01
Easiest NFS sharing howto ever: [http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing]("http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing")

I've used it myself.

---

### Post by dgrafix on 2008-03-01
ive done that, i have the exports file created and the nfs server installed.

---

### Post by dgrafix on 2008-03-02
LOL, i finally figured out why.

 :rolleyes:

i hadn't restarted the server:
sudo /etc/init.d/nfx-kernel-server restart

I was restarting the nfs-common by mistake.

Its working now, thanks.

---

