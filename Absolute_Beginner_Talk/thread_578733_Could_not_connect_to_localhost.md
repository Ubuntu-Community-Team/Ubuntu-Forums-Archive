---
title: "Could not connect to localhost"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by cosmiccharles on 2007-10-17
It seems that I have some how messed up my network settings. When I perform an apt-get instal it unpacks and then I get this error message:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe xchat-common 2.8.4-0ubuntu5
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe xchat 2.8.4-0ubuntu5
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xchat/xchat-common_2.8.4-0ubuntu5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xchat/xchat-common_2.8.4-0ubuntu5_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xchat/xchat_2.8.4-0ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xchat/xchat_2.8.4-0ubuntu5_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I am not sure what this means. All I know is I am unable to apt-get install or update. Can anyone help?

---

### Post by caspar_wrede on 2007-10-17
Can you post the contents of the file "hosts" in the /etc directory?

---

### Post by cosmiccharles on 2007-10-17
**It says this:**

127.0.0.1	localhost
127.0.1.1	charles-laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts



**What does any of this mean? Any help?**

---

### Post by bodhi.zazen on 2007-10-17
See if this link helps :

[http://www.linuxforums.org/forum/debian-linux-help/104921-apt-get-update-error-111-connection-refused.html](http://www.linuxforums.org/forum/debian-linux-help/104921-apt-get-update-error-111-connection-refused.html)

---

### Post by cosmiccharles on 2007-10-17
Ah man, I am somewhat starting to get what may be going on here but I as a newbie, I am still rather lost. This is probably because I' not all that great with this stuff in the first place. So in other words, no, that did not help me. There is just too much indirect suggestions or variables that I am just not sure of. What may have on wrong here? Anyone else have any steps to rectify this problem?

---

### Post by bodhi.zazen on 2007-10-18
LOL, well lets take a look then.

Open a terminal and type:

```
cat /etc/environment
```

See if it looks anything like this :> # +ANON_MARK+ Don't change this while anon-proxy manages this variable.
# +ANON_MARK+ To take back control of it run dpkg-reconfigure and tell
# +ANON_MARK+ debconf not to set this variable for you.
HTTP_PROXY=http://localhost:4001 # +ANON_MARK+
http_proxy=http://localhost:4001 # +ANON_MARK+

If it does, that is the problem.

To fix it :

```
sudo dpkg-reconfigure anon-proxy
```

and when answering the questions tell it NOT to write to /etc/environment ??

Then, edit /etc/environment and comment out those lines:

```
gksu gedit /etc/environment
```

> # +ANON_MARK+ Don't change this while anon-proxy manages this variable.
# +ANON_MARK+ To take back control of it run dpkg-reconfigure and tell
# +ANON_MARK+ debconf not to set this variable for you.
# HTTP_PROXY=http://localhost:4001 # +ANON_MARK+
# http_proxy=http://localhost:4001 # +ANON_MARK+

Alternately just remove the proxy :

```
sudo apt-get remove --purge anon-proxy
```

remove those lines form /etc/environment

REBOOT

Best of luck

---

### Post by cosmiccharles on 2007-10-18
THIS TOTALLY WORKED! Thank you, thank you, thank! So would this by chance have been caused because I loaded that anon proxy application?

---

### Post by bodhi.zazen on 2007-10-18
\o/

Yes, that that anon proxy application was the problem.

It would help others if you were to file a bug report. You can link to this thread ...

How to : [http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

---

