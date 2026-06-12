---
title: "Amd64 vs i686 Pentium D"
date: 2013-07-01
forum: Any Other OS
---

### Post by mamamia88 on 2013-07-01
I ordered a cheap computer on ebay and it comes with 3.0 ghz dual core 3.0ghz pentium d and 2gb ram.  I plan on hooking it up to tv for basic stuff and will probably go with debian 7 or arch on it.  Probably debian since I don't need. latest and greatest 	and I'm lazy.  Should I go with a 64 bit image just in case?

---

### Post by mips on 2013-07-01
I don't see why not.

---

### Post by mamamia88 on 2013-07-01
Care ti clarify? I could probably upgrade to 4gb ram pretty cheap on this machine then again I'm gonna use xfce version of debian so probably wont need it.  Will performance be same either way?  Will I break compatability with simple stuff like vlc or anything?  Basically all I really want to run is vlc and chrome. maybe a light bt client.

---

### Post by sanderj on 2013-07-01
> **mamamia88 said:**
> Should I go with a 64 bit image just in case?

in case of what?

---

### Post by mamamia88 on 2013-07-01
> **sanderj said:**
> in case of what?
I up the ram to 4gb

---

### Post by oldos2er on 2013-07-01
I would go with 64-bit. If you run CPU-intensive tasks you will notice a speed difference; for daily tasks not so much.

---

### Post by MadmanRB on 2013-07-02
I dunno, because its an older processor you may want to go 32bit.
It wont be beneficial to go 64bit if the max ram is 4GB

---

### Post by sanderj on 2013-07-02
> **mamamia88 said:**
> I up the ram to 4gb

32-bit Ubuntu can handle RAM well above 4GB, thanks to PAE.

Anyway: 
1) you can choose both 32-bit and 64-bit
2) it doesn't matter much for the (practical) amount of RAM you can address
3) I would choose 64-bit ... because you can

---

### Post by lykwydchykyn on 2013-07-02
As long as you run the PAE kernel on any distro (and assuming the CPU supports PAE, which this should), you can handle up to 64GB on 32bit linux.  I don't think debian defaults to a pae kernel, but there's one in the repos.

The only time I've had trouble running 64bit is when I tried to install some off-the-wall proprietary stuff that was 32bit only.  Probably nothing that's going to be an issue on a TV system.

---

### Post by uRock on 2013-07-02
> **MadmanRB said:**
> I dunno, because its an older processor you may want to go 32bit.
It wont be beneficial to go 64bit if the max ram is 4GB

+1 I installed lubuntu 32bit on my old Lenovo and it runs better that the 64 bit install did. That system only has 2 gigabytes of RAM.

---

### Post by mips on 2013-07-03
> **uRock said:**
> +1 I installed lubuntu 32bit on my old Lenovo and it runs better that the 64 bit install did. That system only has 2 gigabytes of RAM.

Compare compressing/uncompressing files, encoding/decoding audio & video, running encryption algorithms etc and you will see 64-bit wins by a big margin.

If you have a 64-bit system there's very little point in not running a 64-bit OS as it will perform better. The one downside is 64-bit will use more RAM and if you are short on RAM you will take a hit, 4GB however is plenty.

---

### Post by mamamia88 on 2013-07-03
> **mips said:**
> Compare compressing/uncompressing files, encoding/decoding audio & video, running encryption algorithms etc and you will see 64-bit wins by a big margin.

If you have a 64-bit system there's very little point in not running a 64-bit OS as it will perform better. The one downside is 64-bit will use more RAM and if you are short on RAM you will take a hit, 4GB however is plenty.

Well i installed 64 bit debian with xfce and it runs great.  Makes me think people are too quick to upgrade their computers or there is some kind of conspiracy in the industry to keep people upgrading.  But 3.4ghz dual core intel chip and 2gb ram for $110 shipped seems like a really good deal.  Thanks for all the help

---

### Post by uRock on 2013-07-03
> **mips said:**
> Compare compressing/uncompressing files, encoding/decoding audio & video, running encryption algorithms etc and you will see 64-bit wins by a big margin.

If you have a 64-bit system there's very little point in not running a 64-bit OS as it will perform better. The one downside is 64-bit will use more RAM and if you are short on RAM you will take a hit, 4GB however is plenty.I did mention I tested both and which one did better with the 2GB RAM, which is the MB's limit.

---

