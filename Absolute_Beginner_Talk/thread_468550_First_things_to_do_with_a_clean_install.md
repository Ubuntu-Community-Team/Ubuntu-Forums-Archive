---
title: "First things to do with a clean install"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by superhaus on 2007-06-09
What are the first things that you usually do with a clean install?

Are there certain programs that you download right away? Certain configuration settings?

I have done dozens (may be hundreds) of Windows installations, but I am pretty new to Linux. I was just wondering.

---

### Post by Bohlio on 2007-06-09
[Multimedia]("http://ubuntuforums.org/showthread.php?t=413624")

Thats a must have on my list :-)

And if you are looking for eye candy...
[Shinytastic Purdyness :-)]("http://www.compiz.org/")

---

### Post by knightnet on 2007-06-15
The first thing I do is to create a text file that notes all of the configuration that I do!
That way, when I have to rebuild - I can do so more easily. I also make a note of the disk partitions I use with both their grub and dev style references, size and labels.

Then it is on with the nvidia driver, reconfigure for twinview.
Next update all packages.
Next I have a config shell script that connects my home folder to my seperate shared partition containing things I don't want to loose if Linux goes belly-up. That includes standard sub-folders (bin , Backups, Documents, Music, Video) and bash config files.
Reconfigure Kate/Kwrite how I like.
Then install my favourites:
- VLC, Firefox, digiKam, exiv2, etc.

Then configure Firefox how I like. Then set up Kontact (I use KDE).
Set up cron for scheduled jobs (e.g. backups).
......

It's a long list!

---

### Post by sailor2001 on 2007-06-15
1st thing I do is go to synaptics (system/administration/synaptics) and check settings to see if all repositories are checked and then reload...Add kde group
2nd is Applications/add-remove (front-end for synaptics) and see what would be nice to have.........
3rd would go to [www.automatix](www.automatix) and check for restricted codecs, player etc.
seems like no matter how many apps you install, you just can't fill up the hard drive...... (I guess you could, but I have never come close to that)  enjoy.......there's a lot out there for you

---

### Post by dbbolton on 2007-06-15
> **superhaus said:**
> What are the first things that you usually do with a clean install?

Are there certain programs that you download right away? Certain configuration settings?

I have done dozens (may be hundreds) of Windows installations, but I am pretty new to Linux. I was just wondering.
here's my to-do list:

1. download some [firefox addons](http://danielsudo.blogspot.com/2007/06/best-firefox-add-ons-of-all-time.html)
2. get some new themes from [http://gnome-look.org](http://gnome-look.org)
3. get some wallpapers from [http://deviantart.com](http://deviantart.com)
4. add my 3 million accounts to gaim
5. install beagle, exaile, openbox, and a few other apps
6. enjoy

---

### Post by nitro_n2o on 2007-06-15
I would say you need the build-essentials and maybe upgrade to Java 6 if you use it 
then make sure you have the flash player for firefox

---

### Post by Phixion on 2007-06-15
I usually:

1. Configure Codecs
2. Install Graphics Drivers
3. Mount HDD's
4. Install Apps (Firefox, VLC etc)
5. Theme my desktop

---

### Post by nymphaeles on 2007-06-15
It depends on how you want use your PC...

I go for this order:

update repositories
upgrade 
install java JDKs
Eclipse
Anjuta
Dr. Python
gFTP
FileZilla
customize Firefox to my taste
multimedia

---

### Post by SkyNet2029 on 2007-06-15
Agreed that this all depends on the intended use of your machine. 
For me, the first thing I do is to
$apt-get install and
its an auto-nice daemon that keeps me from killing my machine (I like to watch dvd's whilst compiling)..
Needless to say I also install build-essential and fakeroot , along with one of my favorites, locale-purge, to free up some drive space (about 80MB on a fresh installation) by removing any locales I don't need or use.

---

