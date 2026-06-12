---
title: "Thunderbird 2.0.0.12"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by Suncoaster on 2008-04-07
How do I upgrade to Thunderbird 2 in Feisty.   I have downloaded a tarball from the Mozilla site but how do I install this tarball.  I have extracted the files but where do I go from there.  Is there a deb package available, I have not been able to find one, maybe I am looking in all the wrong places.

I have only recently started using linux and can cope with everyday tasks but this is the first tarball I have come across.

Thanks in advance for your help

---

### Post by Crafty Kisses on 2008-04-07
You may have to compile the file, there should be a README.txt within the folder, read that.

---

### Post by Suncoaster on 2008-04-07
There is and all it states is:

For information about installing, running and configuring Thunderbird
including a list of known issues and troubleshooting information, 
refer to: [http://getthunderbird.com/releases/](http://getthunderbird.com/releases/)

All that does is take you to the download site which isn't much help.

---

### Post by VncentVega on 2008-04-07
I believe Thunderbird 2.0.0.12 is available in the main repository. Just run 

sudo apt-get install thunderbird

---

### Post by scramasax on 2008-04-07
> **VncentVega said:**
> I believe Thunderbird 2.0.0.12 is available in the main repository. Just run 

sudo apt-get install thunderbird

You're dead right.  I just looked in Synaptic, and it gives the version number there.  Not surprising -- (1) that one version's been out since February and (2) it includes security fixes.

---

### Post by stchman on 2008-04-07
> **Suncoaster said:**
> How do I upgrade to Thunderbird 2 in Feisty.   I have downloaded a tarball from the Mozilla site but how do I install this tarball.  I have extracted the files but where do I go from there.  Is there a deb package available, I have not been able to find one, maybe I am looking in all the wrong places.

I have only recently started using linux and can cope with everyday tasks but this is the first tarball I have come across.

Thanks in advance for your help

I have a script that installs 2.0.0.12 in Feisty.

[http://www.stchman.com/tools_page.html](http://www.stchman.com/tools_page.html)

Look in the Scripts section.

The tarball that you get from Mozilla website is a pre-compiled binary.  You do not have to make it.  If you wish to install from source then you can get the source code from the developers section.

---

### Post by aysiu on 2008-04-07
[https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion) should help.

---

