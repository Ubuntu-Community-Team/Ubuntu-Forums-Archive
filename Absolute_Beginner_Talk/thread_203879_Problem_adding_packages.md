---
title: "Problem adding packages"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by Cod on 2006-06-26
Hi,
I'm completely new to Linux so bear with me.
I've installed Ubuntu OK and have managed to connect to the internet (which is how I'm posting this message).  I want to add some new applications so I tried using Add/Remove packages under Applications.

When I try to reload the list of available packages I get an error message:

"The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences."

The repository addreses are:
"http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg: Could not connect to gb.archive.ubuntu.com:80 (85.133.25.8). - connect (111 Connection refused)
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Could not connect to gb.archive.ubuntu.com:80 (85.133.25.8). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to archive.ubuntu.com:80 (85.133.25.8). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
"

Any idea what's going on?  Is it my connection (but I am connected to the internet)?  Are the repositories out of date, and if so, where do I get new ones from?

Any help much appreciated

---

### Post by slimdog360 on 2006-06-26
System- Admin- Synaptic.
then go to settings- repositories. You can choose the places where to get the repositories from etc in there.

---

### Post by Cod on 2006-06-26
Thanks for the help.  I'll give it a try (and apologies for the late thanks - just got back from work)

---

