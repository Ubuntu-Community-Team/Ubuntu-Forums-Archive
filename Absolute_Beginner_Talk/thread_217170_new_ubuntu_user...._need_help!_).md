---
title: "new ubuntu user.... need help! :)"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by limberlegs on 2006-07-16
Hello,

I recently took the Ubuntu plunge, and I must say that for the most part I am quite impressed!  I've been reading these forums (which are wonderful!) and trying my best to get the hang of Ubuntu.  

Recently, Easy Ubuntu was brought to my attention.  I have already messed around with trying to get the proper codecs etc for mp3 and DVD playback, and have had some success.  I thought that this would be a good way to take care of most of my problems with one fell swoop.  

I followed the instructions on their website, and the program seems to work fine. It is able to access 27/28 packages and then is outputs the following:

Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/bin](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/bin) ary-i386/Packages.gz  404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free) /binary-i386/Packages.gz  404 Not Found

It then tells me to "fix broken packages first."  Does anyone know what this means, and how I might go about fixing it?

Any help would be greatly appreciated.

Best Regards,

Bryn

---

### Post by Paerez on 2006-07-16
Open the menu and click Add/Remove packages, click advanced. Then click Edit->Fix broken packages.

I think that the freecontrib package list may be down. But don't worry, easyubuntu mostly uses packages in the main packages lists.

If you want to just remove the freecontrib list so you dont see the error anymore, just go to Settings->Repositories and remove the freecontrib menu item.

---

### Post by John.Michael.Kane on 2006-07-16
```
**[COLOR="Blue"]sudo apt-get install -f[/COLOR]**
```

---

### Post by deadgobby on 2006-07-16
You can all so install Automatix.
[http://ubuntuforums.org/showthread.php?t=138405&highlight=Flash+Player](http://ubuntuforums.org/showthread.php?t=138405&highlight=Flash+Player)
Please read before installing,....!!!

---

### Post by limberlegs on 2006-07-16
Thank you to all for your quick replys!  I will try these options and let you know what happens!

---

