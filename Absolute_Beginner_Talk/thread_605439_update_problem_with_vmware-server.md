---
title: "update problem with vmware-server"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by muguwmp67 on 2007-11-07
The update manager popped up today to inform me of an update available for vmware-server (v 1.03-1).  I installed the update, and it appears to have updated sucessfully, but vmware-server is not getting cleared from the list of updates.

If I do:

```
sudo apt-get update
sudo apt-get upgrade

```

It tries to apply the vmware-server update again.

---

### Post by skillllllz on 2007-11-07
I have the same exact problem on two of my machines, but not on a third. All  three are running Feisty 7.04 and have VMWare Server installed via apt-get. Could this be caused by some sort of conflict between two repositories?

---

### Post by lenticular on 2007-11-07
Same problem here with Feisty on two of my machines starting with yesterday's upgrade.

-John

---

### Post by twistedtwig on 2007-11-07
aye same here!

---

### Post by schneertz on 2007-11-07
Me too, on my Fiesty machine.

---

### Post by newportl on 2007-11-07
Same problem here.  Running Feisty.

---

### Post by twistedtwig on 2007-11-07
can I ask how everyone installed it to begin with?  wondering if Automatix was used?

---

### Post by schneertz on 2007-11-07
I installed via Add/Remove, IIRC.

---

### Post by scorp123 on 2007-11-07
> **twistedtwig said:**
> can I ask how everyone installed it to begin with? I installed it via Canonical's commercial repos. The relevant line in /etc/apt/sources.list says: ```
deb http://archive.canonical.com/ feisty-commercial main
```

---

### Post by skillllllz on 2007-11-07
> **scorp123 said:**
> I installed it via Canonical's commercial repos.


I too installed it from the commercial repos.

---

### Post by kameleon25 on 2007-11-07
I too am having this issue. Kind of annoying. I noticed that the version from-to is the same even before I did the upgrade. Weird.

And yes 7.04 on that machine that has the issue.

---

### Post by rubbrduck on 2007-11-08
Copy that, same thing here.

Only difference is that I downloaded the vmware installation from [http://www.vmware.com/download/server/](http://www.vmware.com/download/server/).
I have the issue on my home workstation, and my laptop (both running feisty).

No difference after apt-get {update upgrade}

---

### Post by JohnPhys on 2007-11-08
I'm also running feisty and am experiencing this issue.  I installed it from either the universe/multiverse or commercial repository (not sure where it's from).  Never used automatix.

--John

---

### Post by LakeWind on 2007-11-10
I've also got the same problem with my Feisty system. This unresolved bug has been reported and you can follow it here:

[https://bugs.launchpad.net/ubuntu/+source/vmware-server/+bug/160683](https://bugs.launchpad.net/ubuntu/+source/vmware-server/+bug/160683)

Hope it's fixed soon.

---

