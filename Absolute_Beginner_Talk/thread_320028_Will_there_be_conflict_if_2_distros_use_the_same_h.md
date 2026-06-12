---
title: "Will there be conflict if 2 distros use the same /home?"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by happy-and-lost on 2006-12-16
I want to dual boot Ubuntu with Arch (To see if Arch really is *that* fast). I currently have a seperate /home partition as I have a habit of mucking up installs. If I tell arch to use that as /home too, will either systems suffer (I'll be using the same user name/pass on both)?

Ta :KS

---

### Post by Bachstelze on 2006-12-16
It's not recommended, espacially if you use different versions of software that store data in /home.

What you can do though is to mount the partition as something else, say /homes and have two dirs /homes/arch and /homes/ubuntu, then you do some symlinks to have each OS use the correct folder as /home, voilà :)

---

### Post by lamego on 2006-12-16
If both distros do not have major applications version differences that use your data/settings it should be ok. 
If there are major differences once you use an upgraded version you will not be able to use it on the other distro or you may get data/config corruption on some cases...

It all depends on the contents of your /home and on the applications versions...

---

### Post by happy-and-lost on 2006-12-16
Thought so, I'll just symlink the folders I want from Ubuntu's home to Arch. Thanks :)

---

### Post by gaebriel on 2006-12-16
If you do keep the same /home partition, make sure your UIDs, and not just the usernames, are the same in each distro. Otherwise, you might have issues.

---

