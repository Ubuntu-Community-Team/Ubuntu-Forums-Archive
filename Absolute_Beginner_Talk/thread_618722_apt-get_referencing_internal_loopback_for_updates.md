---
title: "apt-get referencing internal loopback for updates?"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by Kolfinna on 2007-11-20
Hello, all.
I have a bit of a problem with apt-get and/or synaptic... really, the same problem.
Anyway, during any updates, instead of pinging the actual location of where packages are located, it pings the NIC's internal loopback address instead (127.0.0.1). I did have the anonymous-surfing package running and ccrypt, but I've removed them both and am still having problems.

I also referenced the article " apt-get errors : localhost:4001 (127.0.0.1) ", which pretty much sums up what I have going on. 

Here's my code output... what do I need to do to fix this and re-install the encryption after it's done? Or, how can I find out what my specific proxy is and configure synaptic to play nice?

Thanks!

~Kolfinna

Output:
[COLOR="Red"]root@3[kolfinna]#[/COLOR] apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://apt.mepis.org](http://apt.mepis.org) mepis Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://apt.mepis.org](http://apt.mepis.org) mepis Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://apt.mepis.org/mepis32-6.5/dists/mepis/Release.gpg](http://apt.mepis.org/mepis32-6.5/dists/mepis/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://apt.mepis.org/simply32-6.0/dists/mepis/Release.gpg](http://apt.mepis.org/simply32-6.0/dists/mepis/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/dapper/Release.gpg](http://medibuntu.sos-sts.com/repo/dists/dapper/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[COLOR="Red"]root@3[kolfinna]#[/COLOR] echo $http_proxy
[http://localhost:4001](http://localhost:4001)

---

### Post by markharding557 on 2007-11-20
you need to check your proxy settings perhaps change it to direct connection

---

### Post by Kolfinna on 2007-11-20
By listing the article I followed means that I already took the steps mentioned there... sorry I didn't clarify.

But yes, synaptic is set to a direct connection by default but is still referencing internal loopback.
Hence my curiosity in configuring proxy settings for synaptic...

~K

---

### Post by OffAxis on 2007-11-20
in the article you referenced (I assume this one [http://ubuntuforums.org/showthread.php?t=234704]("http://ubuntuforums.org/showthread.php?t=234704")
they mentioned that they could run the updates as root instead of sudo...
can you?

```
sudo -i
apt-get update

```

---

### Post by Kolfinna on 2007-11-20
I typed
ps -e | grep -e apt -e adept | grep -v grep

and that got everything unlocked... 
As sudo -i in terminal I was able to get the updates. Yay! :)

So that at least answers the possibility to get updates... but what do I need to do to make this possible using synaptic in a user profile? 

Thanks!

~K

---

### Post by OffAxis on 2007-11-21
what's the name of the 'anonymous surfing package' that you had installed?
(I don't think ccrypt runs the connection through a proxy, internal or otherwise)

Since you can connect on the root account, I'm guessing there's a hidden file  under your profile that is doing the reroute.

```
ls ~ -a
```

There should be a 
**.synaptic**
folder in the list. I'd start there.

---

### Post by twiceasworn on 2007-11-21
> **OffAxis said:**
> what's the name of the 'anonymous surfing package' that you had installed?
(I don't think ccrypt runs the connection through a proxy, internal or otherwise)

Since you can connect on the root account, I'm guessing there's a hidden file  under your profile that is doing the reroute.

```
ls ~ -a
```

There should be a 
**.synaptic**
folder in the list. I'd start there.

I think this is certainly the issue.  You never know how many hidden directories/files/config files are in your home directory.

---

