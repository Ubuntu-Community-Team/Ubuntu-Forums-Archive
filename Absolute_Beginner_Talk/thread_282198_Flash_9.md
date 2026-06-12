---
title: "Flash 9"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by gaby PR on 2006-10-22
I read that is available a beta for Linux of Flash player 9. Anybody know when will be available for ubuntu via synaptic?

I downloaded the gz available.  Anybody have installed it?

---

### Post by uncreative on 2006-10-22
I installed it and am not having good luck getting webpages to recognize that I have flash installed at all anymore.  Some do, some don't.

---

### Post by raul_ on 2006-10-22
I installed it with Automatix2

---

### Post by tiendn on 2006-10-22
U can click on flashplugin-nonfree... which u downloaded.

---

### Post by NESFreak on 2006-10-22
i just got it from auto updating. Don't know from wich repro though.

NESFreak

---

### Post by Esben Kramer on 2006-10-22
I thought it (Automatix2) just installed flash 7? I tried to copy the flash-file into the mozilla/plugins/, but Firefox still didn't recognize it. I then tried Opera, but unbelievably it didn't work in Opera either. I'm trying Automatix2 now.

EDIT: And it worked! If you have trouble installing the flash 9 beta, you should give automatix2 a whirl, as it seems that the flash is actually ver. 9 beta. It would be nice if it told you that it was not ver. 7, though.

---

### Post by Paul133 on 2006-10-22
```
 
wget http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_101806.tar.gz
tar xvzf FP9_plugin_beta_101806.tar.gz
sudo cp flash-player-plugin-9.0.21.55/libflashplayer.so /usr/lib/flashplugin-nonfree/ 
sudo cp flash-player-plugin-9.0.21.55/libflashplayer.so /usr/lib/firefox/plugins/ 
```

Copy and paste this into the terminal. It worked for me.

---

### Post by d4ndy on 2006-10-22
I installed it with the tar.gz, earlier today. I copied the .so file into the plugin directories of firefox and opera, and the adobe site told me I had 7.0.68.0 installed. (Then again, last week it was telling me I had nothing worthy installed, so this is an improvement.) After reading Paul133's post I added the .so to the non-free directory, but it didn't change my perceived version. But like I say, it's already an improvement (even YouTube works), so I'll check back in a few days and see what new ideas have popped up.

---

### Post by raul_ on 2006-10-22
and into the mozilla-firefox or mozilla directories?

---

### Post by Esben Kramer on 2006-10-22
You say that there are some improvements? When you right-click on the movie, does it say flashplayer 7 or 9? Again, if you keep having problems let automatix2 make the install.

---

### Post by d4ndy on 2006-10-23
Also [this]("http://www.debianadmin.com/install-flash-player-9-beta-in-ubuntu.htmlprint/") howto with possibly new repositories. New for me anyway.
But I can't try it till I get home.

---

### Post by bdb on 2006-10-23
What improvements does flash 9 make? Has anyone had luck with the flash 9 beta on AMD64?

---

### Post by raul_ on 2006-10-23
It should fix the sync problem in youtube for example, but it freezes after some time

---

### Post by StayPuft on 2006-10-23
> **Paul133 said:**
> ```
 
wget http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_101806.tar.gz
tar xvzf FP9_plugin_beta_101806.tar.gz
sudo cp flash-player-plugin-9.0.21.55/libflashplayer.so /usr/lib/flashplugin-nonfree/ 
sudo cp flash-player-plugin-9.0.21.55/libflashplayer.so /usr/lib/firefox/plugins/ 
```

Copy and paste this into the terminal. It worked for me.

Worked great for me. Thanks Paul.

---

### Post by fragos on 2006-10-24
I replaced libflashplayer.so in /home/fragos/.mozilla/plugins with the new one from the flash 9 tar.  Works great with Edgy and Firefox 2.0.

---

### Post by d4ndy on 2006-10-24
Thank you, Frogos! I had copied the .so into the plugin directories in usr/lib, in /firefox and /opera, and got up to version 7, but putting into the <user>/.mozilla/plugins directory brought me up to nine.
**not to complain** but is there is similar fix for opera? My <user>/.opera doesn't have a plugin directory. But looking in there, I see a pluginpath.ini which locates them in usr/lib/opera/plugin and usr/lib/mozilla/plugin.  So I guess I can try sudo cp the .so into the mozilla, but my terminal is having an i/o error. I think I logout/login and see if I can get that thing moving...

---

### Post by d4ndy on 2006-10-24
...aaand I'm back. Logout/login didn't work (drat) so I rebooted, and everything got normal again; I copied the .so to usr/lib/mozilla/plugins, fired up opera, and I'm flash version #9 in both firefox and opera!

As I pause to catch my breath, I wonder -- should I be using symlinks instead of copying one file to five or six different directories?
I guess that's tomorrow's lesson.  Thanks for the tips, guys.:-D

---

### Post by fragos on 2006-10-24
This would be a very appropriate use of a symlink.

---

### Post by rahelvey on 2006-11-09
> **Paul133 said:**
> ```
 
wget http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_101806.tar.gz
tar xvzf FP9_plugin_beta_101806.tar.gz
sudo cp flash-player-plugin-9.0.21.55/libflashplayer.so /usr/lib/flashplugin-nonfree/ 
sudo cp flash-player-plugin-9.0.21.55/libflashplayer.so /usr/lib/firefox/plugins/ 
```

Copy and paste this into the terminal. It worked for me.

That did it thanks

---

### Post by evereign on 2006-11-17
great paul133. it worked great for me. mad props to you man.

---

### Post by stoer on 2006-11-17
This latest fix Seems to work a treat, 
my kids can now use the games on disney so many, many  thanks. :)

---

### Post by cies on 2007-01-30
the new place to download is:

[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

i had to find this by many trial and many error...

```

cd ~
mkdir temp
cd temp
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
tar xvzf install_flash_player_9_linux.tar.gz
cd install_flash_player_9_linux
sudo cp libflashplayer.so /usr/lib/firefox/plugins/

```

this works for (k)ubuntu 6.10... at least for me it does.

cies breijs.

---

### Post by deadgobby on 2007-01-30
Here is a vid that may show you how to install that flash player. It moves kinda fast, but that is why there is pause and rewind. Just scroll down tell you see How to Install Flash.
[http://doc.ubuntu.com/screencasts/](http://doc.ubuntu.com/screencasts/)

Gobby

---

