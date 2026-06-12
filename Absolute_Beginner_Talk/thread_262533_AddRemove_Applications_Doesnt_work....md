---
title: "Add/Remove Applications Doesnt work...?"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by reddeth on 2006-09-21
Alright, I'm still relatively new to Linux and deffinetly new to Ubuntu. First of all, the Add/Remove programs deal is awesome. however, it isnt working. Any time I try to update something, well, anything for that matter (repository list, an X-Org update, etc etc) I keep getting a "Connection Refused" message. I'm lost... I have a decent ammount of computer experience but its all with Windows so right now I'm just trying to understand it all...

Any help is appreciated.

---

### Post by aysiu on 2006-09-21
Problems are usually easier to diagnose from terminal output.

Can you post here the output of this command? ```
sudo aptitude update
```

---

### Post by reddeth on 2006-09-21
```
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 195.248.90.23 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
  Connection failed [IP: 195.248.90.23 80]
Reading package lists... Done

```

I'm sorry if this has been coverend, I have tried searching, and at this point am a bit overwhelemed. Thanks for the help.

I just noticed this, that may be whats wrong, this is what I think the 'update' command is TRYING to connect to:
```
http://us.archive.ubuntu.com dapper/main
```

Or something along the lines of that, shouldnt is be:
```
http://us.archive.ubuntu.com/dapper/main
```
(Note the '/' after the Ubuntu URL)

---

### Post by aysiu on 2006-09-21
[This page](http://www.ubuntuforums.org/showthread.php?t=208627&page=2) might help.

---

### Post by reddeth on 2006-09-21
Alright, I did what that page said, I tried editing my DNS servers, disabling IPv6, and it seems to happen at all sources.

Is it possible its an issue with the port (port 80 I beleive) and the router I'm using? Should I set it up to forward or something...?

---

### Post by aysiu on 2006-09-21
I'm not sure, to be honest. I've never had this problem, but I did a search for your error, and that was the best I could come up with.

I don't think you should need port forwarding for a simple Add/Remove...

---

### Post by reddeth on 2006-09-22
Hmm, alright, well thank you for your help. I'll keep looking for a solution, if I find it I'll post it

---

### Post by reddeth on 2006-09-28
Problem solved, sort of. Going off what others were saying, I found a common denominator, everyone seemed to be using a netgear router. So, I tried plugging directly into the Cable Modem and bam, updates galore.

So, kind of a solution, not perfect, but it works.

---

