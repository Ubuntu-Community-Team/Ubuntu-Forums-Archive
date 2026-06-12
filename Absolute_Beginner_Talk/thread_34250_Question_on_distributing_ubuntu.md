---
title: "Question on distributing ubuntu"
date: 2005-05-14
forum: Absolute Beginner Talk
---

### Post by contact_dchan on 2005-05-14
Hi! I am pretty new in open source licensing and have a few questions:

1. Is ubuntu under the GNU license?

2. When I distribute ubuntu to my customers and friends, do I need to give the source code also? If so, where can I find the source code image to download, I can only find the install and live CDs.

3. Can I burn as many ubuntu CDs from an downloaded image as I want?

4. Can I use a single ubuntu CDs to install the system on as many as computers as I want?

Thanks.

---

### Post by 23meg on 2005-05-14
1) there's no mention of the GPL in ubuntu's [licence policy page](http://www.ubuntulinux.org/ubuntu/licensing/document_view), thus it's safe to assume it's not licensed under the GPL. the licence definition on this page is quite similar to that of the GPL though, and you should bear in mind that the Free Software Foundation recognizes only one single distro (i don't remember its name) among the thousands available as completely "free" (=GPL compatible). 

2) quoting the licence policy page:

> All application software included in the Ubuntu main component:

    * Must include source code. The main component has a strict and non-negotiable requirement that application software included in it must come with full source code.
    * Must allow modification and distribution of modified copies under the same licence. Just having the source code does not convey the same freedom as having the right to change it. Without the ability to modify software, the Ubuntu community cannot support software, fix bugs, translate it or improve it.


you can get source codes for any package by adding "source" options to each repository you want sources from in your sources.list file, i think. someone with better knowledge of this please correct me if i'm wrong. but really, i have to ask as well, where exactly in the main installation and the cds can we access the source codes?

3) yes

4) yes

---

### Post by N'Jal on 2005-05-15
> 
2. When I distribute ubuntu to my customers and friends, do I need to give the source code also?

Only if they ask for it and if Ubuntu say's you have to

---

### Post by N'Jal on 2005-05-15
> 
2. When I distribute ubuntu to my customers and friends, do I need to give the source code also?

Only if they ask for it and if Ubuntu say's you have to. If they ask for it and Ubuntu say you can't or don't have to distrbute it then no. If Ubuntu say if they DO ask for it then you must give them the source code then you must.

---

### Post by az on 2005-05-15
1.  There are two categories of software on the cd (and in ubuntu)  Software that is GPL-compatible (which respects the debian free software guidelines) and the stuff that does not.  Everything that is in multiverse is the latter.
So, basically if you want 100 percent free software on your system, remove the linux-restricted-modules package and you are there.

2.  Canonical distributes Ubuntu and it is up to them to provide the source.  If you distribute an Ubuntu cd, you are distributing Caninical's work, so it is still up to them to provide the source.  
If you make a derivative work of the software in Ubuntu, it becomes your responsability to provide the source.  Making a copy of the cd is not making a derivative work.  Making an add-on cd or a cusom cd with different packages is.

---

