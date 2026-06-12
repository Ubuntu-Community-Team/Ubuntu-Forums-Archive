---
title: "Install Firefox Extension From Terminal"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by nhandler on 2007-04-11
Is there any way to install a firefox extension from the terminal? I'm trying to make a small script that will install all my firefox extensions for me. If there is no "firefox --install-plugin=xxx" command (or something similar), then is there a different way? Thanks.

P.S. I know how to install extensions normally. I just need to find a way to do it from a script.

---

### Post by userundefine on 2007-04-12
It seems you can do it, but I'm not sure if you can on Linux.

[http://www.mozilla.org/projects/firefox/extensions/commandlineoptions.html](http://www.mozilla.org/projects/firefox/extensions/commandlineoptions.html)

I tried but it didn't work for me with the -install-global-extension option.

---

### Post by nhandler on 2007-04-12
The command didn't crash with an error, but it didn't install the extension either. What actually happens when an extension is installed? Since the extension is only a renamed zip file, it is probably extracted somewhere. A config file is also probably updated. Does anyone know if it would be possible to try and install an extension using a bash script from this approach. Could anyone clear up the process?

---

### Post by Tprnyc on 2008-06-19
In fedora I su to become root then followed these steps

wget [https://addons.mozilla.org/en-US/firefox/downloads/file/xxx.xpi](https://addons.mozilla.org/en-US/firefox/downloads/file/xxx.xpi)
firefox -install-global-extension xxx.xpi
rm -f xxx.xpi

next time I launched firefox there it was.

---

