---
title: "Downloaded Firefox - Now What?"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by Sleestack on 2007-01-21
I've downloaded the latest version of Firefox (v 2.0) from their website into a directory and extracted the archive. I want to install it now but the instructions I have tell me to look for .deb files but there are none. I see a lot of .so files and many sub-directories. How can I start the installation?

---

### Post by teitunge on 2007-01-21
Take a look at [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

I believe you will find the answer to a whole lot of your questions there :-)
Including how to install Mozilla Firefox.

Cheers

---

### Post by bruenig on 2007-01-21
With firefox there isn't really what you would call an installation. Basically you extract the tar.gz file, then run the firefox script inside the extracted directory. What I would do, and this is probably not the most complete way to do this but it will work well enough, is this:

replace firefox.tar.gz with what it is actually called.
```
cd /path/to/directory/with/firefox.tar.gz
tar xf firefox.tar.gz
sudo mv firefox /opt
sudo ln -s /usr/lib/firefox/plugins/* /opt/firefox/plugins/
sudo ln -s /usr/lib/firefox/searchplugins/* /opt/firefox/searchplugins/
sudo rm /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```
Then opening from the menu should work.

---

### Post by Sleestack on 2007-01-21
> **bruenig said:**
> With firefox there isn't really what you would call an installation. Basically you extract the tar.gz file, then run the firefox script inside the extracted directory. What I would do, and this is probably not the most complete way to do this but it will work well enough, is this:


Yes, that worked perfectly. Thanks so much for helping this newbie along. :)

---

