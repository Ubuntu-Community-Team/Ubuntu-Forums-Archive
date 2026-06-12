---
title: "Automatix down?"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by Seàn1 on 2006-11-01
I installed automatixbleeder along with automatix previously but after a reinstall of Ubuntu I tried to download Bleeder and automatix2. The latter works, but with ```
aptitude install automatixbleeder 
``` etc I am told the package cannot be found.

```
deb http://www.getautomatix.com/apt edgy main
``` is in sources.list because I am running a 32 bit edgy install.

The site has been busted for a while too.

First, I clicked the main page link and got:
[http://www.getautomatix.com/index.php?option=com_frontpage&Itemid=1](http://www.getautomatix.com/index.php?option=com_frontpage&Itemid=1)

Following with
[http://www.getautomatix.com/index.php?option=com_content&task=view&id=8&Itemid=26](http://www.getautomatix.com/index.php?option=com_content&task=view&id=8&Itemid=26)

and most importantly
[http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Release](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Release)
which is just some lame web spam page.

For grins I swapped edgy w/ dapper and got a file there
( [http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/Release](http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/Release) ) and found something so maybe I am just a big dumb newbie but this has been amazingly perplexing. BTW, why can I not just browse the directory? Every other deb source allows this because it makes troubleshooting bum links easy ( [http://www.getautomatix.com/apt/dists/dapper/](http://www.getautomatix.com/apt/dists/dapper/) ). That should be changed.

Edit: Now the first link (what should be the front page) is back up for the moment.

[SIZE="1"]automatix automatixbleeder automatix2 codecs win32 mp3 m4a ati xgl beryl compiz[/SIZE]

---

### Post by sbassett on 2006-11-01
I would take a look at this:

[Automatix Bleeder info]("http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_Automatix_Bleeder_.28only_on_Ubuntu_Dapper_i386_as_of_now.29")

It appears that bleeder is not currently available for edgy.

---

### Post by Seàn1 on 2006-11-01
> **sbassett said:**
> I would take a look at this:

[Automatix Bleeder info]("http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_Automatix_Bleeder_.28only_on_Ubuntu_Dapper_i386_as_of_now.29")

It appears that bleeder is not currently available for edgy.

*whistles*
Yeah, that would explain it then. Thanks for clearing that up and helping me out.

---

