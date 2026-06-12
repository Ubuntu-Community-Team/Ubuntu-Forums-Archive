---
title: "Installing Flash Plugin for Mozilla"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by stormblue on 2007-07-07
Hello,

I'm trying to install flash.  I found that flash is in the multiuniverse repo, and I have that repo enabled.  However after I've done an apt-get update and I try to install it using the command: ```
sudo apt-get install flashplayer-mozilla
```

It doesn't seem to work. And it says it can't find the package.  Any ideas?

Thanks in advance!

---

### Post by Inxsible on 2007-07-07
What Ubuntu are you using?

64 bit or 32 bit ?

and what doesnt seem to work?

---

### Post by Inxsible on 2007-07-07
Try using this:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by stormblue on 2007-07-07
I'm using 64 bit linux.

Here is what I get when I use the command you asked for:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate
```



It appears as though my sources.list is messed up or not being read correctly.  When I run what I thought was right which was:
```

sudo apt-get install flashplayer-mozilla
```

I get: 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplayer-mozilla
```

---

### Post by Inxsible on 2007-07-07
flash player doesnt support a 64 bit architecture....

you will have to install the 32 bit flash on it. Its NOT trivial. There is a HOWTO here on the forums. Let me see if i can find it for you.

---

### Post by stormblue on 2007-07-07
I think this is what I need:

[http://ubuntuforums.org/showthread.php?t=202537&highlight=32+bit+flash+for+64](http://ubuntuforums.org/showthread.php?t=202537&highlight=32+bit+flash+for+64)

Hopefully, this will get me in the write direction.

---

### Post by Inxsible on 2007-07-07
Check this [link]("http://ubuntuforums.org/showthread.php?t=202537&highlight=install+flash+64+bit"). Its pretty detailed on what steps you need to follow.


EDIT : Too late :rolleyes:

---

### Post by stormblue on 2007-07-07
Worked like a Charm!

Thanks.  This issue is resolved.

---

