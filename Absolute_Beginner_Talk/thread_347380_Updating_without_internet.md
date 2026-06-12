---
title: "Updating without internet"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by Serotonin on 2007-01-27
I did search the forums before posting this, and I found a link to this website: 

[http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/](http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/)

My question is based loosely on the concept of updating without internet at all. At the current moment, it is highly unlikely I will never be able to use the internet on my Ubuntu system so I was wondering if when the latest version of the system comes out (I.e. when Edgy replaced Dapper), will I be able to update the whole system, without a reinstall, via a newly burnt ISO off the latest version? 

If so, how will this be done?

As you can probably tell, I am new to the whole "Linux" thing, so, I don't know what I can do about this problem yet. 

Thanks, 
Craig.

---

### Post by jvc26 on 2007-01-27
I think you can upgrade your computer via the alternate install cd .iso. You will have to check out either:
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)
I'm afraid I can't remember where I read it, but I think you can download the alternate cd, and then using that as a resource you can update your install to the latest version. Note that via cd you wont get the periodic updates which happen fairly regularly. Take a peek round the (above) sites and I'm pretty sure it was on one of them.
Il

---

### Post by nullmind on 2007-01-27
You might be able to specify the path to a repository that is on a local storage meduim.

Just go to **System -> Administration -> Software Sources**

In the **Third Party** tab there is a section to add repositories that are usually on the web, but I wouldn't be suprised if you could specify any protocol like this:

deb file://some/path/to/a/place/ edgy main

Here is one of the repositories: [http://archive.ubuntu.com/ubuntu/dists/edgy/](http://archive.ubuntu.com/ubuntu/dists/edgy/)
You most likely do not want the entire thing! But you can also browse the repo and download the sections of interest (keeping in mind that packages that depend on others will also need to be available)

---

### Post by Serotonin on 2007-01-27
> **nullmind said:**
> You might be able to specify the path to a repository that is on a local storage meduim.

I assume the repository is where a Ubuntu system updater would look to find the updates for the system? 

And I'll check out those links later Illuvator, I'm going to a friend's 18th now. If there is an alternate install ISO then I'll try that, too. 

Thanks, 
Craig.

---

