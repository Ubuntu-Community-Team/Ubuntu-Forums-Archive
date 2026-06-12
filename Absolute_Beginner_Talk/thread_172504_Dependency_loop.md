---
title: "Dependency loop?"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by Kurt` on 2006-05-08
[http://denyhosts.sourceforge.net/faq.html#1_15](http://denyhosts.sourceforge.net/faq.html#1_15)

Great, debian packages! not :P

After dpkg -i'ing denyhosts-python2.4_2.3-2_all.deb, I was notified that it depended on denyhosts-common. So I attempted to dpkg -i denyhosts-common_2.3-2_all.deb. I was then notified that that package is dependent on the python package.

wtf?

Now if I try to dpkg -r either of them, it says they're not installed. If I try to dpkg -i them, it says the other needs to be installed first. Even though it says they're not installed, I have a /usr/bin/denyhosts now...

Where do I go to edit what packages ubuntu thinks are installed? Is there a better way to fix this?

Any suggestions are extremely welcomed :p

---

### Post by Kurt` on 2006-05-10
Any ideas? This is pretty annoying, attempting to apt-get install anything results in:

root@gemini:/# apt-get install nessusd
Reading package lists... Done
Building dependency tree... Done
E: The package denyhosts-common needs to be reinstalled, but I can't find an archive for it.

`apt-get -f install` displays the same error as above. :(

---

### Post by ComplexNumber on 2006-05-10
many people claim that debian systems either don't have dependency issues, or have less dependency issues than rpm. in reality, they both do equally as much.
i'm sorry i couldn't help.

---

### Post by macdo on 2006-05-10
they need each other - so install them together!
I *think* that you can do so with dpkg: ```
sudo dpkg -i denyhosts-python2.4_2.3-2_all.deb denyhosts-common_2.3-2_all.deb
```
If thet doesn't work, you can create a local apt repository - follow the [Apt guide]("http://www.debian.org/doc/manuals/apt-howto/index.en.html")

---

### Post by Kurt` on 2006-05-11
```
root@gemini:~# dpkg -i denyhosts-python2.4_2.3-2_all.deb denyhosts-common_2.3-2_all.deb
(Reading database ... 26565 files and directories currently installed.)
Preparing to replace denyhosts-python2.4 2.3-2 (using denyhosts-python2.4_2.3-2_all.deb) ...
Unpacking replacement denyhosts-python2.4 ...
Preparing to replace denyhosts-common 2.3-2 (using denyhosts-common_2.3-2_all.deb) ...
 * I can't stop DenyHosts Maybe it's NOT runnig?
invoke-rc.d: initscript denyhosts, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
 * I can't stop DenyHosts Maybe it's NOT runnig?
invoke-rc.d: initscript denyhosts, action "stop" failed.
dpkg: error processing denyhosts-common_2.3-2_all.deb (--install):
 subprocess new pre-removal script returned error exit status 1
/etc/init.d/denyhosts: line 51: log_daemon_msg: command not found
invoke-rc.d: initscript denyhosts, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of denyhosts-python2.4:
 denyhosts-python2.4 depends on denyhosts-common (= 2.3-2); however:
  Package denyhosts-common is not configured yet.
dpkg: error processing denyhosts-python2.4 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 denyhosts-common_2.3-2_all.deb
 denyhosts-python2.4

root@gemini:~# dpkg --purge denyhosts-python2.4_2.3-2_all denyhosts-common_2.3-2_all
dpkg - warning: ignoring request to remove denyhosts-python2.4_2.3-2_all which isn't installed.
dpkg - warning: ignoring request to remove denyhosts-common_2.3-2_all which isn't installed.
```

From the apt-guide ([http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html#s-erros-comuns](http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html#s-erros-comuns)):

```
root@gemini:~# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
E: The package denyhosts-common needs to be reinstalled, but I can't find an archive for it.

root@gemini:~# dpkg --configure -a
dpkg: dependency problems prevent configuration of denyhosts:
 denyhosts depends on denyhosts-python2.3 (= 2.3-2); however:
  Package denyhosts-python2.3 is not installed.
dpkg: error processing denyhosts (--configure):
 dependency problems - leaving unconfigured
Setting up denyhosts-python2.4 (2.3-2) ...
dpkg: error processing denyhosts-common (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 denyhosts
 denyhosts-common

root@gemini:~# dpkg --configure -a
dpkg: error processing denyhosts-common (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of denyhosts:
 denyhosts depends on denyhosts-python2.3 (= 2.3-2); however:
  Package denyhosts-python2.3 is not installed.
dpkg: error processing denyhosts (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 denyhosts-common
 denyhosts
```

That's what I'm getting now. Extremely confused. What caused this problem initially, the fact that I didn't try to dpkg -i both packages at once?

Also, this is from /var/lib/dpkg/status/:

```
Package: denyhosts
Status: install ok unpacked
Priority: optional
Section: net

...

Package: denyhosts-common
Status: install reinstreq half-configured
Priority: optional
Section: net
```

---

