---
title: "flash plugin non free"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2006-09-20
my update manager told me that my flash plugin non free had to be updated (originally obtained using automatix) once it was installed it asked me to accept some liscensing terms and i agreed except i got this message:

E: flashplugin-nonfree: subprocess post-installation script returned error exit status 1

Now anytime I use apt-get or synaptic it keeps kicking me to the accept liscensing part of the installation, it is as if the installation is not finished and it complains each time I use any kind of updater regardless of the package.

I tried to say no to the agreement but I still get the error, how can I just halt the installation of the nonfree plugins so that it quits bothering me???

When I try to remove it I get 
charles@charles-desktop:~$ sudo apt-get remove flashplugin-nonfree
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  flashplugin-nonfree
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 168kB disk space will be freed.

---

### Post by Drakkor on 2006-09-20
Same here got the auto update and had problems,then tried aptitude install:
drakkor@drakkor:~$ sudo aptitude install flashplugin-nonfree
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up flashplugin-nonfree (7.0.68~ubuntu1~dapper1) ...
Downloading...  done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up flashplugin-nonfree (7.0.68~ubuntu1~dapper1) ...
Downloading...  done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
drakkor@drakkor:~$

But according to Synaptic it's already installed ?

---

### Post by Najand on 2006-09-20
Well, try to update your package database using:
```

sudo aptitude update

```
Then try to remove it by force:
```

sudo aptitude -f remove flashplugin-nonfree

```
Then clean the downloaded offending package and try to upgrade your packages:
```

sudo aptitude clean
sudo aptitude upgrade

```
Then try to install it again using
```

sudo aptitude -v remove flashplugin-nonfree

```

---

### Post by dentaku65 on 2006-09-20
Same here ... I really don't understand the error: **why** flashplugin recall update-rc.d :confused:

---

### Post by Obor on 2006-09-20
Same here as well
Errors were encountered while processing:
 flashplugin-nonfree

Edit: it seems to be affecting quite a lot of people [Related thread]("http://ubuntuforums.org/showthread.php?t=261179") Reply 17&18 in that thread has got some instructions on how to fix it.
It's been reported as a bug [here]("https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/61349")

---

### Post by Najand on 2006-09-20
Hmm, I think I know the reason now;
Have a look at:
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW)
flashplugin-nonfree usually download flash player for linux and install it... You are receiving the error because the adobe site is getting ready for a new version of flashplayer for linux and downloading version 7 is not available now... 
That is why you get error 1.

---

### Post by ajgreeny on 2006-09-20
If you get a problem with flash missing from your system after this cock-up, you can force the version back to the original *7.0.63.3ubuntu3* using synaptic and then wait for the problem to be sorted  by Adobe

---

### Post by jmtjet on 2006-09-20
I fixed it using the code in the link supplied by Obor. Seems OK now. :)

---

### Post by charles.g.moore on 2006-09-20
> **Najand said:**
> Hmm, I think I know the reason now;
Have a look at:
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW)
flashplugin-nonfree usually download flash player for linux and install it... You are receiving the error because the adobe site is getting ready for a new version of flashplayer for linux and downloading version 7 is not available now... 
That is why you get error 1.
worked like a charm, I just went back in and grabbed it again with automatix, thanks for the help

---

