---
title: "Can't install 6.06 on iMac g3/233"
date: 2006-08-10
forum: Apple PPC Users
---

### Post by JKJ on 2006-08-10
I've downloaded the alternate install of Ubuntu 6.06 and burned the iso.

When i put it in my imac bondi blue and press the c-botton during startup the install screen comes up, but no matter "which kind of install" i type i just get this message:

[ 136.631551] RAMDISK: incomplete write (-28 != 32768 ) 8300
[ 136.877536] RAMDISK: ran out of compressed data
[ 136.877890] invalid compressed format (err=1)
[ 136.883787] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(1.0)
[ 136.884376]  _

What am i doing wrong? I downloaded the alternate because lack of ram. I am only interested in having Ubuntu on my mac. No dual boot or something like that.

:confused:

---

### Post by linear on 2006-08-10
Just how much RAM do you have? You may be unable to run Dapper at all.

---

### Post by JKJ on 2006-08-10
> **linear said:**
> Just how much RAM do you have? You may be unable to run Dapper at all.

Have 32mb

Which distro can i run then?

---

### Post by avtolle on 2006-08-10
[http://ubuntuforums.org/showthread.php?t=98233&highlight=Ubuntulite](http://ubuntuforums.org/showthread.php?t=98233&highlight=Ubuntulite) provides one option. W/32 mb RAM, I would normally point you to Damn Small Linux, except it doesn't run on PPC AFAIK. Perhaps Debian Sarge; see [http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html), which is somewhat outdated as to Ubuntu, but still valid  as to Debian, IIRC.

---

### Post by JKJ on 2006-08-10
> **avtolle said:**
> [[url]http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html]([url]http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html), which is somewhat outdated as to Ubuntu, but still valid  as to Debian, IIRC.

When trying this i get the message: Unknown or corrupt filesystem

---

### Post by avtolle on 2006-08-10
Probably your best bet is to read the How To on Ubuntulite; generally involves downloading and installing server version of Ubuntu, then adding light weight (low resource) desktop, etc. I **believe** that the folks doing this have constructed an iso to download, but am not totally sure. From my recollection, there is at least one post in the thread from someone who installed on a 32mb system w/success. The install on Low Ram How To was an earlier attempt by one of the players in Ubuntulite to run a "bare bones" system; the better bet now is the Ubuntulite.

---

