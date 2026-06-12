---
title: "Update not working"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by t.z0n3 on 2007-11-26
I've tried to update my Fesity to 7.10, but it won't work. 

I get this:

```
Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz Sub-process gzip returned an error code (1)

```

Can anyone tell me what I'm doing wrong? I think all of my stuff is enabled (multiverse, universe, etc.).

---

### Post by t.z0n3 on 2007-11-26
Bump

---

### Post by spiderbatdad on 2007-11-26
sever down?

---

### Post by rsambuca on 2007-11-26
Please wait a day or two before bumping your own posts in the future.

You might want to try another mirror for your repositories.

---

### Post by t.z0n3 on 2007-11-26
I don't understand what you mean by other server. I'm just clicking on the update button under the updates at the right hand side of my screen.

And as for the bumping, once my topics go beyond the first page, I've had bad luck with people searching for them. Sorry.

---

### Post by dr johnson on 2007-11-27
system > administration > synaptic package manager > settings > repositories > updates...
tick the boxes you want :-)

---

### Post by t.z0n3 on 2007-12-09
All of them are checked, so my repositories weren't the problem. 

I've tried several times, so if the server is down, it's becoming ridiculously so. 

This is really starting to nag at me. If the update doesn't work (and if none of you have any more fixes), how can I NOT overwrite my home directory and installl Gutsy?

---

### Post by Clickbg on 2007-12-09
Paste the output of commands:

ping us.archive.ubuntu.com
traceroute us.archive.ubuntu.com

---

### Post by t.z0n3 on 2007-12-09
They just keep going and GOING! Do those commands ever actually stop? :confused:

---

### Post by swerner on 2007-12-14
I would actually just UNTICK the Feisty security and Feisty updates options in your repository section.  Then upgrade and tick the boxes again.  Let me know how it goes.

---

### Post by t.z0n3 on 2007-12-29
> **swerner said:**
> I would actually just UNTICK the Feisty security and Feisty updates options in your repository section.  Then upgrade and tick the boxes again.  Let me know how it goes.

Actually, it's only missing one file each time now. It returns error code 2, if that means anything. ><

> Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

---

### Post by rc89pl on 2008-01-01
Same problem here. Given advices won't work. Please help ;|

---

### Post by rsambuca on 2008-01-01
> **rc89pl said:**
> Same problem here. Given advices won't work. Please help ;|

There have been a lot of different problems discussed here.  What exact problem(s) are you having?

---

