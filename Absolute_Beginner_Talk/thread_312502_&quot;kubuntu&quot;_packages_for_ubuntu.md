---
title: "&quot;kubuntu&quot; packages for ubuntu"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by Sunborn on 2006-12-04
I have three newb questions. 

[LIST=1]
[*]What are the backports repositories and is there anything wrong with enabling them? I assume they have old versions of programs but I am wary because they are not on by default.

[*]Is there anything wrong with using a package that says it is for kubuntu but I use ubuntu?

[*]Are the kubuntu repositories/packages the same as the ubuntu ones, can I just grab a kubuntu package from synaptic?
[/LIST]

Apparently the newest stable kubuntu version of a program I want to use is 2.0 in the backports repository but the ubuntu one in the regular repository is 1.2.

Thanks in advance

---

### Post by igknighted on 2006-12-04
You should be able to use KDE apps (kubuntu) on Ubuntu (gnome).  In some cases there may be issues with performance because the extra KDE apps have to be loaded along with the GNOME ones, but most fast computers shouldn't have an issue.  Also, backports are actually newer versions of software that get added after the release, the repo is commented out by default because in some cases upgrading a program could update a shared library which might cause a breakage in another program.  You could also install the kubuntu desktop, so you could choose KDE instead of GNOME when you wanted to use that program, especially if the KDE app doesn't run well in GNOME.

---

### Post by Bachstelze on 2006-12-04
There are no "kubuntu" packages. Kubuntu and Ubuntu are the same thing ! So yeah, they use the same repos and the same packages.

And as you can see, the backports repo has newer versions of some programs but is not officially supported, which is why it is disabled by default.

---

### Post by Sunborn on 2006-12-04
> **HymnToLife said:**
> There are no "kubuntu" packages. Kubuntu and Ubuntu are the same thing ! So yeah, they use the same repos and the same packages.

And as you can see, the backports repo has newer versions of some programs but is not officially supported, which is why it is disabled by default.

Thanks, that is exactly what I needed to know.

---

