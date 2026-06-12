---
title: "mount local directories after ssh into remote machine"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by tramir on 2007-08-11
I'm in a bit of pickle and I could really use some help. Here's the problem: my university provides on its network some applications that I desperately need. I can ssh into the network and run them remotely, but my space on the server is limited (and not enough, I have some really large data files). 

As far as I can tell, there could be two solutions:

1. I could mount the remote directory using sshfs and do everything locally. The problem is that the university runs a SPARC network, while I have an Intel machine. This means that I couldn't find a way to run the applications locally. Unless somebody can tell me of a way to run SPARC applications on an Intel x86-32...

2. I could mount the local folders after logging in the university network so that I have access from there to my HD. But I couldn't find a way to do that, and sshfs is not installed on the network (and, of course, I can't install anything on the network).

Does anybody have any ideas on how to get (1) or (2) to work, or if there's any other way to pull this through? Any help would be more than appreciated...

---

### Post by kidders on 2007-08-12
Hi there,

I'm afraid neither of these options seems possible, at first glance. #1 is certainly a non-runner. As for #2, I would be frankly stunned if the security restrictions in place on a public access University server were naive enough to allow unprivileged users to mount filesystems.

It's worth noting though, that you may have access to more disk space than you think. You should check out what kind of temporary storage is available to you, although you would need to bear in mind that your sysadmins may react harshly if you use an "unfair" amount of it. Also, it may be the case that another user could be willing to "lend" you some of his.

It might also be worth checking whether someone with root privileges would be willing to give you special consideration ... perhaps a temporarily extended quota? And you never know ... someone might be willing to mount one of your local filesystems into your remote home directory for you, if you draw his attention to the existence of mount options like "noexec", "nodev", "nosuid", and so on, which would limit their exposure to security issues.

May I ask what kinds of applications you're running? Are you sure there would be no way to set them up locally, on your own box? It may, for instance, be the case that you simply wouldn't have access to sufficient processing power, or can't do so for some other reason, but I thought I'd at least ask.

---

### Post by tramir on 2007-08-12
Thanks for the reply, kidders! I'm trying to use some commercial applications, like SAS (a statistical program), with data files larger than 100MB, which is my quota on the server. So there's not even the question of temporary space yet... The problem is not with processing power, but with the license - I don't have it, and the university only seems to provide it on their network. I don't think there's any way to "set it up locally," or at least not that I know of... Anyway, if you can think of anything, I would really appreciate any idea. And thanks again...

---

### Post by kidders on 2007-08-12
Welcome to the forum by the way!

> **tramir said:**
> I'm trying to use some commercial applications, like SASDamn. I suspected there'd be a good reason you *needed* to involve the SPARC box. You may have already done so, but you should check the server's filesystem structure. Quite often, in my experience, /tmp (and other temporary storage locations) tend to be on different devices than the core system, home directories, and so on ... which may impact your quota entitlements.

I'm only vaguely familiar with SAS ... which is to say I know of its existence, but not a whole lot else. Does it have the ability to access data using internal implementations of protocols like HTTP? OpenOffice, for example, can open documents over a variety of protocols ... in the unlikely event that SAS can do anything similar, that would be a godsend.

I suspect that any solution that involves typing the word "mount" on the server will fail. I'm racking my brains for an alternative, but I'm afraid I've more or less drawn a blank. :-(

**Edit:** Can you by any chance mount Samba shares on the SPARC box? I once used a university Sun box that (perhaps unintentionally) allowed unprivileged users to do so.

---

### Post by olejorgen on 2007-08-13
Can the programs read from stdin? If that's the case you could do something like this:
On remote machine:
```

ssh <user>@<local machine> "cat <file_needed>" | <important program> <option to read from stdin>

```
You might be able to do something with fifos too (?)

This requires that the application only read the file sequential qith no seeking.

---

