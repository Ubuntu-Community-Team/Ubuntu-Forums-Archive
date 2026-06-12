---
title: "Ubuntu 6.06 LTS &amp; Pidgin"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-10-23
Hi.... I have an old laptop which is using Ubuntu 6.06 LTS
I have searched the Repositories and Went over to GetDeb.net
But there apears to be no Pidgin for Ubuntu 6.06 LTS.
I see there is on for 7.04 but not 6.06.  Has anyone found
Pidgin for 6.06 LTS.

Thanks

---

### Post by notwen on 2007-10-23
Not sure who created this deb, but I googled and came up w/ [this]("http://www.mediafire.com/?9dzxhl0z1mj").  Hope it helps. =]

---EDIT---
Some ppl have posted replies to this [blog how-to]("http://jhcore.com/2007/06/04/install-pidgin-in-ubuntu/") saying they successfully installed/upgraded Pidgin on Dapper.

---

### Post by jdfreshwater on 2007-10-23
Pidgin has probably not been built for that version.  You can always download the source, extract it to a folder.  After that you need to run the following commands.

In the extracted folder run.

./configure
make
sudo make install

This will configure and install pidgin for you.  It is not as hard as it seems.  I was doing it for a while in 7.04 because I was not seeing it initially in the repositories.

---

