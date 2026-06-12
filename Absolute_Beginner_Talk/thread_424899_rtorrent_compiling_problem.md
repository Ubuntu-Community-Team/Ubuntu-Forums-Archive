---
title: "rtorrent compiling problem"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by jdimas on 2007-04-27
Hi!
I'm having problem with rtorrent compilation since I upgraded to Feisty.
all the deps are installed, the configuration runs ok, but at the installation of the deb package, it says me:

```
Copying files to the temporary directory... FAILED!

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package... FAILED!

*** Failed to install the package

Do you want to see the log file?  [y]: 

Erasing temporary files...OK

```

here is the log file:
```
(Reading database ... 113731 files and directories currently installed.)
Unpacking rtorrent (from .../rtorrent_0.7.4-1_i386.deb) ...
dpkg: error processing /home/jdimas/Sources/rtorrent-0.7.4/rtorrent_0.7.4-1_i386
.deb (--install):
 trying to overwrite `/usr/bin/ld', which is also in package binutils
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/jdimas/Sources/rtorrent-0.7.4/rtorrent_0.7.4-1_i386.deb

```

any ideas?
thank you

---

### Post by ttakun on 2007-04-27
Sorry man, I don't know what your problem is, since I'm a noob. I guess the reason should be on the line saying 
>  trying to overwrite `/usr/bin/ld', which is also in package binutils.
But why don't you just install rtorrent from its web page. There it goes a great and helpful HOWTO. 
[HOWTO install the latest rtorrent]("http://ubuntuforums.org/showthread.php?t=371275")

Just change the following:
When it says **[COLOR="Blue"]libtorrent 0.11.1[/COLOR]** write [COLOR="Blue"]**libtorrent 0.11.4**[/COLOR] and when it says **[COLOR="Blue"]rtorrent 0.7.1[/COLOR]** just write [COLOR="Blue"]**rtorrent 0.7.4**[/COLOR]. That worked wonderfully for me. Hope it helps.

---

### Post by jdimas on 2007-04-27
I'm installing it downloading the tarballs from the official website, configuring and using checkinstall...
I tried your sugestion with the same result...
it worked ok in edgy, but now it doesn't.
and rtorrent is the best bittorrent client, in my opinion...

:(

---

### Post by chalex on 2007-04-27
Why can't you just install it from the repositories like everything else? "sudo apt-get install rtorrent"

---

### Post by jdimas on 2007-04-27
because the repositories version is from the time of the dinossaurs.

and, miraculously, it installed perfectly after an upgrade of some packages... no explanation found...

thanks for everyone

---

### Post by zarathustra on 2007-04-29
I seem to keep getting this problem for various programs when I want to install via checkinstall on feisty.

---

