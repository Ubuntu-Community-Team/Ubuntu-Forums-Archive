---
title: "&quot;no rootfile system is defined, please set this with the partition manager&quot;"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by hobs0n on 2007-06-16
Im trying to install Xubuntu on my server and I got some problems ;)

First, the install program partition manager cant make the partitions and make it work on the empty 80GB HDD I have solely for Xubuntu so I created a 70GB ext3 and a 6GB linux swap partition with the gnome partition manager(I got this tip from here, thanks!) so I choose Manuell in the install program partition manager and it sees the ext3 and swap partition manager and when I press next it says "no rootfile system is defined, please set this with the partition manager". How do do I fix this?

---

### Post by floke on 2007-06-16
Change the mount point for the ext3 partition to '/' and off you go - (I think its right click to edit)
btw - what are you doing with a 6gb swap file?? Its a complete waste of space - you'll never ever ever need that much - and if you did your system would be so unusable anyway - a 1g swap is huge enough!

---

### Post by hobs0n on 2007-06-16
Aaah that simple :D Got it working now, its formatting and copying the files now, finally! Its been sooo much trouble with my new server gear and getting it to work. Only OSes that have worked so far is Longhorn Beta 3, XP didnt work to even install and I couldnt find drivers for Server 2003. I hope I get Xubuntu to work as my server OS :)

I have no clue how big the swap was needed to be so ;) And I wont store anything on that HDD, its just gonna be OS´s on it so I really dont need the space. I have 2GB of RAM on the server so I guess 6GB swap is really overkill? Tho Im gonna use it and run lots of torrents and 1-2 DC clients, FTP server and use it as a MediaCenter server too so that might require some RAM?

---

### Post by Golyadkin on 2007-06-16
The old rule used to be to have 1.5 to 2 times your RAM in swap space. However, because people have much more RAM now, that doesn't apply anymore. If you have 2GB of RAM, you won't need more than 1GB to 1.5GB of swap space. Swap space is very very slow compared to RAM anyway, so you would rather have more RAM if you need it.

---

### Post by hobs0n on 2007-06-16
Ok but since I finally managed to get Xubuntu installed I think Il let the 6GB swap partition be there. Thanx for informing me tho :)

---

### Post by Golyadkin on 2007-06-16
No problem :) or "Inget problem", if I am not mistaken

---

### Post by hobs0n on 2007-06-16
Hehe tack så mkt för hjälpen ;) Or spank thee very much kind sir! :D

And now I just created another thread for more newbish questions :)

---

