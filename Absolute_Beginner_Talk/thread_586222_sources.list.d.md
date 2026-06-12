---
title: "sources.list.d"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by ofb on 2007-10-22
Why do we have /etc/apt/sources.list.d rather than only /etc/apt/sources.list? I can't figure out the advantage or need of it, yet there's the obvious disadvantage of having to look in more than one place for what seems to be the same information.

The MAN page is a fine read but thin on motive. I'd like to know the intent of this feature, and how sources.list and sources.list.d are meant to work together. Could someone point me at documentation with that sort of detail?

---

### Post by molly_001 on 2007-10-22
If they are the same file exactly (contents) upon a fresh install of the operating system, then I would think that *.list.d (as appended with the letter 'd') is surely a default backup file.  That is, a fail-safe of the sources.list just in case the other file gets messed about with.

---

### Post by hyper_ch on 2007-10-22
sources.list.d is a directory that contains more repositories.

Medibuntu makes use of that system. So if you upgrade you can alter the medibuntu repo just by copying their code. If you have feisty and change to gutsy then the feisty version will be overwritten. It allows simpler "repo" updates.

The system is the same as with apache and the virtual hosts. In Apache 1.3 all was in the httpd.conf. Now you can put that all into another directory where you can configure for each vh an own file that will get parsed.

---

### Post by capink on 2007-10-22
As the previous poster said, this is in line with the debian policy of storing settings in directories instead of files, with each configuration entry in separate file. The same is also used for apt.conf.d. And if your run the following command you will see more examples:

```
find /etc -iname '*.d'
```

This allows for easier adding and removing of configuration options by just dumping - or removing - a file that contain the setting you want into the directory instead of missing ( i.e parsing ) with config files. This is specially handy for automatic modification of configurations by scripts or software.

The question I want to ask is how to make files in sources.list.d take precedence over entries in sources.list? I made a script that generates a local repositories and add entries to them in sources.list.d. The problem is that the Ubuntu repositories still have precedence over my local repositories.

I know I can overcome this problem by listing my local repositories in sources.list above the Ubuntu repositories. But the point is I don't want the script to miss with sources.list so I am using sources.list.d which is more convenient for me.

I tried apt-pinning but it only works for different versions of packages. That is, if I have the same version of the package in my local repository and Ubuntu repository, apt-pinning does not work.

---

### Post by ofb on 2007-10-22
This is largely a repeat of what's being said, but since I'm still wrapping my head around it, repeating is helpful and it gives others an opportunity to correct me.

What I was able to figure out last night is sources.list.d contains "fragments" that are to be merged with sources.list by any application using sources.list.

So it's an organizational tool. For example, a third party vendor like mediabuntu could create their own .list file within sources.list.d, and then modify it with autoupdates in future with reasonable confidence that they know what's already in there. If an autoupdater was let loose on the much more variable sources.list, you'd have a fair chance of the wrong things being altered.

I have no idea if that's the only purpose, but at least that makes sense to me.

As for precedence, that's still a mystery. About the only solid information I found about sources.list.d  was a 2003 developer argument about whether to change how precedence is handled. (Apparently the reverse of apt.conf.d.) I've no idea what's been decided since.

Since that was four years ago, sources.list.d really should have its own man page by now. That's a bit of an oops, and leads directly to asking what documentation is being used by the devs who use sources.list.d? There must be something, but i was unable to find it.

---

### Post by hyper_ch on 2007-10-23
it's not autoupdate... but because you have a seperate medibuntu.list you can just use the bash command they provide on their website to update the existing one.

---

