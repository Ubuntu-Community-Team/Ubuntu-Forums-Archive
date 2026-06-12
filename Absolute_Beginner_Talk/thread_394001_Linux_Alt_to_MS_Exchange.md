---
title: "Linux Alt to MS Exchange"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by kingjimbob on 2007-03-26
Is there a linux based (free) alternative to MS exchange....

I want to be able to set up internal email for a local group. no external mail is required.


Any feedback would be much appericated

---

### Post by thelinuxguy on 2007-03-26
> **kingjimbob said:**
> Is there a linux based (free) alternative to MS exchange....
I want to be able to set up internal email for a local group. no external mail is required.
Any feedback would be much appericated

Zimbra has an Open Source edition. 
[http://www.zimbra.com/community/downloads.html](http://www.zimbra.com/community/downloads.html)

---

### Post by jhenager on 2007-03-26
[http://www.open-mag.com/1823548701.shtml](http://www.open-mag.com/1823548701.shtml)

This article lists a couple of alternatives.

---

### Post by kingjimbob on 2007-03-26
Thanks for the feedback!

It is appericated but I did across both examples myself, problem i am finding is that a majority of the time the examples are trails.

What i am trying to attempt todo (for a uni project) is build a network for a workgroup which users a Linux box for its File sharing, internal email, print server etc. all based on free open-source products.

I am not having much luck so far.

---

### Post by superjet on 2007-03-26
Have you seen Citadel?

 [http://www.citadel.org/doku.php](http://www.citadel.org/doku.php)

---

### Post by kingjimbob on 2007-03-26
Thanks Superjet!

That looks like exactly what i need!!! I have literally spent hours in front of google and Linux websites searching for such a thing.

I will keep you all updated!

---

### Post by thelinuxguy on 2007-03-26
> **kingjimbob said:**
> Thanks Superjet!
That looks like exactly what i need!!! I have literally spent hours in front of google and Linux websites searching for such a thing.
I will keep you all updated!

I tried out Citadel using the pre-built packages from: [http://www.citadel.org/doku.php/installation:debian](http://www.citadel.org/doku.php/installation:debian). 
But the installation of the web-interface (citadel-webcit) threw an error dialog with the message:
```

E: citadel-webcit: subprocess post-installation script returned error exit status 127

```

The terminal screen behind shows errors which are in the attached thumbnail.

The command line interface is working. But I would like to try out the web interface. Is it working at your end?

---

### Post by Balle-Larsen on 2007-04-15
I tried to install citadel-webcit with the same result as above.

/var/lib/dpkg/info/citadel-webcit.config: 80: source: not found
dpkg: error processing citadel-webcit (--configure):
 subprocess post-installation script returned error exit status 127

I decided to change the shell used in /var/lib/dpkg/info/citadel-webcit.config from /bin/sh to /bin/bash
After that I got citadel to run in my Firefox browser with http:/localhost:8504/

source is apparently not build into "our" version of sh

---

### Post by thelinuxguy on 2007-04-15
> **Balle-Larsen said:**
> I decided to change the shell used in /var/lib/dpkg/info/citadel-webcit.config from /bin/sh to /bin/bash
After that I got citadel to run in my Firefox browser with http:/localhost:8504/
source is apparently not build into "our" version of sh

That did it!!! Can run the web interface now.
Thank you.

---

