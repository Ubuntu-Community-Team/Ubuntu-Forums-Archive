---
title: "Unable to install anything"
date: 2014-01-10
forum: Any Other OS
---

### Post by mandeeprayat on 2014-01-10
Hi.. I am new here. I recently installed BackTrack on a machine but I am not able to install anything on it. Whenever I am trying it is giving me error. Following is the output I am getting:    root@bt:/# apt-get upgrade Reading package lists... Done Building dependency tree        Reading state information... Done 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 2 not fully installed or removed. After this operation, 0B of additional disk space will be used. Do you want to continue [Y/n]? y dpkg: warning: 'ldconfig' not found on PATH. dpkg: warning: 'start-stop-daemon' not found on PATH. dpkg: warning: 'update-rc.d' not found on PATH. dpkg: 3 expected program(s) not found on PATH. NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin. E: Sub-process /usr/bin/dpkg returned an error code (2)   I am getting this whenever I am trying to install anything..   Plz help...Thanks in advance..

---

### Post by TheFu on 2014-01-10
To fix the formatting, please use "code" tags. This is found in the "Adv Reply."  Editing the original post would be best.

In the meantime, it appears something is really borked with the installation - could be that important files were deleted (sudo or root needed) or a loose HDD cable or failing HDD or cracked MB.  I'd guess the errors above are just symptoms of the real error to be discovered. Basically, something is wrong so we need more information.

Check the system log files for any warnings or errors. That should lead to what the root cause is. You probably already know [howto do this.]("http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files")

---

### Post by oldfred on 2014-01-10
Moved to otherOS since not Ubuntu.

I thought Backtrack was replaced with a newer different distribution?

---

### Post by TheFu on 2014-01-10
> **oldfred said:**
> Moved to otherOS since not Ubuntu.

I thought Backtrack was replaced with a newer different distribution?

It was and I saw an announcement for a new Kali release this morning. These are distros meant to be used for penetration testing, NOT as a normal desktop. Still, I would be shocked if the maintainers tried to break dependencies, but they are security people 1st, linux people 2nd. I could see where They would install from source or with specific .deb files that wouldn't be compatible with the normal repositories.

---

### Post by hoopia on 2014-01-10
It looks like your PATH is not defined, most likely due to some problem that occurred during the install process. This should be fixable by updating your /etc/sudoers file:

```

Defaults   env_reset
Defaults   secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin" 

```

Source: [http://forums.debian.net/viewtopic.php?f=20&t=69093](http://forums.debian.net/viewtopic.php?f=20&t=69093)

---

