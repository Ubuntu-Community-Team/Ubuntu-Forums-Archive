---
title: "Copying files from a mac?"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by Lunchmeat on 2006-09-16
When i converted to Ubuntu, i lost all the music on this machine.. 
Luckily, I have most of the files on a mac on the same network. 
How do i get them from the mac into my linux machine?

I've been looking in the forums for hours, but i can't seem to find the easiest way to do it!

thanks,

---

### Post by Xappe on 2006-09-16
if you are running osx, you can use ssh/sftp to tranfer the files. make sure the mac accepts ssh-connections and use the "Connect to server" function under the Places menu in gnome.

The connection type you want is SSH, and the port is 22.

---

### Post by Lunchmeat on 2006-09-18
Thanks, I am now able to log into the remote computer through the terminal. I can't figure out how to copy the files from the folder in music on the mac ( Mac Hd:music:iTunes etc..) to my /home/user... what command do i use?

Thanks again!

---

### Post by jd65pl on 2006-09-18
Try using nautilus to get the connection as suggested in the previous post by Xappe

```
"Connect to server" function under the Places menu in gnome.
```

You can then just copy and paste files in nautilus file manager

---

