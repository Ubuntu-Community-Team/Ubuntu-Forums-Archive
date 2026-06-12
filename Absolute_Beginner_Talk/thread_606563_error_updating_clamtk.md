---
title: "error updating clamtk?"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by genbuntu on 2007-11-08
Hi

I installed the latest version (3.04) of clamtk from : [http://sourceforge.net/project/showfiles.php?group_id=131278&package_id=144061](http://sourceforge.net/project/showfiles.php?group_id=131278&package_id=144061)

but am having trouble updating the virus definitions. So when I type ```
sudo freshclam
``` in terminal, I get the following error:

```
ClamAV update process started at Thu Nov  8 00:26:07 2007
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.90.2 Recommended version: 0.91.2
DON'T PANIC! Read http://www.clamav.net/support/faq
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.cvd is up to date (version: 4708, sigs: 32893, f-level: 21, builder: ccordes)
LibClamAV Error: Database Directory: /var/lib/clamav/ not locked

```

Updating graphically also gives the last error line in terminal.

Pls. advise. :)

P.S: I'd prefer not to be advised against using any anti-virus for linux. I know that its v. safe. However, this is for occassional scanning and for my dual-boot with windows.

---

### Post by markharding557 on 2007-11-08
it is telling you that the software is outdated but the virus definitions are up to date

---

### Post by genbuntu on 2007-11-08
So now its become even more out of control. When I try to update through GUI  it repetitively gives the error :
```

LibClamAV Error: Database Directory: /var/lib/clamav/ not locked
LibClamAV Error: Database Directory: /var/lib/clamav/ not locked
LibClamAV Error: Database Directory: /var/lib/clamav/ not locked
LibClamAV Error: Database Directory: /var/lib/clamav/ not locked
LibClamAV Error: Database Directory: /var/lib/clamav/ not locked
LibClamAV Error: Database Directory: /var/lib/clamav/ not locked
LibClamAV Error: Database Directory: /var/lib/clamav/ not locked
LibClamAV Error: Database Directory: /var/lib/clamav/ not locked
LibClamAV Error: Database Directory: /var/lib/clamav/ not locked

```

Then when I try to update via terminal this is what happens:

```
sid@zis:~$ sudo freshclam
ClamAV update process started at Thu Nov  8 17:33:31 2007
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.90.2 Recommended version: 0.91.2
DON'T PANIC! Read http://www.clamav.net/support/faq
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
Ignoring mirror 24.215.0.24 (too often connections with outdated version)
Ignoring mirror 208.70.244.158 (too often connections with outdated version)
Ignoring mirror 205.139.192.213 (too often connections with outdated version)
Ignoring mirror 67.15.61.160 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-4712.cdiff from db.local.clamav.net
Ignoring mirror 67.15.61.160 (too often connections with outdated version)
Ignoring mirror 24.215.0.24 (too often connections with outdated version)
Ignoring mirror 208.70.244.158 (too often connections with outdated version)
Ignoring mirror 205.139.192.213 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-4712.cdiff from db.local.clamav.net
Ignoring mirror 24.215.0.24 (too often connections with outdated version)
Ignoring mirror 208.70.244.158 (too often connections with outdated version)
Ignoring mirror 67.15.61.160 (too often connections with outdated version)
Ignoring mirror 205.139.192.213 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-4712.cdiff from db.local.clamav.net
Ignoring mirror 67.15.61.160 (too often connections with outdated version)
Ignoring mirror 208.70.244.158 (too often connections with outdated version)
Ignoring mirror 24.215.0.24 (too often connections with outdated version)
Ignoring mirror 205.139.192.213 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-4712.cdiff from db.local.clamav.net
Ignoring mirror 208.70.244.158 (too often connections with outdated version)
Ignoring mirror 24.215.0.24 (too often connections with outdated version)
Ignoring mirror 67.15.61.160 (too often connections with outdated version)
Ignoring mirror 205.139.192.213 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-4712.cdiff from db.local.clamav.net
WARNING: Incremental update failed, trying to download daily.cvd
Ignoring mirror 24.215.0.24 (too often connections with outdated version)
Ignoring mirror 67.15.61.160 (too often connections with outdated version)
Ignoring mirror 205.139.192.213 (too often connections with outdated version)
Ignoring mirror 208.70.244.158 (too often connections with outdated version)
ERROR: Can't download daily.cvd from db.local.clamav.net
LibClamAV Error: Database Directory: /var/lib/clamav/ not locked
Trying again in 5 secs...

```

and it does this a few times before saying:

```
Giving up on database.clamav.net...
Update failed. Your network may be down or none of the mirrors listed in freshclam.conf is working. Check http://www.clamav.net/support/mirror-problem for possible reasons.

```

My net and everything is working fine. Wonder what the problem is ?

---

### Post by markharding557 on 2007-11-09
have you considered the linux version of avg it's quite reliable

---

### Post by genbuntu on 2007-11-09
> **markharding557 said:**
> have you considered the linux version of avg it's quite reliable

hmm.. I read about other anti-virus programs also, like F-prot and avg but chose clamav because it seemed to me the most popular. Also, am not sure whether avg-linux can scan for both windows and linux viruses. (Isn't it only for linux viruses?)

Even then before jumping on to another product, I'd like to know what is causing these errors. Others have installed it successfully, so what could be wrong here...
Thanks

---

### Post by genbuntu on 2007-11-10
Ok, so finally I managed to resolve this :-\"
Here is what I did:

1) Completely removed all clamav, clamtk .. from synaptic.
2) Fresh installed latest version (0.91.2) of clamav (from source).

At this point when I tried ```
freshclam
``` it gave that 'locked' error ```
LibClamAV Error: Database Directory: /usr/local/share/clamav not locked 
```
and another error (which I cannot trace back in terminal). So after doing some homework (searching through internet), I made the following changes:
```

chown 112:121 /usr/local/share/clamav
chown 1000:1001 /usr/local/share/clamav
chmod 755 /usr/local/share/clamav
```

The numbers '112, 121, 1000, 1001'  were taken from the error hint: 
```
Hint: The database directory must be writable for UID 112 or GID 121
```
and
```
Hint: The database directory must be writable for UID 1000 or GID 1001
```

3) I updated the virus definitions using freshclam command.

4) Finally, I installed the GUI 'clamtk' , again using the latest .deb package (3.04) from sourceforge.

Now it seems to work just fine :) and I am giving myself a *pat on the back*  =D>

Doing these changes leads me to ask : [SIZE="2"]**[COLOR="Red"]Are the changes I've made using chmod and chown, Safe?[/COLOR]**[/SIZE] I read somewhere that one should not fiddle with chmod, chown... commands since it can compromise the security of the system. So I am a bit worried after whatever I have done to make clamtk work (I just used the commands without in-depth knowledge as to what it really is doing) .

---

