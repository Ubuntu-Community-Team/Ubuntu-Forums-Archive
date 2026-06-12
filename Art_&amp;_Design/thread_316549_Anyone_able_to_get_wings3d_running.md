---
title: "Anyone able to get wings3d running?"
date: 2006-12-10
forum: Art &amp; Design
---

### Post by Peepsalot on 2006-12-10
I get a segfault when trying to start it on Edgy.  It appears this is a [common problem](https://bugs.launchpad.net/distros/ubuntu/+source/erlang/+bug/62145).

Has anyone gotten around this problem?

---

### Post by chek2fire on 2006-12-18
i have the same problem :( .anyone to help us?

---

### Post by pveith on 2006-12-18
Hi,

i found a solution in ubuntu launchpad. There is a bug posted in launchpad and a solution to get wings running posted by Jonathan Sieber.

Just install the libsdl-erlang package from debian found at: [http://packages.debian.org/unstable/libs/libsdl-erlang](http://packages.debian.org/unstable/libs/libsdl-erlang). And don't forget to select the right architecture. (download and "sudo dpkg -i <filename>")
This somewhat "dirty" solution solved the wings3d bug for me. Hopefully the debian package gets "overriden" as soon as the ubuntuteam fixes the bug.

---

### Post by Peepsalot on 2006-12-18
nice, such a simple fix.

---

### Post by salviablue on 2008-03-01
I tried that and I just get the same message!? Any clues?

---

### Post by salviablue on 2008-03-01
Perfect fix found (I think). Download the latest dev release.
wings3d-0.99.01
[http://www.wings3d.com](http://www.wings3d.com)

It sdevelopment release but I have had no problems with it whatsoever (so far, touch wood).

gutsy ati radeon express 200M (advent 7201 laptop)
:guitar:

---

