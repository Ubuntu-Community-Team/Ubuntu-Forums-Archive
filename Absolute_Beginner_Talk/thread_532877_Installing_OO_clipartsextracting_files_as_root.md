---
title: "Installing OO cliparts/extracting files as root"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by tobleron on 2007-08-23
I have downloaded the clipart gallery from openclipart.org and would like to install it now. As far as I know it should go into /usr/lib/openoffice/share/gallery. However, if I try to extract the tar.gz with Ark, it tells me I don't have write access to the folder (obviously). I'm sure there is a nice command line that let's me extract the files to the right place as root - only what is it...? 

I've thought about creative workarounds, such as extracting the files into a folder for which I do have write access, then starting konqueror as root and manually copying the files to the right place. But I quite like the idea of neat and handy command lines and would like to learn more about this.

---

### Post by Dr Small on 2007-08-23
Press ALT+F2 and type "gksudo nautilus".
This will log you in as Root in Nautilus.

Then press CTRL+L, which will allow you to type in the nautilus location bar, and then paste in your address, "/usr/lib/openoffice/share/gallery/".

Paste your archive there and then extract it ;)

Dr Small

---

