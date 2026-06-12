---
title: "Connect to XP network share through SSH"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by ryanh on 2008-03-16
I've setup an ssh server on my office Windows XP machine and am ultimately using it for Unison file synchronization with my Ubuntu laptop.

I'm having a problem navigating to a network share in a gui window (Nautilus or Unison command line).


When I login to my ssh server in the terminal window I can switch to //server no problem.
```

ryan@RYAN-PC ~
$ cd //server/

ryan@RYAN-PC //server
$ 

```

I'm not sure how to switch to this folder in, say, Nautilus or in a profile setting to Unison.

It seems that Nautilus doesn't like double // in its location bar.

My instinct is to type this (which doesn't work...);
```
ssh://rhaanappel@group92.ath.cx//server
```

Any help is greatly appreciated!

---

### Post by finer recliner on 2008-03-16
try escaping the /s with a backslash (\) in front of it

```
ssh://rhaanappel@group92.ath.cx\/\/server
```

---

### Post by ryanh on 2008-03-16
Thanks for the tip, but this didn't work either.

---

### Post by kevdog on 2008-03-17
Why dont you mount the share to a local directory on the server so it would appear to be a local directory when in fact it was not??  If not try a symbolic link.

---

### Post by ryanh on 2008-03-17
The shares are mapped to a local drive letter on the server, however they don't show up in /cygdrive/ (only my c drive shows up).

I read somewhere in a post that cygwin won't show these drive letters, that you have to use the //server/sharedfolder method...

I'll look into symlinks, not sure how they work exactly.



Thanks for the advice!

---

### Post by kevdog on 2008-03-17
Can you describe your setup please, 

Cygwin, server type (OS), etc.

---

### Post by ryanh on 2008-03-17
Cygwin is installed on an XP Pro machine attached to a Small Business Server 2003 domain server.

Not sure what version Cygwin is, but I assume its the latest stable as I only downloaded it 2 days ago. The setup installer is 2.573.2.2

The domain server has a lot of the network files I want access to (//server). These network folders are "mapped network drives" on my XP machine, but as I said they don't show up in /cygdrive/

I'm connecting from my Ubuntu installation (7.10) and ultimately trying to get Unison up and going (I've done preliminary tests with usable folders and it works fine.)

---

### Post by ryanh on 2008-03-17
For some reason mapped network drives are now listed under /cygdrive

When I get back to my laptop I'll confirm access through Nautilus/Unison.

---

### Post by ryanh on 2008-03-17
My apologies... I misrepresented what I said in the last post.

I was able to access the network drives in the cygwin shell on my XP computer.

When I access the machine through SSH that I can't access these drives. This must be a limitation/setting of SSH, not Cygwin.

---

### Post by kevdog on 2008-03-17
How did you access the shares in cygwin?  What exactly did you type?  What are the permissions?

---

### Post by ryanh on 2008-03-18
To access the mapped network drive in cygwin I can just type

```
cd /cygdrive/g
```

This switches to the folder and I can do the "ls" command to show the drive contents.

When I try the same command under SSH I get the message "No such file or directory".


I'm not sure how to check the permissions of the folder... I wonder if this is a permission issue of the user that I'm logging into SSH as (a network administrator on the XP machine/domain).

---

