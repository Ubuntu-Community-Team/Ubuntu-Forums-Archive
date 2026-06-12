---
title: "deluge question"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by TechDragon on 2008-02-12
Hi

Installed deluge, went to the plugin's tab and enabled and configured the blocklist.  Deluge downloaded the file but when it goes to import it justs sits at the import screen 2hrs now.  any ideas?

---

### Post by Moop on 2008-02-12
I've found that some of the websites it downloads from aren't always online. Try a different website or manually download a blocklist and import it from file.

---

### Post by TechDragon on 2008-02-12
that is what I have done.  I download the blocklist, it is a gz file is it binary or text?  it is from the site they listed on deluge.

also, the preferences box is greyed out.  How do I get back into the preferences?

---

### Post by mikewhatever on 2008-02-12
> **TechDragon said:**
> that is what I have done.  I download the blocklist, it is a gz file is it binary or text?  it is from the site they listed on deluge.

also, the preferences box is greyed out.  How do I get back into the preferences?

Tar.gz is an archive with the text file inside. Which version of Deluge are you talking about?

---

### Post by Moop on 2008-02-12
I'm not sure why the preferences box is grayed out. When I have trouble with deluge I delete everything in the deluge config folder and that usually fixes it. In your home directory is a hidden folder .config and in that folder is a deluge folder. You can delete everything in that folder unless you have torrents unfinished or something. 

Try the emule ip list (gzip) using this [http://www.bluetack.co.uk/config/pipfilter.dat.gz]("http://www.bluetack.co.uk/config/pipfilter.dat.gz")

Deluge needs to be restarted to load the blocklist.

---

### Post by HappyFeet on 2008-02-12
the following is the way it works for me.
go here for the level1 blocklist(p2p) [http://www.bluetack.co.uk/forums/index.php?act=dscriptca&CODE=viewcat&cat_id=4](http://www.bluetack.co.uk/forums/index.php?act=dscriptca&CODE=viewcat&cat_id=4)
unzip it.
you will have level1.txt
put it in your home folder
open deluges blocklist preferences
choose peer guardian uncompressed
then input path to file /home/yourname/level1.txt
OK

---

### Post by Sammi on 2008-02-12
Make sure you are using the newest version of Deluge: [http://deluge-torrent.org/downloads.php](http://deluge-torrent.org/downloads.php)

The one in the repositories is quite out of date.

---

