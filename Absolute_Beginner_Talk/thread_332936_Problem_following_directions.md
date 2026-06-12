---
title: "Problem following directions?"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by chatterbabies on 2007-01-06
Ok I found more than one helpful thread on how to get my Netgear USB WG111 wireless thing working. Problem is the first step. I'll refer to this thread [http://ubuntuforums.org/showthread.php?t=329299&highlight=wg111]("http://ubuntuforums.org/showthread.php?t=329299&highlight=wg111")
The first thing it says is to install and gives me the command. If I figured this out right I go Applications>Accessories>Terminal and paste that code in and give it my password. But I keep getting 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-utils-1.8
So I thought well maybe I have to have it on my computer, so I downloaded it. It didn't find it. I can't figure how to make it install. 
And would someone please tell me if all that code goes in the terminal?
Confused but not hopeless :D 
Thanks

---

### Post by just_old_bob on 2007-01-06
The first thing I can think of is to go to the terminal again and type ndiswrapper.
Just the word ndiswrapper if it comes up with a help screen listing options for ndiswrapper then it's installed.

---

### Post by jvc26 on 2007-01-06
It could be because you havent the right repos installed. A repo, or repository is a storage space with lots of apps and packages in it that you can install.
Anyhow: some of these are disabled by default, so go to:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)
And that may well help you out - after completing the above instructions, try your method again.

> **just_old_bob said:**
> The first thing I can think of is to go to the terminal again and type ndiswrapper.
Just the word ndiswrapper if it comes up with a help screen listing options for ndiswrapper then it's installed.
ndiswrapper is not installed straight away you have to install it.
:)
Il

---

### Post by just_old_bob on 2007-01-06
I should have read the post twice. Sorry.

I Installed ndiswrapper from Synaptic and had no problems.

---

### Post by jvc26 on 2007-01-06
:) No worries, with a change in repos and then following the guide chatterbabies is on all should be well :)
Il

---

### Post by chatterbabies on 2007-01-06
Thanks bunches off to do more reading! (They need a smilie with nerd glasses :-D )
You all are great!

---

