---
title: "Firefox Flas Player shutdown"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by ldiegoa on 2006-11-24
Hi , im new here , im trying to see sites like youtube, i have the plugin of flash macromedia installed but when the youtube (or any other with flash content ) starts, the firefox shutdown and i have to restart it, and no, i cant see flash not enter youtube site.... can anyone help me here? im using firefox 2.0 with ubuntu 6.10 , thanks:confused:

---

### Post by AndyCooll on 2006-11-24
This is a known defect.

If you do a search for "Firefox 2 Edgy Flash" you'll find that different folk have found different solutions for fixing this.

I fixed by typing into the command line the following:
```
sudo gedit /etc/X11/xorg.conf
```

I then scrolled through that file and found the line that mentions ColourDepth. I changed that setting to 24, and saved the file. Reboot the system and FF now works fine.

Having said all that Edgy has Flash 7 installed, but some sites require Flash 9.

:cool:

---

### Post by x64Jimbo on 2006-11-24
Flash 9 beta is available right now, btw. It is leaps and bounds better than 7 IMO.

---

### Post by caver1 on 2006-11-24
> **x64Jimbo said:**
> Flash 9 beta is available right now, btw. It is leaps and bounds better than 7 IMO.

Okay where did you get Flash 9? I need it for a couple of sites. All I can find is 7.;)

---

### Post by Kobalt on 2006-11-24
Here is where you'll get the instructions on how to install flash 9 : 
[http://ubuntuforums.org/showthread.php?t=280252](http://ubuntuforums.org/showthread.php?t=280252)

Cheerio !

---

### Post by caver1 on 2006-11-24
> **Kobalt said:**
> Here is where you'll get the instructions on how to install flash 9 : 
[http://ubuntuforums.org/showthread.php?t=280252](http://ubuntuforums.org/showthread.php?t=280252)

Cheerio !

I went to adobe's site and all I could find was 7. 
Thank you am now using it.:)

---

### Post by Dual Cortex on 2006-11-24
Do this, just a matter of copying and pasting ;) :


> 

```
sudo rm /usr/lib/firefox/plugins/libflashplayer.so /usr/lib/firefox/plugins/flashplayer.xpt
```

If it tells you that a file doesn't exist, don't worry about it. Flash 7 had flashplayer.xpt but flash 9 beta 1 didn't, so depending on which version you had installed, you may get an error that flashplayer.xpt doesn't exist. Or if you don't have any of them installed, they both won't exist. Either way, just carry on.

Second get the tar.gz file

```
wget [http://www.adobe.com/go/fp9_update_b2_installer_linuxplugin](http://www.adobe.com/go/fp9_update_b2_installer_linuxplugin)
```

Third extract the tar.gz

```
tar xf FP9_plugin_beta_112006.tar.gz
```

Fourth change into the new directory

```

cd flash-player-plugin-9.0.21.78/
```

Finally move over the plugin to the plugins directory.

```

sudo mv libflashplayer.so /usr/lib/firefox/plugins/
```

That should be it. If you want to remove all the excess garbage that you downloaded, just change back into the home directory and remove it.

```

cd rm -rf FP9_plugin_beta_112006.tar.gz flash-player-plugin-9.0.21.78/
```



Stripped from the instructions here:
[http://ubuntuforums.org/showthread.php?t=279990&highlight=howto+flash](http://ubuntuforums.org/showthread.php?t=279990&highlight=howto+flash)

---

