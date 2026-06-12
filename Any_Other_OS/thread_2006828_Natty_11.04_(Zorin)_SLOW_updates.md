---
title: "Natty 11.04 (Zorin) SLOW updates"
date: 2012-06-19
forum: Any Other OS
---

### Post by markless on 2012-06-19
Hello everyone,

I'm having a bit of trouble installing updates on Natty 11.04 (Zorin) 

Every time I try to run the updates, it will say, "awaiting apt-get to stop" or something along those lines. So I tried to change the server to a different one, and I kept getting the following.

"The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."

-Click "Close"

and I get this, 

"E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory"

Now I did see another post on here that went along the lines of removing the lock, (sudo rm /var/cache/apt/archives/lock) but that was for Maverick. 

Also, I was able to get it to download from the CD in the update settings, but it is INCREDIBLY slow. about this slow... 2890 B/s

It will download, but it will take about three days for it to update. which is fine with me, but I have tried it and most of them fail.

Does anyone know of something that I can do to make the update go faster? Without the updates, there are a lot of APT and ppa things I cannot do.

if anyone can help, I would greatly appreciate it.

Thanks,

---

### Post by HiImTye on 2012-06-19
```
sudo fuser -k /var/lib/lists/lock; sudo rm -f /var/lib/lists/lock; sudo apt-get update
```
run this and then paste the output

---

### Post by uRock on 2012-06-19
Moved to Other OS/Distro Talk.

> Other OS/Distro Talk This forum is for the discussion of other operating systems and Linux distros. No official Ubuntu supported distro questions should be posted here. No bashing/flaming of any OS/Distro is allowed. Please be aware this is not the best place to receive tech support for these OS's/Distro's and users should look for official support channels for those systems.
You my have better results via Zorin's Forums [http://www.zoringroup.com/forum/viewforum.php?f=3&sid=a022f69311a014a8e105ef0a393592fa](http://www.zoringroup.com/forum/viewforum.php?f=3&sid=a022f69311a014a8e105ef0a393592fa)

---

### Post by markless on 2012-06-19
Hey HiImTye. 

Still the same output i'm afraid. Very very slow load. I couldn't copy it from terminal since it was still updating and wipe the highlighted away. here is the screen shot of the bottom.

Let me know if you can think of anything else.

Thank you,

---

### Post by uRock on 2012-06-19
It looks as if Google's repos are what is slowing your updates.

---

### Post by markless on 2012-06-19
How can I change the repositories?

please help. The Zorin forum was useless.

---

### Post by critin on 2012-06-20
Are you following this procedure?

[http://www.zoringroup.com/forum/viewtopic.php?f=6&t=1694](http://www.zoringroup.com/forum/viewtopic.php?f=6&t=1694)

---

