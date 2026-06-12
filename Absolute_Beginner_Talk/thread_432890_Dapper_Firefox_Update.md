---
title: "Dapper Firefox Update"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by rotamo on 2007-05-04
Hello. I have installed Dapper. It looks there is not any update for Firefox 2.0.0.2 in Synaptic. Dapper still uses Firefox 1.5 .  Can I install Firefox 2 or will I bear to Firefox 1.5?

---

### Post by viciouslime on 2007-05-04
I think if you enable the backports repository firefox 2 will have been backported to dapper. Preferably though, you should install feisty, dapper is pretty old now.

---

### Post by Acglaphotis on 2007-05-04
You can install it to /opt via getfirefox.com, just unzip and change shorcuts.

-Acgla

---

### Post by rotamo on 2007-05-04
> **viciouslime said:**
> I think if you enable the backports repository firefox 2 will have been backported to dapper. Preferably though, you should install feisty, dapper is pretty old now.
Done already. But as said above FF 2.0 is not listed in Synaptic.
> **Acglaphotis said:**
> You can install it to /opt via getfirefox.com, just unzip and change shorcuts.

-Acgla
Thanks . Then, there is not a way to install new software in Dapper with conventional ways like installing from Synaptic or apt?

---

### Post by reckless2k2 on 2007-05-04
I disagree with the one post saying to upgrade because Dapper is old. Dapper is an LTS version supported for 3 years on desktop and should be able to support newer critical software versions especially since the Firefox 1.5.x line is being abandoned. I imagine that somewhere between now and the time it is abandoned will be an update reflecting the 2.0 line in one of the repositories. 

Until then, you can install directly from the source on the Mozilla site which I admit is not as "friendly" as you might like or check the automatix and or easyubuntu packages because I think they have repos that will bring you up to the 2.0 line. I do believe a backport or alternate repo will bring you to the firefox 2.0 line on Dapper. I'm pretty sure that's how I installed it on my Dapper box.

---

### Post by moreinfo on 2007-05-04
Hi, I also have Dapper, I downloaded Firefox 2 and 'saved' it, it saved it to my desktop as firefoz-2.0.0.3.tar.gz.

I tried to extract it, but nothing - probably not the right idea anyway-, and I tried automatix, Firefox2 is not listed.  
What do I do now?

Thanks in advance.

---

### Post by Acglaphotis on 2007-05-04
moreinfo:

```
sudo file-roller
```

and then extract to /opt.

-Acgla

---

### Post by moreinfo on 2007-05-07
Thanks,

I tried that but it came up with the following error message:

"Extraction not performed

You don't have the right permissions to extract archives in the folder "/opt" "

Thanks again for your reply.

---

### Post by steve.horsley on 2007-05-07
Odd. Try this approach:

1) Text command **gksudo nautilus**
2) In this new nautilus window (which has root permissions), find the file you downloaded, right-click it and choose **Extract To..** and extract it to /opt. 

or fully command line:

1)  get a shell with root permittions:
**sudo -i**
2) change to the /opt directory:
**cd /opt**
3) unzip the downloaded file (use your real username of course):
**tar xfz /home/moreinfo/firefoz-2.0.0.3.tar.gz**

Either way creates a folder called firefox on /opt/. You can launch this version of firefox with the command:
**/opt/firefox/firefox**
which you can put in a launcher if you like. What I do is to replace the symlink in /usr/bin/firefox with one that pointsw to the new version. I do it with these commands:

sudo -i
cd /usr/bin
mv firefox firefox.original
ln -s /opt/firefox/firefox firefox
exit

Note that this new version of firefox will not be updated automatically. You will need to run this version of firefox as root occasionally and go **Help->Check for updates** to keep it up to date (only root has permissions to do this).

---

### Post by moreinfo on 2007-05-11
That worked perfectly.

Thanks

---

### Post by persev on 2007-08-28
> **viciouslime said:**
> I think if you enable the backports repository firefox 2 will have been backported to dapper. Preferably though, you should install feisty, dapper is pretty old now.

3d won't work on Thinkpads with Savage video cards anymore so some of us are stuck with Dapper. There are fixes to get DRI working but every time you do and update it breaks the fix, stuck with Dapper.:(

---

