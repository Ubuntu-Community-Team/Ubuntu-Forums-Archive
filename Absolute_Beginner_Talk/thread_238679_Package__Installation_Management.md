---
title: "Package / Installation Management"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by John Boyd on 2006-08-18
First post; please be patient...

Is there a package installer that handles **all** the formats I've seen used for distributing software?  I want to install Mozilla (*Not* Mozilla Fire Fox and Mozilla Thunderbird, just Mozilla the Browser+Mail program), and cannot seem to get KDE or Gnome to deal with .tar.gz, .run, or any other package I download from elsewhere.  Adept doesn't list Mozilla as an option.

Needless to say, this is a bummer.

Ideas? ](*,)

---

### Post by aysiu on 2006-08-18
Mozilla is in the Universe repositories.

Step 1: [Enable extra repositories](http://www.psychocats.net/ubuntu/sources)

Step 2: Paste this command into the terminal ```
sudo aptitude update && sudo aptitude install mozilla
```

---

### Post by aysiu on 2006-08-18
Alternatively, you could install [SeaMonkey](http://www.mozilla.org/projects/seamonkey/) by copying and pasting these commands: ```
wget -c http://ftp.mozilla.org/pub/mozilla.org/seamonkey/releases/1.0.4/seamonkey-1.0.4.en-US.linux-i686.installer.tar.gz
tar -xvzf seamonkey-1.0.4.en-US.linux-i686.installer.tar.gz
cd seamonkey-installer/
chmod +x seamonkey-installer
sudo ./seamonkey-installer
```

---

### Post by em3raldxiii on 2006-08-18
To my knowledge, there is no such program, but this is because there are some very substantial differences between Linux distributions (and therefore package formats).  Gnome and KDE should both natively handle tar.gz (GZipped Tarballs), as well as a number of other compressed packages.  One of the things you can do is open a terminal (applications>Accessories>terminal) and type:

```

tar --help

```

This will give you a fairly lengthy explanation of how to use the tar archiving program.  The Gnome desktop also uses the program File Roller for handling many different compressed file formats.

So muck about with those programs and see if you can figure some stuff out.

Now, to answer your questions about installing programs.  Have you searched through Synaptic Package Manager for the programs you require?  First you want to enable additional repositories (online resources that Ubuntu uses to gather specific packages from) [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources).   Then go to System>Administration>Synaptic Package Manager.  There, you can click the SEARCH button at the top-right and enter **mozilla** in the search field then press enter.  You may have to wait for a second or two for it to compile the results of your query.  Once it's done, you can scroll down to M and there you should find Mozilla.  Just click the box beside it.  If you get a pop-up that says it requires other stuff, just go ahead and accept.  Then you click on the APPLY button at the top and it will download the required packages, install them, and configure them for you.  Totally painless.  No surfing the 'net and trying to find a howto at all :D

Same thing applies to Thunderbird.  Actually you can follow the same steps for a LOT of different software.

Now, an alternative method might be to open a terminal and enter this:

```

sudo apt-get install mozilla

```

This should do roughly the same thing, only without all the pretty buttons and lights to click on.

Post here if you want more info, have troubles, or just want to discuss this whole process :D

---

### Post by aysiu on 2006-08-18
These two links may help you with installing software in general:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

