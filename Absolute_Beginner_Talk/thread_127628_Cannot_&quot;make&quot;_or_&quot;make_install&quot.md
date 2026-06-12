---
title: "Cannot &quot;make&quot; or &quot;make install&quot;"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by thoffland on 2006-02-09
EDIT: I figured it out... I needed to 

apt-get install make


----------------
I've downloaded some dockapps that I wanted to install, but cannot seem to run the make or make install commands. It tells me that the command is not found. 

I'm running just the Ubuntu Server base with fluxbox... so I'm assuming that there's something I'm missing that would normally have been installed with the complete install?

---

### Post by flight_master on 2006-02-09
Hello!

You need to do the following:

```

sudo apt-get install build-essential g++ gcc checkinstall

```

Also, on Ubuntu, don't use ```
make install
```, instead, use ```
checkinstall
``` that way, you can use Aptitude to remove the packages at any point in the future.


Regards,
Christian

---

### Post by simon_is_learning on 2006-02-09
rememer also that you need to be "root" to be able to make install.

./configure
make
sudo make install

---

### Post by thoffland on 2006-02-10
Thanks! 

No matter what I did I still couldn't get it to work. Then I installed Fluxter and didn't read the README file all the way and of course ran into changes in the desktop background and theme at startup. So... I removed everything and re-installed and just finished reconfiguring... for some reason it seems to be working better now. I changed the slit and it remembered it after a reboot... so this is good. 

I'm still getting an error on the "checkinstall" and "make install" but I found a deb package for what I wanted... so it's ok. Unfortunately I can't remember the error code it was giving me... something like alaconf.m4 or similar. That probably isn't very helpful. 

Just consider this a rambling "thank you" for trying to help!

---

