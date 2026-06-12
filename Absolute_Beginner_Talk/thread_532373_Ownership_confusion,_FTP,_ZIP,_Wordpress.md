---
title: "Ownership confusion, FTP, ZIP, Wordpress?"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by mahalie on 2007-08-22
I'm not sure what's going on enough to post a succinct question (my searching isn't effective either) so please excuse the rampling.

I've an Ubuntu Dapper Drake LTS 6.06 LAMP running.

I managed to get phpMyAdmin going fine and have installed MediaWiki and Wordpress several times. I ran into problems with Wordpress at first because I was downloading them on my workstation (XP) and uncompressing the files there and then using FileZilla to connect to my Ubuntu server and put them in the /www/ directory. There was *some kind of ownership/permissions issue * because it wouldn't run at all. However, uploading the TAR ball to my home directory using FileZilla and then untarring it to the target directory via CLI made everything work. Same files, same location, different method.

Now I'm trying to install plugins and **even though the wp-content/plugins/ directories seem to be permissible enough, Wordpress isn't seeing them**. I suspect it's because I unzip them on my XP box, but **I don't know how to unzip on my LAMP** (unzip command not found!).

I will try installing gzip but there's still a big gaping hole in my understanding. Can someone help me understand or at least tell me what exactly I should be reading up on? It's annoying to download zips/tars only to upload them and then unzip them elsewhere. **Any advice appreciated (even RTFM as long as it's RTFM, chapter x, here ->)**

p.s. Also I ran CHOWN MYUSERNAME on the wp-content and plugins directory. Is that bad???

Thanks in advance!!

---

### Post by funrider on 2007-08-22
run the following command on the wordpress root directory:
```
ls -al
```

then the same command one upper level of your plugin dir and in the plugin dir.

---

### Post by feistyfirsttimer on 2007-08-22
An easy way to "unzip" compressed files in Ubuntu is to do it in the graphical interface, using the **Archive Manager**.  You use the Archive Manager to **extract** the files in question, it saves you having to remember the often complicated "gzip" commands!

---

### Post by mahalie on 2007-08-22
Thanks FunRider...will try as soon as my attempt at installing ubuntu-desktop finishes.

Which brings me to FeistyFT...I guess I'll try that once desktop finishes. I really didn't want to go the GUI route, ya know, I want to be hard-core. 

I found a thread related to web directory ownership [here]("http://ubuntuforums.org/showthread.php?p=3235645#post3235645") which suggested adding yourself as owner of 'www' if you're using that instead of home (which I am). I suppose that might fix some things as well!? 

I tell you, I've been looking for the soft intro to apache that would tell me this kind of basic stuff but the apache docs have been really confusing to me.

---

### Post by mahalie on 2007-08-22
```
sudo chown MYUSERNAME /var/www/
```

This fixed my problem :KS

---

