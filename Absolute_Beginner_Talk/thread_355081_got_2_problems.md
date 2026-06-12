---
title: "got 2 problems"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by zetsumei on 2007-02-06
Ok, I installed gnump3d and when I go to change the /var/music to /home/Music and the user to root it doesn't connect no more.  And when I type my ip address:8888 it takes me to my routers page and I've set it to forward to my computer.

And the other question is I installed apache2, php5, mysql and phpmyadmin and I get the following error when trying to access phpmyadmin and login...also I dont know what the user and password are, it never showed me them.

```

#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)
```

---

### Post by ^rooker on 2007-02-06
1) gnump3: 
- when pointing it to a folder with loooots of media-files, gnump3 can take quite a long while before it responds again. You can monitor if the "gnump3-index" process is still running and spidering through your /home/Music, by executing:

$ top -d 3

- I can't understand why "http://your_local_ip:8888/" should redirect you to your router? And why is your router configured to reroute it back to you (which couldn't work anyway, because you would create a recursive loop.... :confused:)


2) After installing mysql you must set a root password first. 
There's good information about that in the "[perfect setup howto]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06")" page 3 or so I guess...

phpmyadmin uses the local root account to logon as first/default.

---

### Post by zetsumei on 2007-02-06
got the phpmyadmin working but gnump3d is now working but it downloads the file as .mp3.m3u instead of playing it and when i tried to play it it froze up the entire system...

---

### Post by hapablap on 2007-04-07
Is there a way to enable two directories as root?

---

