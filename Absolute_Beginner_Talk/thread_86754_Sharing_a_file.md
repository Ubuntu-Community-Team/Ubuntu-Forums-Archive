---
title: "Sharing a file?"
date: 2005-11-06
forum: Absolute Beginner Talk
---

### Post by Darrin on 2005-11-06
I installed Kmymoney. I have two user accounts on ubuntu. My wife and I. I saved my Kmymoney data in **/home/darrin/Kmymoney**. I wish to be able to share this file with both of us and both have the ability to read and write to it. I right clicked on the Kmymoney folder and in properties changed the permissions of others to read,write,execute. When I log into her name It doesnt seem to work. Whats the best way to get this working?
Thanks

---

### Post by mlomker on 2005-11-06
> changed the permissions of others to read,write,execute. When I log into her name It doesnt seem to work.

Can't open the file or can't even see it?  It seems to me like that should work.  You could try creating a new directory at /home/shared or something and then setting the permissions on it.

You could post the output of **ls -l filename**.

```

mlomker@mlomkernote:/home/src$ ls -l get*
-rwxr-xr-x   1 mlomker mlomker 13599 2005-10-24 16:43 get-amarok-svn.sh

```

---

### Post by Darrin on 2005-11-06
[QUOTE=mlomker]Can't open the file or can't even see it?  It seems to me like that should work.  You could try creating a new directory at /home/shared or something and then setting the permissions on it.

You could post the output of **ls -l filename**.
[/QUOTE]

In my wifes login I can see the file but it doesnt seem to import it. It says something like the directory doesnt exist. But its there.
I need a little more help with post the output of the  file you desire. Im not sure how to read that code you posted. Sorry, Im still a newbie here. :???:

---

### Post by mlomker on 2005-11-06
I just wanted to verify the permissions that you set.  We tend to do things by the command line because swapping pictures of the graphical tools isn't too practical.  If you did set the permissions like you stated then it should have worked.

I'm not familiar with that application, so without an error message I'm not sure why it wouldn't import.  It might not be a permissions problem.

There are some good tutorial websites around.  [Here's one.]("http://linuxcommand.org")

---

### Post by Darrin on 2005-11-06
Heres some things I noticed. Even though I set the permissions for /home/darrin/Kmymoney for others to 777. My home folder itself for others is set at 700. Could this be the issue? When I tried to change others to all permissions I get [this issue]("http://ubuntuforums.org/showthread.php?p=470965#post470965"), which I have fixed. Any ideas?

---

### Post by mlomker on 2005-11-06
Okay.  I created a test user so that I could try this out.  Yes, you need to change the permissions on your home folder as well.  If you don't care about security then this would work while logged in as you:

```

chmod 777 ~

```

---

