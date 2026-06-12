---
title: "madwifi performances issue"
date: 2008-05-22
forum: Apple Hardware Users
---

### Post by Romu on 2008-05-22
Hi all,
As the madwifi 0.94 doesn't work with my macbook pro 2G, I'm using the current snapshot (I upgraded to the May 22, but the problem remains). Wifi works pretty fine except the performances are only 10% of what they were with Gutsy and the madwifi at the Gutsy date.

Could you please confirm? And do someone have a solution?

Thanks in advance.

---

### Post by cyberdork33 on 2008-05-22
> **Romu said:**
> Hi all,
As the madwifi 0.94 doesn't work with my macbook pro 2G, I'm using the current snapshot (I upgraded to the May 22, but the problem remains). Wifi works pretty fine except the performances are only 10% of what they were with Gutsy and the madwifi at the Gutsy date.

Could you please confirm? And do someone have a solution?

Thanks in advance.
use an older revision of the madwifi driver... I think the ng versions are he only ones that will work:
[http://snapshots.madwifi.org/madwifi-trunk/](http://snapshots.madwifi.org/madwifi-trunk/)

---

### Post by Romu on 2008-05-22
Whaou, many thanks !! This works !!

It seems that the most recent the madwifi package is the worst the performances are, as I tested the r3556 (April 2008) and r3111 (January 2008) and this last much better than the other.

I finally recovered my bandwidth, thanks to cyberdork33, thanks to you.

---

