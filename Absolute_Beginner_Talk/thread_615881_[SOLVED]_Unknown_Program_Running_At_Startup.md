---
title: "[SOLVED] Unknown Program Running At Startup"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by keith1 on 2007-11-17
When I started my computer a couple of days ago, everything was loading slowly and I noticed the tower light was staying on. So I went to - process table - KDE system guard. I looked for what was running and found - Scrollkeeper - updater. There was another Scrollkeeper item, but I didn't catch what it was.

So... I just let it "run it's course". When I came back later and went back in to see what those items were they were gone. I Googled about it, but didn't understand what it is.

So.... What took place, and if it occurs again, should I take some action or is it a normal process?

Thanks,   Keith

---

### Post by taurus on 2007-11-17
```

SCROLLKEEPER(7)                                                SCROLLKEEPER(7)

NAME
       ScrollKeeper - An open document cataloging and metadata management sys&#8208;
       tem.

DESCRIPTION
       ScrollKeeper is a system for managing document metadata.   Its  primary
       function  is  to  act as a card catalog for documents, keeping track of
       what documents are available, where they  can  be  found,  and  various
       attributes  of  the  documents such as their language, format, subject,
       version, and position in a contents list.  It also manages other  meta&#8208;
       data such as document indices.

       ScrollKeeper  acts  as  a  middle  layer  between applications and help
       browsers.  When applications install documentation,  the  documentation
       is  registered  with ScrollKeeper.  Any ScrollKeeper-aware help browser
       on the system can then access this information.  In this  way,  Scroll&#8208;
       Keeper is a compatibility layer which allows any help browser to inter&#8208;
       face to all the documentation on a system, provided the  package  which
       ships  the  documentation  registers  it  with  ScrollKeeper.   It also
       removes much of the burden from application packagers and help  browser
       developers  by  providing  a standard set of tools and by doing much of
       the work inside of ScrollKeeper.

RESOURCES
       The ScrollKeeper web pages can be found at  http://scrollkeeper.source&#8208;
       forge.net  and  the  mailing  list can be found at http://lists.source&#8208;
       forge.net/lists/listinfo/scrollkeeper-devel.

AVAILABILITY
       ScrollKeeper is licensed under the GNU Lesser Public License (LGPL).  A
       copy  of  this  license  can  be  read in the file COPYING shipped with
       ScrollKeeper.

       The latest version of  ScrollKeeper  can  be  found  at  http://source&#8208;
       forge.net/projects/scrollkeeper.

FILES
       /etc/scrollkeeper.conf
       /var/log/scrollkeeper.log
       /var/lib/scrollkeeper/*

AUTHOR
       Laszlo Kovacs   <laszlo.kovacs@sun.com>
       Dan Mueth       <d-mueth@uchicago.edu>
SEE ALSO
       scrollkeeper-config(1),      scrollkeeper-gen-seriesid(1),      scroll&#8208;
       keeper.conf(5),  scrollkeeper-preinstall(8),  scrollkeeper-rebuilddb(8)
       scrollkeeper-update(8)

scrollkeeper                      Dec 5, 2001                  SCROLLKEEPER(7)

```

---

### Post by keith1 on 2007-11-17
Thats what I needed to know, thank you,

Keith

---

