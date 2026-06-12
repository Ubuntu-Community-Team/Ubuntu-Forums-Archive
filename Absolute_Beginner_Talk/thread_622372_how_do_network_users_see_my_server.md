---
title: "how do network users see my server"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by Kuroda_Shun on 2007-11-24
I just set up the apache2 server. How do my other windows computers see the index page?mkdir/var/ftp/

---

### Post by kelbizzle on 2007-11-24
open your favorite web browser on windows and point it to [http://what.ever.the.servers.ip.is](http://what.ever.the.servers.ip.is) you may need to open port 80 to the other computers.

---

### Post by Kuroda_Shun on 2007-11-24
I have tried 127.0.1.1 from my wifes computer and it cannot see it. Should I enter the routers ip of 192.168.0.101? I am not sure what the ip is because the linksys dosen't show either of the Ubuntu computers on it.
Thanks I got it... Now how do I edit the pages in it?

---

### Post by kelbizzle on 2007-11-24
> **Kuroda_Shun said:**
> I have tried 127.0.1.1 from my wifes computer and it cannot see it. Should I enter the routers ip of 192.168.0.101? I am not sure what the ip is because the linksys dosen't show either of the Ubuntu computers on it.

127.0.1.1 is just like typing [http://localhost](http://localhost). It's what you would type to test the server setup on the actual server. To find the ip address of your server type this into a terminal window. ```
ifconfig
``` Then try [http://192.168.x.x](http://192.168.x.x) on your wifes computer.

---

### Post by Kuroda_Shun on 2007-11-24
That works thanks for your help. 
How do I edit the index page from the other ubuntu gnome computer I have set up?

---

### Post by kelbizzle on 2007-11-24
lots of ways. You can make a new one and just drop it into the folder to replace the old index.html. You can do this by sharing /var/www or by setting up and ftp on the server so you can upload and download the files.

---

### Post by Kuroda_Shun on 2007-11-24
How do I share it? when I drop a new index into the folder it says I dont have the permissions for it. Sorry I am being a pain. This is still really new to me but I am trying.

---

### Post by kelbizzle on 2007-11-24
oh sorry about that. thats because /var/www is a system folder you need to be root to modify files in there.
couple ways
```
sudo cp /home/kelbizzle/Desktop/index.html /path/to/www/folder
```

or browse to where you want it in a root nautilus window 
```
gksudo nautilus
```

---

