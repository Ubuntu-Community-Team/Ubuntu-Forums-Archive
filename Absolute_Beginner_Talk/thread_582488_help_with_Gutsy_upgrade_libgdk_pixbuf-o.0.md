---
title: "help with Gutsy upgrade libgdk_pixbuf-o.0"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by DalaiDakkar on 2007-10-19
hello, after running apt-get upgrade on feisty to upgrade to gutsy
all the packages where downloaded and then after several minutes of normal upgrade process i've got the following error:

[B]setting up gnome-themes (2.20.0-0ubuntu1)
gtk-update-icon-cache: error while loading shared libraries: libgdk_pixbuf-o.0: cannot open shared object file: No such file or directory
dpkg: error processing gnome-themes (--configure):
subprocess post-installation script returned error exit status 127
error where encountered while processing:
gnome-themes
Sub-process /usr/bin/dpkg returned an error code (1)
dakkarNautilus2$
[/B]
hope anyone can help me please :(

(here's a screenshot of the error: [http://dakkar.tk/terror.jpg](http://dakkar.tk/terror.jpg)) to see the image copy and paste the url to your browser addres bar (otherwise sends error)
thank you very much

---

### Post by octotom on 2007-10-19
If you're still able on another machine, maybe you could try and download Gutsy and do a fresh install.  Other than that, I couldn't say much.  Perhaps someone else here will know more though.

Tom

---

### Post by DalaiDakkar on 2007-10-19
I will love to do that but I have months with feisty and everything it's like set up already :S i'm trying to save this installation as much as possible, hope anyone else can give me advice to save me from a fresh install.

Thank you for your answer


--------------UPDATE-------------------
My problem was fixed with this steps

No, don't delete /usr/lib/libgdk_pixbuf-2.0.so.0... You definetely need that! You can get it back by doing apt-get --reinstall install libgtk2.0-0.

Then run: ldd /usr/lib/libgdk_pixbuf-2.0.so.0 and it will list all libraries that it's trying to load. Look for /usr/local/lib/<<Some file>> the local part is key as this is where most make install's put libraries. Any file in /usr/local/lib is in your way and I suggest moving it somewhere else not deleting it.

Thanks to jalbrant for the help
-------------------------------------------

---

