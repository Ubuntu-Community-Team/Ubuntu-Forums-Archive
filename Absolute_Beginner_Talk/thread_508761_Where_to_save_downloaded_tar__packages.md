---
title: "Where to save downloaded tar / packages?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by dsewell on 2007-07-24
Stupid question, but where should one save downloaded tar / packages?

e.g. I am trying to setup Torrentflux, and the instructions are as follows.  Where is the best place to save the tar file?

      > Step 3: Get Torrent-Flux
      > Now you can go download torrentflux:
      > [http://www.torrentflux.com/](http://www.torrentflux.com/)
      > The files are hosted by SourceForge:
      > [http://prdownloads.sourceforge.net/t...ar.gz?download](http://prdownloads.sourceforge.net/t...ar.gz?download)
      > Once the file is downloaded, you can untar it in the usual way:
      > Code:
      > $ tar -xvzf torrentflux_2.1.tar.gz

Similarly, where should I save the webmin tar file?  I downloaded to the desktop as I didn't think it reallt mattered.  Then untar'ed the file and installed.  But, I can't delete the untared directory from the desktop as some of the files are in use by webmin.

Sorry for the dumb question, but I can't find any quidance on where to save the files and where to extract the packages.  All guides / tips just say download and unpack.  But, not where!!!

Any clues?

Regards,

Dean

---

### Post by doomster on 2007-07-24
probably somewhere in your home folder. its the safest place :D
there you can untar them and work on them

ps: i think i will get bored of saying this: there is no stupid question. none was born with knowledge

---

### Post by Mornedhel on 2007-07-24
Or, if you feel like it, you could install stuff in /opt. I think that's what /opt is for. Someone correct me on this ?

---

### Post by Cypher on 2007-07-24
You should download all files to your home directory. I usually create a directory called "downloads" and make that the default directory for Firefox.

During installation, all binaries will usually want to go into /usr/local/bin and libraries into /usr/local/lib. "/opt" is just one of those directories that is around but isn't used much.

The LSB (Linux Standard Base) which defines the use for particular directories had a use for it, but frankly in my 10+ years of Linux usage I've never come across any consistent use for that particular directory. Some vendors of tools seem to use it as an installation base for full-applications, but single binaries usually go directly into /usr/local/bin.

---

### Post by bogr@ on 2007-07-25
My /home directory is full (98%), but I can't figure out how to change the default download directory to an empty one:

/                       :17% used of 18.3GB
/boot                 :4% used of 957MB
/data                 :15% used of 9.2GB
/home               :99% used of 9.2GB 
/tmp                  :1% used of 957MB
/var                   :73% used of 957MB
/media/External  : (ntfs) 29% used of 111.8GB <- this wiil eventually be formatted to ext3 when I completely ditch windows

Any help on how to change the default download directory, or which would be best, is much appreciated.
Thanks

---

### Post by Cypher on 2007-07-25
In firefox..Edit->Preferences, choose the Main tab if not already selected. There is an option to "Save Files to", here you can direct it to any directory you have write access to.

Since you have a /data and /home partition, and have space in /data, you might want to move over unused stuff from /home to /data.

---

### Post by asmoore82 on 2007-07-25
> **Cypher said:**
> You should download all files to your home directory. I usually create a directory called "downloads" and make that the default directory for Firefox.

During installation, all binaries will usually want to go into /usr/local/bin and libraries into /usr/local/lib. "/opt" is just one of those directories that is around but isn't used much.

The LSB (Linux Standard Base) which defines the use for particular directories had a use for it, but frankly in my 10+ years of Linux usage I've never come across any consistent use for that particular directory. Some vendors of tools seem to use it as an installation base for full-applications, but single binaries usually go directly into /usr/local/bin.

archlinux is one of the few distros that is using /opt for its intended purpose...

gnome and GDM are installed at /opt/gnome
firefox is installed at /opt/mozilla
openoffice at /opt/openoffice

in real world I can't really say either setup is better than the other, execpt that in odd standard
'/opt' setup it would be easier to purge software in an emergency, but why in the world would anyone ever want to get rid of the greatest OpenSource apps ever?

---

### Post by jcullen on 2007-07-25
I thought I would help with this one. 

I have always created a folder named /usr/local/downloads for a centralized area for downloads. 

To create the directory or folder do the following.  

1:  From your menu bar click on places. 
2:  Click on filesystem.
3:  Click on USR.
4:  Click on LOCAL
5:  Then from your menu bar click on File
6: Create a folder and name it DOWNLOADS

You now have a directory and centralized location for your downloads. 

Next configure your browser to download into that directory. I will explain that process below. 

1:  Open Firefox:
2:  Select Edit -> Preferences 

Select the radio button :  Save file to. 
Then click on the browse Icon:

Choose Filesystem in the left frame
Choose the USR folder on the right frame.
Then choose LOCAL again on the right frame.
Then choose DOWNLADS on the right frame. <-- This is the directory that we created earlier.
Then click the "OPEN" button.

You should now see save files to:  /usr/local/downlads

Click close.

Now everything that you download in your web browser will be in /usr/local/downloads.

---

### Post by asmoore82 on 2007-07-25
> **jcullen said:**
> I thought I would help with this one. 

I have always created a folder named /usr/local/downloads for a centralized area for downloads. 

To create the directory or folder do the following.  

1:  From your menu bar click on places. 
2:  Click on filesystem.
3:  Click on USR.
4:  Click on LOCAL
5:  Then from your menu bar click on File
6: Create a folder and name it DOWNLOADS

You now have a directory and centralized location for your downloads. 

Next configure your browser to download into that directory. I will explain that process below. 

1:  Open Firefox:
2:  Select Edit -> Preferences 

Select the radio button :  Save file to. 
Then click on the browse Icon:

Choose Filesystem in the left frame
Choose the USR folder on the right frame.
Then choose LOCAL again on the right frame.
Then choose DOWNLADS on the right frame. <-- This is the directory that we created earlier.
Then click the "OPEN" button.

You should now see save files to:  /usr/local/downlads

Click close.

Now everything that you download in your web browser will be in /usr/local/downloads.

***_MASSIVE WARNING_***

No user other than 'root' should have the ability to arbitrarily create files and folders outside of their home directory. If you were able to create this folder and MORE importantly, If firefox is allowed to save to this location when running under Your user account, You have bonked the filesystem permissions on your system.

The multiple conversations/arguements over the last few days about security and AntiVirus (read: waste of time) have led to the point that "Linux is secure." ...
people demand to know why and the Simple answer is that
"Linux is secure **because** Linux is secure."

sorry if I come on too strong but saving download from the wide web outside of your Home directory is a bad Idea for a multitude of reasons. If you absolutely must, they should still remain in the /home and be read/write to a group account on your system and NOT to everyone. I.E.

```
~ $ ls -l /home/
...
**drwxrwx---** 2 root **users** ... share
...
```

:D *NIX ~ multiuser and secure from the ground up

---

### Post by dsewell on 2007-07-27
Thanks guys.

Just some background on my setup.  I'm running Ubuntu as a headless Media / Torrent server on a low power EPAI mainboard and booting from USB flash (/dev/sdb).  The system has a 500gb HDD installed that I use for the media and backup (/dev/sda).

Currently, /dev/sda is mounted under one of the users in the home directory as follows:  /home/dean/storage.  As there is little space on the USB (/dev/sdb), I need to use the HDD for downloads.

Is it thus possible to have multiple mounts?  So, I mount the entire drive as above, but sub-directories to other places.

e.g. mount a sub-dir on HDD called "downloads" directly to /home giving /home/downloads?  (I will also have /home/dean/storage/downloads in this case).

Also, I need to map my back-up sub-dir to /usr as apparently SBackup can not write to /home.

If this is possible, how do I do this and how do I make it persistent?  (I tried adding this line "/dev/sda1 /home/dean/storage Ext3 defaults 0 0" to fstab and saving, but it is removed every time I reboot.  Maybe this is a quirk of booting from USB?  

Does that make sense?

Thx again.

---

### Post by Mornedhel on 2007-07-27
You can in the worst case link a folder named /home/downloads to the relevant folder on the HDD. I don't know if it's very good practice to create non-user-directories in /home though...

---

