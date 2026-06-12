---
title: "Installing Samba"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by bkb3 on 2007-08-08
I'm brand new to Linux/Ubuntu in the last week.  So far (once I got my wireless drivers up) it looks very good.  I want to look at file sharing on my home peer-to-peer network (two Ubuntu/XP dual boot systems connected wirelessly and a wired W2000 Pro system) and think I made a mistake.  I got printers shared fine.  When I went to share a directory very late last night, I selected NFS but not SMB on one box.  It loaded the service fine but I now realize I'd like to add the SMB (Samba) piece to simplify sharing.  It no longer offers the option to set it up.  I've tried the Synaptic Package Manager but it doesn't find SMB or Samba or . . . .

What I need to be able to do is share on a mixed Windows / Ubuntu network regardless of which OS the two dual boot systems are running at a given point.  

I know there are other solutions but I'd really like to start with Samba.

Thanks.

---

### Post by finer recliner on 2007-08-08
check out this tutorial:
[https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=(samba](https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=(samba))

---

### Post by bkb3 on 2007-08-08
Thanks.  That did it.  The problem I'm having with the forums is simple information overload.

fyi, I was trying to use the the Synaptic package manager and couldn't find a Samba or smb package to install.  apt-get smbfs did the trick (from the tutorial).

---

### Post by dhtseany on 2007-08-08
If I'm not mistaken the way to install samba (from the CLI) is:

```

$sudo apt-get install samba

```

Sorry if that doesn't help, just trying to give you an answer.

Sean

---

