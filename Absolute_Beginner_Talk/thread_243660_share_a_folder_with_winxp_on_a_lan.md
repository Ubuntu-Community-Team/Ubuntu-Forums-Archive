---
title: "share a folder with winxp on a lan?"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by bplus on 2006-08-25
Hi,
I have a lot of data in a folder that I want to shift to a winxp pc on a lan.
Normally on winxp Id just make that folder shared and then go to the other winxp PC on the lan an type //some_ip_address/name_of_folder

Is there an equivalent way to make a folder shared on ubuntu?

thanks in advance!

---

### Post by benfindlay on 2006-08-25
There is, but you need to install samba server first, then configure it for use with a windows network. Once samba is working you can share folders with windows rather easily, but for what you want to do it's probably quicker to share the folder on the windows computer then copy it across that way

---

### Post by bplus on 2006-08-25
Ah but the data is on an ubuntu pc. Am I misuderstanding you?

---

### Post by Jerome36 on 2006-08-25
Like benfindlay already suggested, you're going to need to install "Samba."  It'll allow you to share folders on your Linux computer, and be able to see them over your network, on your Windows Machine, and vise-versa.

There should be a How-To, and other help, on this forum about setting up Samba, so just do a little search.

---

### Post by dmeehan on 2006-08-25
try here: [http://ubuntuforums.org/showthread.php?t=238135](http://ubuntuforums.org/showthread.php?t=238135)

post number 2 is the one with the link you want. it worked a treat a for me

---

### Post by bplus on 2006-08-26
ta thanks!

---

