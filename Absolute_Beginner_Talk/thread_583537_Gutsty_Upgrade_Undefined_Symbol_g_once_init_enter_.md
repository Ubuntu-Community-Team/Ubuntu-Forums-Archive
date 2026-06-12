---
title: "Gutsty Upgrade: Undefined Symbol g_once_init_enter_impl"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by DalaiDakkar on 2007-10-20
Hello I upgrade to gutsy with apt-get upgrade
after all packages were downloaded in several hours and the installation ran for a while with no problems it came up with this:

[COLOR="DimGray"]setting up gnome-themes (2.20.0-0ubuntu1)...
gtk-update-icon-cache: symbol lookup error: /usr/lib/libgdk_pixbuf-2.0.so.0: undefined symbol: g_once_init_enter_impl
dpkg: error processing gnome-themes (--configure):
subprocess post-installation script returned error exit status 127
error were encountered while processing:
gnome-themes
E: Sub process /usr/bin/dpkg returned an error code (1)
dakkar$
[/COLOR]

I found this thread but it's now closed:
[http://ubuntuforums.org/showthread.php?p=3555579](http://ubuntuforums.org/showthread.php?p=3555579)

I dont undesrstand what jalbrant proposes to do exactly, could anyone help me please?

Thank you very much

--------------UPDATE-------------------
My problem was fixed with this steps

No, don't delete /usr/lib/libgdk_pixbuf-2.0.so.0... You definetely need that! You can get it back by doing apt-get --reinstall install libgtk2.0-0.

Then run: ldd /usr/lib/libgdk_pixbuf-2.0.so.0 and it will list all libraries that it's trying to load. Look for /usr/local/lib/<<Some file>> the local part is key as this is where most make install's put libraries. Any file in /usr/local/lib is in your way and I suggest moving it somewhere else not deleting it.

Thanks to jalbrant for the help
-------------------------------------------

---

### Post by perroil on 2007-10-25
thank you so much i had the same problem you save my life \\:D/

---

### Post by DalaiDakkar on 2007-10-25
I'm glad to know I helped someone else, although I got gutsy already running (and how it runs with compiz!!!!!) I've noticed that everytime I install something through synaptic package manager  this conflicting files we just moved from /usr/local/lib get created again and then after the install I can't open firefox nor many programs so I had to get them out of the way again.

I have not yet searched how can I solve this but I tell you in advance in case you notice your computer unresponsive after synaptic manager or updates.

Cheers!

-dD

---

### Post by Ej@Y on 2007-11-29
The post here did solve my problem, but after an upgrade from Synaptics Package Manager the error returned again. I knew the problem arrived when I compiled and installed glib2.9.6. 

So i just deinstalled (make uninstall) glib2.9.6 and everything was okay again (even after adding a new package). Maybe this will be helpfull for you, DalaiDakkar!

---

### Post by DalaiDakkar on 2007-11-29
Thanks for your answer Ej@y, but I don't know exactly how to do that, I couldn't remember if I installed libglib manually and where is the folder where I can apply the make uninstall command :( my only solution for now is moving these files from the previous post every time I install something through synaptic, I'll appreciate if you know a way to fix this and tell me about it.

Thank you very much.

---

