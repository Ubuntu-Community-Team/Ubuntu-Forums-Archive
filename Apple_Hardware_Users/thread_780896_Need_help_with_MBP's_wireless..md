---
title: "Need help with MBP's wireless."
date: 2008-05-03
forum: Apple Hardware Users
---

### Post by cksubs on 2008-05-03
I'm using:
Ubuntu 8.04
Macbook Pro Generation 2 EDIT: "MacBookPro2,2"
Have access to a wired line, which works correctly.

I need major help getting my wireless working. I've followed the steps outlined on the wiki, the first step of which is:

sudo apt-get install build-essential autoconf automake

but this cannot find the package. Is it gone, or somewhere else now? What should I do? Why doesn't this work correctly out of the box?

---

### Post by JCasper on 2008-05-03
Goto administration > software sources > and enable the cd as a source. This downloads it off the cd. I had the same problem.

Only thing is, I still can't get wireless to work.

---

### Post by cyberdork33 on 2008-05-03
> **JCasper said:**
> Goto administration > software sources > and enable the cd as a source. This downloads it off the cd. I had the same problem.

Only thing is, I still can't get wireless to work.
no need to add the cd as a source.

just install build-essentials and continue from there. if a package is not found, don't install it.

---

### Post by cksubs on 2008-05-05
Can you elaborate please? I really have no idea what I'm doing, so more explicit help would be great. How do i install build-essentials? And what must I do after that?

---

### Post by cyberdork33 on 2008-05-05
> **cksubs said:**
> Can you elaborate please? I really have no idea what I'm doing, so more explicit help would be great. How do i install build-essentials? And what must I do after that?
The command ```
 sudo apt-get install build-essential autoconf automake
``` invokes the 'apt-get' utility with root priviledges (sudo) and tells it to install "build-essential", "autoconf", and "automake". Just try installing ONLY build-essential (that is no 's' on the end).

```
sudo apt-get install build-essential
```then follow the rest of the how-to. If you run into other issues, just post back again.

---

### Post by cksubs on 2008-05-06
Alright, installing only build-essential worked (after listing the CD as a source). But now I'm stuck again.

The snapshots URL in the next line of the wiki produces a 404.

Using the other method, with the "svn co ...." stuff gives me a "svn is not installed" error and tells me to "sudo apt-get install subversion," which of course does not work.

Next step?

---

### Post by cksubs on 2008-05-06
Woooooooooooooo got it working. I'm not going to say I know how, but just re-opening Terminal every time something in the tutorial didn't work and trying it again seemed to do it.

---

### Post by russo.mic on 2008-05-09
Are you trying to compile madwifi?  

Just a hint, if you can't get madwifi working, don't give up.  NDISWrapper is another easy to install option.  there are plenty of how-tos on the forums.  

If you can't get madwifi, repost here and I'll try and walk you through ndiswrapper should you be unable to find a clear howto.

Russo

---

