---
title: "rhythmbox ipod plugin problem"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by kno712 on 2006-12-03
I have updated Rhythmbox through a deb file that I found in "Ubuntu click and run" [http://www.getdeb.net/]("http://www.getdeb.net/"). But when I run it, I get the following message: "Unable to activate plugin ipod support"

In the console, I get this:

(rhythmbox:7506): Rhythmbox-WARNING **: Unable to start mDNS browsing: MDNS service is not running

(rhythmbox:7506): Rhythmbox-WARNING **: /usr/lib/rhythmbox/plugins/ipod/libipod.so: undefined symbol: itdb_get_itunesdb_path

(rhythmbox:7506): Rhythmbox-WARNING **: Could not load plugin ipod


(rhythmbox:7506): Rhythmbox-WARNING **: Error, impossible to activate plugin 'iPod support'

(rhythmbox:7506): Rhythmbox-WARNING **: Unable to stop mDNS browsing: MDNS service is not running

Please, help!

---

### Post by kno712 on 2006-12-04
hello!? Anybody can help me?

---

### Post by doclivingston on 2006-12-06
> **kno712 said:**
> /usr/lib/rhythmbox/plugins/ipod/libipod.so: undefined symbol: itdb_get_itunesdb_path

Have you install either rhythmbox or libgpod from any third-party repositories? That error indicates that your version of libgpod is different from the one Rhythmbox was compiled against, and they are incompatible.

---

### Post by kno712 on 2006-12-06
Hello, thanks for replying.

No, I got it from "Ubuntu click and run" at [http://www.getdeb.net/](http://www.getdeb.net/) as a deb file; the dependencies were solved automatically.

How can I update that lib? How can I know what version has been installed and what version do I need?

thanks a lot

---

### Post by kno712 on 2006-12-08
hello? please any help!

---

### Post by riven0 on 2006-12-08
> **kno712 said:**
> hello? please any help!

kno712, I don't use rhythmbox, so I can't help there. But why don't you try gtkpod? That's what I use and it works perfect. Fast and snappy.

---

### Post by kno712 on 2006-12-08
the problem is not the ipod itself; I just want to get rid of that message;

---

### Post by doclivingston on 2006-12-08
I can't find the rhythmbox package on getdeb.net, so I can't check, but either 1) it's build for a different version of Ubuntu than you are using, 2) there is a newer package of libgpod that you calso need, or 3) it's is a broken package

---

### Post by pyropingvin on 2006-12-08
Alt+F2
gconf-editor

apps/rhythmbox/plugins/ipod


active=value 0

---

### Post by kno712 on 2006-12-09
pyropingvin, thanks a lot; that solved the problem; the ubuntu community is really helpfull;

for those who want to try the new version of rhythmbox, it can be found here [http://www.getdeb.net/search.php?release=Dapper&keywords=rhythmbox](http://www.getdeb.net/search.php?release=Dapper&keywords=rhythmbox)

---

### Post by quarkhirad on 2006-12-09
> **riven0 said:**
> kno712, I don't use rhythmbox, so I can't help there. But why don't you try gtkpod? That's what I use and it works perfect. Fast and snappy.

Yeah or u could try yamipod. 
ITs pretty neat 

u can download it from [www.yamipod.com](www.yamipod.com)

---

### Post by dakevman on 2007-09-01
ok, to deactivate the plugin, is not really a solution. 
actually getdeb installs an own verstion of libgpod. 

so all u have to do is, go into the directoy /usr/lib

and  sudo cp libgpod.so.2 libgpod.so.1

so solves the problem. the plugin just cant find the new files, but if u make a copy of the new files with their old names, the it works again cuz the plugin can find the file agian.. 

sry about my englsih.. 

cheers, 

kevin

---

