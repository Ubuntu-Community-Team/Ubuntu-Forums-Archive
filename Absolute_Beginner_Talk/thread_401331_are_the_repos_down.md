---
title: "are the repos down?"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by waxyfresh on 2007-04-04
root@sleepless:~# apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://seveas.theplayboymansion.net](http://seveas.theplayboymansion.net) dapper-seveas Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://seveas.theplayboymansion.net/seveas/dists/dapper-seveas/Release.gpg](http://seveas.theplayboymansion.net/seveas/dists/dapper-seveas/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/dapper/Release.gpg](http://wine.budgetdedicated.com/apt/dists/dapper/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://deb.opera.com/opera/dists/etch/Release.gpg](http://deb.opera.com/opera/dists/etch/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://people.ubuntu.com/~jbailey/snapshot/bzr/./Release.gpg](http://people.ubuntu.com/~jbailey/snapshot/bzr/./Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/dapper/Release.gpg](http://medibuntu.sos-sts.com/repo/dists/dapper/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.canonical.com/dists/dapper-commercial/Release.gpg](http://archive.canonical.com/dists/dapper-commercial/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
root@sleepless:~#

---

### Post by Happy_Man on 2007-04-04
Well, is your internet connection configured correctly? And another thing, any reason you are in root? In Ubuntu, you can use the sudo command (super user do) in front of anything to execute that task with root privileges. So, instead of doing 

```

sudo su
apt-get update

```

you can just do 
```

sudo apt-get update

```

Much easier.

---

### Post by bapoumba on 2007-04-04
> Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Are you behind a proxy ? Have you declared one somewhere ?

---

### Post by waxyfresh on 2007-04-06
i shouldent be behind a proxy,how do i tell

---

### Post by waxyfresh on 2007-04-07
acording to whatsmyip.org i dont have a proxy unless its an invisible one.jso what else coudl this be?

---

### Post by waxyfresh on 2007-04-07
dont think this will help much but here it is anyway.so im deffintly not behind a proxy right?


Portscan on IP 199.2.58.25

Checking for a SMTP server....
Testing port 25: Connection timed out....

Checking for a POP3 Server....
Testing port 110: Connection timed out....

Checking for a open proxy server....
Testing port 1080: Connection timed out....
Testing port 81: Connection timed out....
Testing port 8080: Connection timed out....

Checking for a open Windows share....
Testing port 136: Connection timed out....
Testing port 137: Connection refused....
Testing port 138: Connection refused....

Checking misc ports....

Results:
Tested ports that are closed:
25, 110, 1080, 81, 8080, 136,

Tested ports that are Open but not accepting connections:
137, 138,

Tested ports that are Open and accepting connections:
None

---

### Post by carlosp on 2007-04-13
I had the same problem after playing around with tor and privoxy.

I solved it by editing my .bash_profile.
I had to comment the following lines:

```
http_proxy=http://127.0.0.1:8118/
HTTP_PROXY=$http_proxy
export http_proxy HTTP_PROXY
```

and voilá!

---

