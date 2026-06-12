---
title: "lucid seems to have broken lirc + macbook remote"
date: 2010-05-04
forum: Apple Hardware Users
---

### Post by bluenode on 2010-05-04
After upgrading to lucid, the remote that accompanied my macbook 4.1 appears to do nothing.  (Testing with irw and xev).  The howto at <https://help.ubuntu.com/community/MacBook4-1/Lucid> avoids any reference to the remote.  

I had it working properly in karmic.  

The howto at <https://help.ubuntu.com/community/MacBook5-1/Lucid#Remote%20Control> fails to help -- and is pretty much what I'd successfully done under kamic.  

The following launchpad post accurately describes my experience:  <https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/567512>

Has anyone resolved, found a workaround for, or otherwise had success getting lirc to work on a macbook with lucid?

---

### Post by bluenode on 2010-05-24
I've been able, however clumsily, to restore lucid's lircd to karmic functionality.  I'd appreciate some help in re-doing the following properly and in a more sustainable way.    

I found further confirmation of lucid's broken state and a fix in the 7th post at:  
[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/567512]("https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/567512")

The author states that s/he was able to apply the referenced gentoo patch against lucid source.  I downloaded the patch from:
[http://bugs.gentoo.org/attachment.cgi?id=214663]("http://bugs.gentoo.org/attachment.cgi?id=214663")

Here it is:
```
--- daemons/lircd.c.old	2009-12-30 14:37:13.000000000 -0600
+++ daemons/lircd.c	2009-12-30 14:39:42.000000000 -0600
@@ -1909,6 +1909,17 @@
 				logprintf(LOG_ERR, "writing to uinput failed");
 				logperror(LOG_ERR, NULL);
 			}
+
+			/* Need to write sync event */
+			memset(&event, 0, sizeof(event));
+			event.type = EV_SYN;
+			event.code = SYN_REPORT;
+			event.value = 0;
+			if(write(uinputfd, &event, sizeof(event)) != sizeof(event))
+			{
+				logprintf(LOG_ERR, "writing EV_SYN to uinput failed");
+				logperror(LOG_ERR, NULL);
+			}
 		}
 	}
 #endif


```

I then installed lirc-modules-source but, upon inspection of the deb's files, couldn't find a "daemons/" directory nor a file named "lircd.c".  I guess 'cause lircd isn't a module :).  I couldn't find an "lirc-dev" package.  I searched fruitlessly at [http://packages.ubuntu.com/lucid/]("http://packages.ubuntu.com/lucid/") trying to find the proper package.  

So, I downloaded both the source tarball and diff/patch file from:
[http://packages.ubuntu.com/lucid/lirc-modules-source]("http://packages.ubuntu.com/lucid/lirc-modules-source")

I first applied lucid's patch file and then the gentoo patch.  Both were successful.  

I ran ./configure, selected the mac-mini remote, and then ran make.  

I did not run 'make install' because it seemed unwise to overwrite lots of kernel modules which were already installed via the lucid deb.  

Instead, I moved /usr/sbin/lircd to /usr/sbin/lircd.ORIGINAL
I copied the newly-built lircd to /usr/sbin/lircd.PATCHED
Then, I sym-linked /usr/sbin/lircd.PATCHED to /usr/sbin/lircd

My remote is now working imperfectly, as in Karmic, with the requirement of pausing between key presses and no repeat functionality (for volume control).  But it *is* working.  

What would be the proper "ubuntu way" of doing the foregoing?  

Any other suggestions/improvements would be very much appreciated.  

Thanks in advance for your assistance.

---

### Post by bluenode on 2011-12-06
The previously documented patch to lircd, stopped working within the last few days due to some combination of updates to Lucid.  The good news is that the official lircd works once more.  

Not only is it working but the previously inoperable repeat function now works with a vengeance.  I found that each key depression was repeated 10x.  At first, I tried modifying /etc/lirc/lircd.conf to include "suppress_repeat 9" but that resulted in no recognized input from the remote.  I found that it's an lirc bug:  [https://lists.launchpad.net/mythbuntu-bugs/msg03826.html]("https://lists.launchpad.net/mythbuntu-bugs/msg03826.html")

Eventually, I discovered that simply restarting lircd seems to resolve the problem.  Sometimes, however, a simple restart fails to work.  Based on a few hours' testing, I've had good luck with the following script included in my ~/.kde/Autostart/ directory.  

```
#!/bin/bash
sudo /etc/init.d/lirc stop
sleep 15
sudo /etc/init.d/lirc start
irexec -d &
irxevent -d &
```

If anyone knows what update(s) might have caused this change in behavior or can explain why a restart of the daemon fixes the repeat problem, please post.

---

