---
title: "Macromedia Flash"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-03-31
My web browser is Opera and I'm continually asked to install Macromedia Flash when viewing certain websites. How do I do this so it works with Opera please?

---

### Post by TonKi on 2007-03-31
In Dapper it is in the backports repository and here is a howto
[https://help.ubuntu.com/community/RestrictedFormats/Flash]("https://help.ubuntu.com/community/RestrictedFormats/Flash")

--
Enable multiverse and universe in your sources.list and then run
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by a.v.l on 2007-03-31
> **TonKi said:**
> In Dapper it is in the backports repository and here is a howto
[https://help.ubuntu.com/community/RestrictedFormats/Flash]("https://help.ubuntu.com/community/RestrictedFormats/Flash")

--
Enable multiverse and universe in your sources.list and then run
```
sudo apt-get install flashplugin-nonfree
```

Thanks for your help, I followed your instructions and ran the above and it worked fine with Firefox, but not with Opera. Could there be a different version for Opera?

---

### Post by TonKi on 2007-03-31
Obor's way just more complicated was here

or 

You can also add Mozillas plug-in path to Opera:
'Tools > Preferences > Advanced > Content > Plug-in options... > Change path...'

Its something like /usr/lib/firefox/plugins or /usr/lib/mozilla/plugins to add

---

### Post by Obor on 2007-03-31
I don't use opera myself but following[ this guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_in_Opera") it seems you have to copy the flash plugin into opera plugins folder

My plugin is installed in /usr/lib/firefox/plugins if yours is the same the following should work
```

sudo cp /usr/lib/firefox/plugins/libflashplayer.so /usr/lib/opera/plugins
sudo cp /usr/lib/firefox/plugins/flashplayer.xpt /usr/lib/opera/plugins
```

---

### Post by a.v.l on 2007-03-31
When I try to copy libflashplayer.so to /usr/lib/opera/plugins/  I get an error message:

"Error while copying to /user/lib/opera/plugins. you do not have permission to write to this folder"


Quote:
Ok, go to the adobe site an download the flashpackage in tgz format.
Extract it and copy the "libflashplayer.so" to '/usr/lib/opera/plugins/'

---

### Post by a.v.l on 2007-03-31
> **TonKi said:**
> Obor's way just more complicated was here

or 

You can also add Mozillas plug-in path to Opera:
'Tools > Preferences > Advanced > Content > Plug-in options... > Change path...'

Its something like /usr/lib/firefox/plugins or /usr/lib/mozilla/plugins to add

When I did as you suggested above I had two entries appear which were both ticked.  

The first:

usr/lib/opera/plugins

The second:

usr/lib/mozilla/plugins

Unticking the mozilla entry made no difference so I reticked it and then rebooted the PC and it worked.  Thanks to you both for helping out.

---

