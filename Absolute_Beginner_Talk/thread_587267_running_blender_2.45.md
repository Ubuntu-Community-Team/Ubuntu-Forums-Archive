---
title: "running blender 2.45"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by limac on 2007-10-22
hi,

I am using gutsy and I downloaded blender 2.45 in it manually using internet and when i looked at how to install it, I came across some unfamiliar info. So I will be needing your help to get me to successfully install it.the unfamiliar info is:

after unpacking the distribution, you can copy the .blender directory from it to your home directory.

So what exactly do they mean by saying to copy the .blender directory from it to your home directory? How do u do that thing?

I'm a real newbie.

Thnx

---

### Post by Maestro23 on 2007-10-22
Before we get into installing stuff from source, you do know Blender 2.44 is in the repositories.  You can install that if you want.  Are there just some vast improvements from 2.44 to 2.45 that you must have?

---

### Post by Paul820 on 2007-10-22
> Are there just some vast improvements from 2.44 to 2.45 that you must have? Loads of bug fixes.

@limac, I just put the whole folder in my home directory and created a menu item for it. You need python2.4 installed for it to work.

---

### Post by Maestro23 on 2007-10-22
> **Paul820 said:**
> Loads of bug fixes.

@limac, I just put the whole folder in my home directory and created a menu item for it. You need python2.4 installed for it to work.

Ok, cool.  Never used the program myself.  Looks pretty cool though.

---

### Post by Hospadar on 2007-10-22
also note the the .blender folder will be hidden by default.  In nautilus, ctrl-H to show hidden files (or View->Show Hidden Files)  you can just drag the folder into your home directory, or if you prefer command line, open a terminal and cd to where the .blender directory is in where you unpacked the software you downloaded, and do a ```
cp -rf .blender ~
```

---

### Post by TKR101010 on 2007-10-22
I love Blender. It's one of my favorite programs :)

I recommend downloading the Blender 2.45 .deb file from GetDeb ([http://www.getdeb.net/search.php?keywords=blender](http://www.getdeb.net/search.php?keywords=blender)), 'cause that's a lot easier than dealing with the source code or the binaries available on Blender's page. There were a couple of dependencies that I had to find myself, but the package manager will tell you what you need when you go to try to install it. I think I only had to download 2 libraries to fullfil the dependencies. But afterwards you'll be all set with 2.45 :)

---

