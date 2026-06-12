---
title: "How to get access?"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by TIGRA on 2006-01-24
Hello,

can anyone please tell me how to login as root/superuser on ubuntu 5.10 GNOME? Or how to get write-rights; for example, I have created a new folder but I cannot put files in it because I do not have any rights to.

Thank you.

---

### Post by 23meg on 2006-01-24
Use sudo. 

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by dueY on 2006-01-24
You can make folders in your home directory.


Or ```
 sudo -i
``` if you like to use the terminal.

---

### Post by Jrdgames on 2006-01-25
open terminal "applications -> accessories -> terminal" and type or paste: *sudo passwd root* make a password then go to: "System -> Administration -> Login Screen Setup" then look for: "Security Tab -> Options -> Allow root to login with GDM (Checked)" then logout and for the username type: "root" (without quotation marks) then for the password type the password you created earlier, now you can do anything on ubuntu you want to but becareful what you do because ubuntu wont warn you if your about to change something that shouldnt be changed or move something to the trash.

---

### Post by aysiu on 2006-01-25
Let's say you created a folder called /fun and you wanted to get read/write privileges for your user, you could type this command ```
sudo chown -R tigra:tigra /fun
``` to change ownership or ```
sudo chmod -R 777 /fun
``` to make it available as read/write/execute for everybody.

---

### Post by TIGRA on 2006-01-30
Thanks guys!

---

### Post by TIGRA on 2006-02-04
Another related question:

I've created a FAT32-partition with the purpose to access it both via Windows and Linux. I've mounted it in /mnt/platte, but I cannot write/execute in it from ubuntu. What to do?

Thx.

---

### Post by aysiu on 2006-02-04
See the fourth link of my signature.

---

### Post by Terry of Astoria on 2006-02-04
About creating the root user password: see
[this post please]("http://ubuntuforums.org/showthread.php?t=125672") - Enabling the root account is strongly discouraged. [Here's a link to the wiki about RootSudo]("https://wiki.ubuntu.com/RootSudo?action=show&redirect=EnableRootLogin#head-a76e0b38808fca380fa209babb080d60ffe0ec8e").
It's been recommended to use 
the gksudo command to run Nautilus, etc.

---

