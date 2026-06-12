---
title: "Mind Mapping Software"
date: 2005-07-12
forum: Absolute Beginner Talk
---

### Post by SYD2005 on 2005-07-12
Hi guys,

I am looking high and low for something similar to [MindManager](http://http://www.mindjet.com/us/products/) (mind mapping software) which can be used in Ubuntu. I have pretty much converted all the way to Ubuntu from the dark side but if I can just find something which produces something simliar to Mindmanager the the transfer is complete...

Any suggestions?

Cheers

---

### Post by Poldi on 2005-07-12
hi.

while I cannot help you much yet, I have recently started working on an open-source mindmapper privately. don't get too excited, though - implementation has not yet begun and the project plan projects a first releasable prototype around christmas.

still, if you can give me any information on what you look for in a mindmapping software you could give me a hit or two. any input no matter how (un-)formalized will be of value to me. complete RUP requirement specification documents will help, too.

if you finish your evaluation of todays market, please let me know what you think about the available tools.

thanks and kind regards,
Carsten

---

### Post by Knome_fan on 2005-07-12
Kdissert is great:
[http://freehackers.org/~tnagy/kdissert/](http://freehackers.org/~tnagy/kdissert/)

And as far as I know it's even in backports.
Ubuntuguide on how to add extra repositories including backports:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

There is also freemind, but as I haven't used it in a long time a can't really comment on it:
[http://freemind.sourceforge.net/wiki/index.php/Main_Page](http://freemind.sourceforge.net/wiki/index.php/Main_Page)

Have fun!

---

### Post by SYD2005 on 2005-07-12
hi guys and thanks very much for your replies. 

Knome_fan thanks for the links - in between searching here for a little while and stuff I managed to find Freemind which I have downloaded to have a look. I will also install Kdissert as well and give it a wurl...what do you like about Kdissert?

Carsten thanks for reply also...wow cool that you are taking up this project...would like info posted back this thread, or elsewhere?

Cheers

---

### Post by Knome_fan on 2005-07-12
What I like about Kdissert?

Hm, I think that it's a great mix. On the one hand it's very easy to use as a simple mindmapping tool, on the other it is very powerful at doing advanced stuff with your mindmaps. For exmple it generates an orderd tree view and you can export your maps to html or even use it to make impress presentations. Very cool, imho.

---

### Post by Error_Msg on 2005-07-12
[http://freemind.sourceforge.net/wiki/index.php/Main_Page](http://freemind.sourceforge.net/wiki/index.php/Main_Page)

E_M

---

### Post by SYD2005 on 2005-07-12
thanks for your replies guys...its going to to fun trying out these applications...

---

### Post by maruchan on 2005-07-12
If you try out freemind, make sure you go to their forum and grab the latest .8 RC 5 - it's incredible! It even opens MindManager maps, I think.

---

### Post by SYD2005 on 2005-07-12
hey cool, thanks maruchan!  :-)

---

### Post by sophtpaw on 2005-07-13
[QUOTE=Knome_fan]Kdissert is great:
[http://freehackers.org/~tnagy/kdissert/](http://freehackers.org/~tnagy/kdissert/)

And as far as I know it's even in backports.
Ubuntuguide on how to add extra repositories including backports:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

There is also freemind, but as I haven't used it in a long time a can't really comment on it:
[http://freemind.sourceforge.net/wiki/index.php/Main_Page](http://freemind.sourceforge.net/wiki/index.php/Main_Page)

Have fun![/QUOTE]


Hi, 

Just wanted to let you know that i couldn't in fact find kdissert in Synaptic having fully updated my repositories, including backports
Could you share how else i might find this package?

cheers,

sophtpaw

---

### Post by Knome_fan on 2005-07-13
Ups, you'r right, it's not in backports proper but still in staging.

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports-staging main universe multiverse restricted

This is the line I have in my sources.list for staging. Keep in mind that it's untested software, so you probably don't want to keep this line uncommented all the time (unless you like bleeding edge that is).

Or simply download the package yourself:
[ftp://ftp2.caliu.info/backports/dists/hoary-backports-staging/universe/binary-i386/kdissert_0.9.0-1build1~5.04ubp1_i386.deb](ftp://ftp2.caliu.info/backports/dists/hoary-backports-staging/universe/binary-i386/kdissert_0.9.0-1build1~5.04ubp1_i386.deb)

Have fun!  :grin:

---

