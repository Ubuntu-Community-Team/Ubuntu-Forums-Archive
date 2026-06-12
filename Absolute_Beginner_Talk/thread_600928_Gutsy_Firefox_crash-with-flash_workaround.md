---
title: "Gutsy Firefox crash-with-flash workaround"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by Candace on 2007-11-02
Hello,

Workaround for firefox crash: I have installed Epiphany though which works like a charm. Since I am in school and I depend on my computer, I don't think I'll be using firefox again until it gets fixed or I find a solution that works for my laptop. :-(

History:
Like many who have upgraded from Feisty 7.04 to Gutsy 7.10 in the last few weeks, I have. I have also experienced problems with firefox crashing on any page that has flash embedded (newsgroups, twiki pages,  posting to Ubuntu pages, etc). I didn't have any problems with youtube although others do. 

I have an HP 2020 with wireless card WLAN 1390 Broadband. I have tried all the suggested fixes I could find and none of them work, such as these 3:

[http://ubuntuforums.org/showthread.php?p=3660873](http://ubuntuforums.org/showthread.php?p=3660873) - removing libflashplayer
[http://ubuntuforums.org/showthread.php?t=596381](http://ubuntuforums.org/showthread.php?t=596381) - simply kill firefox, not really a fix
[http://www.backports.ubuntuforums.org/showthread.php?p=3620137](http://www.backports.ubuntuforums.org/showthread.php?p=3620137) - remove flash files and reinstall from synaptic

---

### Post by Billy_McBong on 2007-11-02
[COLOR="Blue"]you could try installing the gnash firefox-plugin(an alternative flash player)
```
sudo apt-get install mozilla-plugin-gnash
```
i have not tried it so im not sure if it will help with crashes but i might install it soon because these the crashes are annoying me too[/COLOR]

---

### Post by lgcabarcas on 2007-11-02
sudo apt-get install flashplugin-nonfree        this worked for me, i have a 64 bit machine and used a script to get the flash plugin when i was running feisty. with the gutsy upgrade FF just crashed after the apt-get everything seems to be just fine.

---

### Post by Candace on 2007-11-02
```
sudo apt-get install mozilla-plugin-gnash
```

I tried this install (and I rebooted) and firefox *still* crashes on pages with flash, so I am posting this still from Epiphany. Thanks for the idea anyway.

---

### Post by J0Sb31R on 2007-11-05
Its probably because you used nspluginwrapper on feisty 64bit?

How to fix this:

Completely remove any traces of the old nspluginwrapper (if found it on these forums) in

/usr/lib/firefox/plugins/npwrapper...
/usr/lib/mozilla/plugins/npwrapper...
/usr/lib/nspluginwrapper

And then just do a

```
sudo aptitude reinstall nspluginwrapper flashplugin-nonfree
```

this should fix problems on firefox amd64

---

### Post by blee1170 on 2007-11-07
I am having the same problem.

I have a fresh install of 7.10 on a 32bit system. Firefox seems to crash when I go to my google homepage.  It is very annoying. 

I did reinstall the flash plugin, but that did not seem to help. 

I don't have any Add-ons installed.  Just plain old firefox.

Thanks,
Brian

---

### Post by blee1170 on 2007-11-16
For me it seems like it keeps crashing when I have gmail/gchat going in one of the tabs.  

I have removed the flash plugin and installed the nonfree one.  

Any other idea's?

---

### Post by oberoc on 2007-12-08
Ok, ladies and gents. I solved my flash problems by first identifying that it was in fact it was the flash player and not anything else (for a while I though it might be libcairo). Some symptoms that I was getting was youtube crashing regularly and pandora.com's player not advancing songs after they were done.  So I started to launch firefox from the command line (Applications->Accessories->Terminal). When the new window pops up, type in: firefox and hit return

I found that it still was crashing with a Segmentation fault (Core dumped). After that I start firefox with the -g option. The -g option will put it into debug mode, and I was looking a (gdb) prompt. This is the gnu debugger. I hit: r and return. For more information on gdb, type in: man gdb and hit return (to exit out of the man page, hit q and to advance hit the space bar). After hitting the r for run, I saw this in the terminal: "Starting program: /usr/lib/firefox/firefox-bin". I followed the instructions on the screen. After firefox came up, I went to youtube and it in fact did crash again. I went to the terminal window and saw this: 

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1221354928 (LWP 21768)]
0x00000000 in ?? ()
(gdb) where
#0  0x00000000 in ?? ()

#1  0xaef7991e in ?? () from /home/oberoc/.mozilla/plugins/libflashplayer.so
#2  0xaeb1d3f8 in ?? () from /home/oberoc/.mozilla/plugins/libflashplayer.so
#3  0xb7be61de in _gtk_marshal_BOOLEAN__BOXED () from /usr/lib/libgtk-x11-2.0.so.0
#4  0xb75e3772 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#5  0xb75f4323 in ?? () from /usr/lib/libgobject-2.0.so.0
#6  0x09027560 in ?? ()
#7  0xbf823d30 in ?? ()
#8  0x00000002 in ?? ()
#9  0xbf823e0c in ?? ()
#10 0xbf823d1c in ?? ()
#11 0xb75d321c in ?? () from /usr/lib/libglib-2.0.so.0
#12 0xbf823cd8 in ?? ()
#13 0xb75d321c in ?? () from /usr/lib/libglib-2.0.so.0
#14 0x09936798 in ?? ()
#15 0xbf823d14 in ?? ()
#16 0xbf823cb8 in ?? ()
#17 0xbf823d44 in ?? ()
#18 0x0901c598 in ?? ()
#19 0x00000000 in ?? ()

After see this in the terminal window, I hit q and return at the (gdb) prompt. You will get a warning about the program still running. I typed in Y to terminate the program. After that, I started up firefox again, type: about:plugins in the localation bar. It came back with two entries about Shockwave flash. I saw both were Shockwave Flash 9.0 r60. 

I decided to go grab the new version of flash. I then when to adobe's site, and I downloaded the tar.gz package (don't download the yum or the rpm package, they are for redhat).  I then went back to my terminal window, and changed the directory to my Desktop directory. I uncompressed and untarred the program by doing this: tar -zxf install_flash_player_9_linux.tar.gz. This will decompress and untar into a separate directory called  install_flash_player_9_linux . I changed the directory to install_flash_player_9_linux. You can use: ls to see what is in the directory. I used sudo ./flashplayer-installer. It will asked me to exit any browsers. I did. It prompted for the installation path of the Mozilla browser. If you have a default installation of firefox, it should be /usr/lib/firefox. ls /usr/lib/firefox to see if the directory is in fact there and there is files inside of that directory. I followed the directions after that to install the new flash.

I started firefox back up and when back to about:plugins and saw that it was Shockwave Flash 9.0r115. Cool Deal! Also I saw along instance of Shockwave Flash 9.0 r60. I went ahead and deleted that. It was in my /home/<username>/.mozilla/plugins/. I restarted firefox and everything was cool after that

---

