---
title: "AOL dial-up?"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by don'tknowlinux on 2005-12-15
I unfortunately have an AOL dial-up connection and a 12 month contract, so i was wondering is there any way to connect on Ubuntu, or am i out of luck
Thanks

---

### Post by Arktis on 2005-12-15
I searched for a min. or two and I found a linux aol dialer:

[http://sourceforge.net/project/showfiles.php?group_id=32335](http://sourceforge.net/project/showfiles.php?group_id=32335)

You're gonna need to compile and install it.  I can walk you through that if you like.

---

### Post by don'tknowlinux on 2005-12-15
That would be perfect!
Thanks!
How do you do it?

---

### Post by don'tknowlinux on 2005-12-15
If you are able to tell me how, you can e-mail me.
Thanks

---

### Post by Arktis on 2005-12-15
Aha!  Nevermind that site, I discovered penggy in the universe repositories.  The package is called 'penggy'.  You need to have universe enabled first: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)
be sure to refresh afterwards, then quit synaptec.

Then in a terminal, type the commands:
```
sudo apt-get install penggy
```

And it's installed!

Next you need to edit the config file:
```
sudo gedit /etc/penggy/penggy.cfg
```
go down to line 80 where it says "# foobar" and remove the # and the space, then replace foobar with your aol screen name.

Then go to line 181 where it says "# modem_device = /dev/ttyS0", remove the # and the space, and replace /dev/ttyS0 with what your dial-up modem is called by.  How do you find this out?  Go to System > Administration > Networking and in the connections tab, your dial-up modem will be in the list.  It will say something like "**Modem connection** The interface *blah* is active/not configured".  Whatever *blah* says is what your modem is called by, *unless you haven't configured it yet in which case this may be wrong*.  In my case, this is "ppp0", and so I would edit line 181 to say "modem_device = /dev/ppp0".  So, if your modem isn't configured yet, and you want to be sure, you can highlight "Modem Connection" and click the properties button, go to the modem tab, and for 'modem port' click "autodetect" and this should tell you what you'll need to identify your modem on line 181 of the penggy.cfg file.

Then edit the secrets file:
```
sudo gedit /etc/penggy/aol-secrets
```
Change line 4 to have your screen name and password (in that order) and remove the # of course.

Then the phonetab file:
```
sudo gedit /etc/penggy/phonetab
```
change line 8 to have the phone number you usually dial to connect to aol.  Remove the #.  You can add more connect numbers to the other lines too if you like.

You're done editing now.  Just run:
```
sudo penggy
```
whenever you want to connect.

---

### Post by don'tknowlinux on 2005-12-15
right now i have no way to connect to the internet using linux.  So is there any way i can get it on Windows and transfer it to Ubuntu?
Thanks for all your help!

---

### Post by Arktis on 2005-12-15
You can download it from:
[http://packages.ubuntu.com/breezy/net/penggy](http://packages.ubuntu.com/breezy/net/penggy)

If you don't have your windows partition mounted in ubuntu so you can get the file from it once you have downloaded it, go to System > Help > Ubuntu 5.10 Starter Guide > Windows Partitions for information on how to easily mount your windows partition so you can grab the downloaded package and install it.

You'll want to use dpkg to install it:
```
sudo dpkg -i /path/to/package.deb
```
If you need to satisfy any package dependancies, search for the needed packages at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and grab them, making sure they are for breezy.

**Edit:**  I also found a gui wrapper for penggy.  It's not required of course, but having a gui is nice.  [http://www.casano.com/penggy-wrapper/index.html](http://www.casano.com/penggy-wrapper/index.html)
I'm gonna test that out for you too and post back with instructions if I can get it working.

---

### Post by don'tknowlinux on 2005-12-15
Ok, i'll do that. Again thank you so much, you're a lifesaver.

---

### Post by Arktis on 2005-12-16
No problem.

About the GUI wrapper:  I've been fiddling with it for about 30 minutes and I can't get it to work properly.  It's not that great anyways, but I'll keep trying nonetheless.  After all, I may want to put together a HowTo for AOL users at some point.  Oh, and I made a slight change to the instructions for penggy.

---

### Post by denisesballs on 2006-02-07
This all works, and I connect, but the DNS will not work. I can ping the nameserver they give me, but nothing else, i.e. yahoo.com. Any reason why this would be happening?

---

