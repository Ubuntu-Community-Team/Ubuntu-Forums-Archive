---
title: "Flash &amp; Java don't work"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-04-16
I have checked and it says that I have Macromedia Flash and JRE installed, but in Firefox, neither of them work.  It says that I need to manually install them.

Can anyone help please?

---

### Post by Qrk on 2006-04-16
Flash should be in the repositories you added.

```
sudo apt-get install flashplayer-mozilla
```

For Java I'm not sure of Warty's exact procedure (hint hint, I'd recommend upgrading to breezy)

```
wget http://davyd.ucc.asn.au/projects/misc/sun-j2sdk1.5_1.5.0_i386.deb
```

to get a .deb version of java. I think warty uses java-package to make sure everything gets out right. I can't remember, but Breezy Dapper and Hoary had it. 

```
sudo apt-get install java-package
```

Then finish off with a nice

```
sudo dpkg -i sun-j2sdk1.5_1.5.0_i386.deb
```

---

### Post by Russty of Oz on 2006-04-16
Sorry, I obviously didn't say that I am using Breezy Badger.  

I did the flashplayer install you suggested and it said that it was already installed and that there were no upgrades available.  Still doesn't work!

I have started the second code now but will take about 15 min. to complete.

Russty

---

### Post by Qrk on 2006-04-16
I'm sorry. I remembered the codecs thread, when some else complained they used warty. Looking back it wasn't the OP. I wrongly thought you were using warty. 

Java and flash are both on the wiki page. Just scroll down. Here is the URL again.

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Russty of Oz on 2006-04-16
I got flash from the wiki page before, I uninstalled it using synaptic, and then installed it again from there, I also installed the Firefox plugins, hoping that they would make it work, but no luck there!  Could the fact that I am using FF 1.5 have anything to do with it?

---

### Post by Qrk on 2006-04-16
Yes, that would make a difference. Find your plugins folder for firefox, and make a symbolic link to your java plugin:

Depending on how you installed firefox, you may need to do this: (if you installed by replacing the old version of firefox.
```
sudo ln -s /lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins
```

If you installed firefox 1.5 by extracting it to a directory and running it from there, do
```
sudo cp /usr/lib/mozilla-firefox/plugins/* /path/to/your/firefox/1.5/plugins/directory
```

---

### Post by catlett on 2006-04-16
[http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405) Follow this link and install Automatix. It will make your life easy. An Ubuntu "guru" put this script together that install the things you are struggling with plus much more. Just follow the directions and you will have Firefox 1.5 with all the plug-ins. And much more.

---

### Post by Russty of Oz on 2006-04-16
Qrk; I tried that and it said the file already exists.  Still won't work though (sigh!)

catlett; Yes I used Automatix already, would you suggest I reinstall FF 1.5?

---

### Post by Qrk on 2006-04-16
hmm. I'm afraid I have no experience with automatix. I've never used it. However, you can remove firefox 1.5 using:

```
sudo rm -f /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm -f /usr/bin/mozilla-firefox
sudo dpkg-divert --rename --remove /usr/bin/mozilla-firefox
sudo ln -fs /usr/lib/mozilla-firefox/firefox /usr/bin/firefox
sudo ln -fs /usr/lib/mozilla-firefox/firefox /usr/bin/mozilla-firefox
sudo rm -rf /opt/firefox
```

*from arnieboy

I'd recommend installing firefox 1.5 by extracting it to your home directory and running it from there. Its sooo much easier, and won't mess up your 1.0.7 install. From there, you should be able to use the second method I posted to get 1.5 to use the 1.0.7 plugins.

---

### Post by Russty of Oz on 2006-04-16
Thanks Qrk, I had already decided to use Automatix to reinstall FF 1.5 and at least now the JRE works, so now I can see the weather radar images, but still no Flash!  Oh well, at least that is SOME progress.

---

### Post by Russty of Oz on 2006-04-16
Seeing as reinstalling FF worked with the JRE bit, perhaps I should uninstall then reinstall Flash?  How do I uninstall it?  I can't find it in Synaptic Package Manager.

---

### Post by aquafina on 2006-04-17
I got Flash working 5 mins ago.
You are right, the sudo apt-get install thingy doesn't work.

I suggest you download and install flash player from here [http://physweb.bgu.ac.il/DOWNLOADS/Mozilla/](http://physweb.bgu.ac.il/DOWNLOADS/Mozilla/) 

Good luck

---

### Post by Russty of Oz on 2006-04-17
Thanks aquafina!  That really works well.  And it was so easy to do!

---

