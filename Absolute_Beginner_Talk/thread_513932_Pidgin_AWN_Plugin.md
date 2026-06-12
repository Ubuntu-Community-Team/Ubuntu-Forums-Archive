---
title: "Pidgin AWN Plugin"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by AegisTalons on 2007-07-31
How do I install the plugin for Pidgin to work with AWN? Please I have looked everywhere. I copied the .so file in different folders including /usr/local/lib/purple-2 and /usr/local/lib/pidgin and ./purple/plugins.

I don't know what to do.

Any ideas appreciated.

---

### Post by Kingsley on 2007-07-31
Make sure you're in the directory that you unpackaged the plugin to and type make.

---

### Post by AegisTalons on 2007-07-31
In the tarball there are 3 files: Makefile pidgin_awn.c pidgin_awn.so

I have just been placing the .so file in the the folders listed below:
/usr/local/lib/purple-2
/usr/local/lib/pidgin
~/.purple/plugins

Should I place all three files in one of those folders and type make?

---

### Post by Kingsley on 2007-07-31
Sure, you can put them in a folder. Then you have to open terminal, cd into the directory, type make, and then sudo make install. Pray for no errors.

---

### Post by AegisTalons on 2007-07-31
I do not understand why I have to make and make install if I already have .so file? Plus when I do it that way, it complains and gives errors pretty much for every line of code on there.

---

### Post by AegisTalons on 2007-07-31
I have even created and set executable permissions on a .la file in /usr/local/lib/purple-2. I have no clue what to do to make this plugin work.

---

### Post by AegisTalons on 2007-07-31
Ok, So I got it installed:

Download the correct file from the source: [http://awn.wetpaint.com/page/Pidgin+Plugin]("http://awn.wetpaint.com/page/Pidgin+Plugin")

Untar it. You will have 4 files, Makefile, pidgin_awn.c, pidgin_awn.h, pidgin_awn.so.

The .so file is the plugin. Developers included source code and header files if you want to remake it yourself. Place the .so in ~/.purple/plugins. Also check the permissions and have it executable. 

Either right click on it and go to properties -> permission and check the box or 
sudo chmod +x pidgin_awn.so

I'm still getting an error with "undefined symbol: dbus_g_proxy_call".

If anyone knows how to fix that, I would greatly appreciate it. Either way, I'm closer than before.

---

### Post by fakie_flip on 2007-08-01
How can I compile Off the record plugin for pidgin? I have pidgin 2.0.2-1 compiled and working in 64 bit Ubuntu right now.

---

### Post by ozp on 2007-10-29
This "make" deal is so sad these days
I'd like to have pidgin awn plugin, but make deal is to far away for me

a .deb would be fine

---

### Post by thc_oi on 2007-11-09
try to install the pigin-dev package

```

sudo apt-get install pidgin-dev

```

i have pidgin_awn plugin installed on my system, BUT i  still have an error. I can see this plugin listed on my plugin menu but cant activate this plugin, this is the error msg :
```

Undefined dbus_g_proxy_call
Check the plugin website for an update

```

---

