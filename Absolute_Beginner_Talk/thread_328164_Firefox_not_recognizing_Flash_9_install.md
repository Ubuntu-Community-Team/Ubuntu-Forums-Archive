---
title: "Firefox not recognizing Flash 9 install"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by mormonchess on 2006-12-30
I downloaded Flash 9 Beta using these instructions:

[http://www.psychocats.net/ubuntu/flash]("http://www.psychocats.net/ubuntu/flash")


My Firefox 2.0 isn't recognizing that I installed it.  Youtube is telling me that I don't have Flash.  How do I convince my Firefox that I really did install it?

I'm using Dapper Drake.

---

### Post by deadgobby on 2006-12-30
It should be there. MMM I did not use Cats Howto. I use this thread
[http://www.ubuntuforums.org/showthread.php?t=279990](http://www.ubuntuforums.org/showthread.php?t=279990)
 There is some slight differences on installing it. After looking at apple to apples there is a difference. For example.
Link=wget  [http://www.adobe.com/go/fp9_update_b2_installer_linuxplugin](http://www.adobe.com/go/fp9_update_b2_installer_linuxplugin)
Cat=
wget -c [http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz](http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz)

Link= tar xf FP9_plugin_beta_112006.tar.gz
Cat= tar -xvzf FP9_plugin_beta_112006.tar.gz

 The above is a sample if some small differences on the how to.

 I did not have a problem when doing the forum link. Of course I am running Eft. 
GObby

---

### Post by DavidW2 on 2006-12-30
I have Edgy Eft running now but I thought just before I upgrade that the non-free flash plug version 9 was available in the repos for Dapper.  In any case it is available for Edgy.  

I did have the same problem with the Beta 9 flash plugin that you described, albeit with Firefox 1.5.  My workaround was to copy the two files (flashplayer.xpt and libflashplayer.so to ~/.mozilla/plugins.  That seem to fix the issue.  If no one else is logging into your system then this fix will work fine.

---

### Post by tenjin1 on 2006-12-30
To confim which Flash version is installed, type about:plugins in address bar in Firefox. I had to copy the libflashplayer.so extracted from the Flash6 tarball into /usr/lib/firefox/plugins. I also copied into /usr/lib/mozilla-firefox/plugins/ just for good measure.

---

### Post by tenjin1 on 2006-12-30
> To confim which Flash version is installed, type about:plugins in address bar in Firefox.

btw, that is --> about : plugins (minus the spaces)
(it made smiley when I typed it):D

---

