---
title: "Update Firefox from 1.5.0.2"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-08-31
I started Firefox in root and checked the "check for update" then checked "Later" box then closed Firefox. I then restarted Firefox in root and got the message "Done". Then i opened Firefox from the menu and looked at the version and i still had the 1.5.0.2 version. Do i need to do something else to get the new version ?
 Thanks

---

### Post by aysiu on 2006-08-31
Are you using the Ubuntu Firefox or Mozilla's Firefox?

---

### Post by kent41 on 2006-08-31
> **aysiu said:**
> Are you using the Ubuntu Firefox or Mozilla's Firefox?

I'm using Mozilla's

---

### Post by aysiu on 2006-08-31
You say you opened Firefox "from the menu"--is that menu opening the Mozilla Firefox you're using?

Where is your Firefox installed right now--/opt/firefox?

If so, try this: ```
cd /opt/firefox
gksudo ./firefox
``` Check for updates and close Firefox. Then ```
./firefox
``` and see if you have 1.5.0.6 or not.

If that works, we would just have to make sure the symlinks are in place properly. If you installed it somewhere other than /opt, just modify the directions to *cd* to that directory: ```
cd /home/kent41/firefox
``` or ```
cd /usr/local/bin/firefox
```

---

### Post by kent41 on 2006-08-31
> **aysiu said:**
> You say you opened Firefox "from the menu"--is that menu opening the Mozilla Firefox you're using?

Where is your Firefox installed right now--/opt/firefox?

If so, try this: ```
cd /opt/firefox
gksudo ./firefox
``` Check for updates and close Firefox. Then ```
./firefox
``` and see if you have 1.5.0.6 or not.

If that works, we would just have to make sure the symlinks are in place properly. If you installed it somewhere other than /opt, just modify the directions to *cd* to that directory: ```
cd /home/kent41/firefox
``` or ```
cd /usr/local/bin/firefox
```

I used the command line to update. when I check /opt/firefox it is ver. 1.5.0.2

---

### Post by aysiu on 2006-08-31
Hm. I'm not sure what else to try. This is especially baffling because you're using the Mozilla version and not the Ubuntu one...

---

### Post by kent41 on 2006-08-31
> **aysiu said:**
> Hm. I'm not sure what else to try. This is especially baffling because you're using the Mozilla version and not the Ubuntu one...

How do I look for the ver. 1.5.0.6 ?

---

### Post by aysiu on 2006-08-31
Well, theoretically--with the Mozilla version of Firefox--you should be able to self-update to 1.5.0.6. Clearly that's not working, for whatever reason.

You could always just download another copy and extract it to /opt by pasting these commands into the terminal. That last command *needs* the space and period at the end. ```
sudo mv /opt/firefox /opt/firefox1502
wget -c http://ftp.plusline.de/mozilla//firefox/releases/1.5.0.6/linux-i686/en-US/firefox-1.5.0.6.tar.gz
sudo tar -C /opt -zxvf firefox-1.5.0.6.tar.gz
cd /opt/firefox/plugins/
sudo ln -s /usr/lib/mozilla-firefox/plugins/* .

```

---

### Post by kent41 on 2006-08-31
> **aysiu said:**
> Well, theoretically--with the Mozilla version of Firefox--you should be able to self-update to 1.5.0.6. Clearly that's not working, for whatever reason.

You could always just download another copy and extract it to /opt by pasting these commands into the terminal. That last command *needs* the space and period at the end. ```
sudo mv /opt/firefox /opt/firefox1502
wget -c http://ftp.plusline.de/mozilla//firefox/releases/1.5.0.6/linux-i686/en-US/firefox-1.5.0.6.tar.gz
sudo tar -C /opt -zxvf firefox-1.5.0.6.tar.gz
cd /opt/firefox/plugins/
sudo ln -s /usr/lib/mozilla-firefox/plugins/* .

```

Is there some  way  to search all directories for the installed 1.5.0.6 ver ?

---

### Post by aysiu on 2006-08-31
The self-updater would not install the new version to another directory. The whole point of the self-updater is to download only the differences between version--not an entirely new version.

Since I have no idea what's going on, my last post was a last resort... downloading an entirely new version and completely replacing your old version.

---

### Post by kent41 on 2006-08-31
> **aysiu said:**
> The self-updater would not install the new version to another directory. The whole point of the self-updater is to download only the differences between version--not an entirely new version.

Since I have no idea what's going on, my last post was a last resort... downloading an entirely new version and completely replacing your old version.

Thanks I must go to bed now I will try to down load new ver. tomorrow.
Thanks for your help.
 Kent41

---

### Post by kent41 on 2006-08-31
> **aysiu said:**
> The self-updater would not install the new version to another directory. The whole point of the self-updater is to download only the differences between version--not an entirely new version.

Since I have no idea what's going on, my last post was a last resort... downloading an entirely new version and completely replacing your old version.

Thanks AYSIU I used the script you provided and I now have ver. 1.5.0.6 of Firefox.  This is great.:D

---

