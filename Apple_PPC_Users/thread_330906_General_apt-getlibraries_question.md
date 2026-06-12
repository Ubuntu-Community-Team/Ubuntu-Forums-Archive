---
title: "General apt-get/libraries question"
date: 2007-01-03
forum: Apple PPC Users
---

### Post by dpny on 2007-01-03
So I'm trying to install mt-daapd so I can share the music on my Linux machine with my OS X machine's iTunes. As I can't find a PPC .dep of it I figured I'd compile. I've hit a dependency problem. ./configure tells me I need ibid3tag0-dev. No problem, I figure, and hop into Synaptic to get it. Synaptic tells me I have an error, so I try apt-get. Apt-get tells me:

```
sudo apt-get install libid3tag0-dev Reading package lists... Done 
Building dependency tree... Done 
Some packages could not be installed. This may mean that you have 
requested an impossible situation or if you are using the unstable 
distribution that some required packages have not yet been created 
or been moved out of Incoming. 

Since you only requested a single operation it is extremely likely that 
the package is simply not installable and a bug report against 
that package should be filed. 
The following information may help to resolve the situation: 

The following packages have unmet dependencies: 
  libid3tag0-dev: Depends: libid3tag0 (= 0.15.1b-7) but 0.15.1b-8 is to be installed 
E: Broken packages
```

If I'm reading this right, it's telling me that the -dev library is dependent on an older version of the main library than is currently installed. I tried to remove the newer version of libid3tag, but apparently the some of the gstreamer plugins are dependent on it, so that sounded like a bad idea.

So, questions:

1) Am I reading this right? If not, what is it really telling me?;
2) What can I do to fix the problem so I can install mt-daap?
3) Is there anything else I should know? Knowing me, the more obvious the more I'm missing it.

---

### Post by ssam on 2007-01-05
rhythmbox (ubuntu's default music player) can share music with daap. it might be an easier solution.

regarding the error message
```
sudo apt-get install libid3tag0-dev
```

word ok for me on ubuntu 6.10 (edgy). which version of ubuntu are you using?

---

### Post by dpny on 2007-01-05
> **ssam said:**
> rhythmbox (ubuntu's default music player) can share music with daap. it might be an easier solution.

regarding the error message
```
sudo apt-get install libid3tag0-dev
```

word ok for me on ubuntu 6.10 (edgy). which version of ubuntu are you using?

I'm running Dapper. I tried something suggested by a friend--remove the newer libid3tag and install the older version--which worked, and mt-daapd compiled.

---

