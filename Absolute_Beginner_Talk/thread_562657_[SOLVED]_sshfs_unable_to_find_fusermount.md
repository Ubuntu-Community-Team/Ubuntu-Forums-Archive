---
title: "[SOLVED] sshfs unable to find fusermount"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by Scotty562 on 2007-09-29
I followed the guide to setup sshfs here: [http://ubuntuforums.org/showthread.php?t=275856&highlight=ssh+mount+drive](http://ubuntuforums.org/showthread.php?t=275856&highlight=ssh+mount+drive) .

Everything works great as long as I am root.

This command is suppose to fix the issue:
sudo chmod +x /usr/bin/fusermount

However I do not have a fusermount in that directory. I'm running gutsy if it matters... Maybe it's just in a different location?

---

### Post by bodhi.zazen on 2007-09-29
sshfs works fine for me in gutsy without that command (sudo chmod +x /usr/bin/fusermount)

1. make sure your user can ssh into the server

2. make sure your user is a member of fuse. Remember you need to log out an back in for this change to take effect.

---

### Post by Scotty562 on 2007-09-29
> **bodhi.zazen said:**
> sshfs works fine for me in gutsy without that command (sudo chmod +x /usr/bin/fusermount)

1. make sure your user can ssh into the server

2. make sure your user is a member of fuse. Remember you need to log out an back in for this change to take effect.

I can ssh to the server without any issues.

I did the member part of the howto and it appears to be successful. I rebooted a few times since then too. It's not that it isn't working, it's that I can't access my files as a regular user.

---

### Post by bodhi.zazen on 2007-09-29
I am sorry, but I can not tell from your description what the problem is.

Are you having problems mounting the directory as a user ?

Make sure it is not mounted as root first ...

Then, is there an error message when you, as a user :

sshfs user@<ip>:/directory_to_mount /mount/point

Or, if you can mount the directory are you having problems with permissions (access) to the contents ?

---

### Post by Scotty562 on 2007-09-29
> **bodhi.zazen said:**
> I am sorry, but I can not tell from your description what the problem is.

Are you having problems mounting the directory as a user ?

Make sure it is not mounted as root first ...

Then, is there an error message when you, as a user :

sshfs user@<ip>:/directory_to_mount /mount/point

Or, if you can mount the directory are you having problems with permissions (access) to the contents ?

Sorry for the confusion. when I do 
sshfs user@<ip>:/directory_to_mount /mount/point it works just fine as long as I'm root. I can browse my files and do whatever I like. If I run rhythmbox as root and I even play my music through it (which is what I'm after :)).

What I want to be able to do is run rhythmbox as a normal user and be able to have access to the sshfs files I'm mounting. So yes, I am having problems mounting the directory as a user.

When you say make sure it's not mounted by root, what do you mean by that?

When I try and access the directory as a user I get a permission denied error.

Like I said, if I run everything as root it works just the way it should. Obviously I'd like to not have to do this :).

---

### Post by bodhi.zazen on 2007-09-29
Well, mounting with sshfs is strange ...

If you mounted as root, unmount the directory and re-try mounting as a user. You can unmount the ssh share with "sudo killall ssh" 

Now make sure the directory was unmounted.

Now try mounting as a user.

I hope that works ...

---

### Post by Scotty562 on 2007-09-29
> **bodhi.zazen said:**
> Well, mounting with sshfs is strange ...

If you mounted as root, unmount the directory and re-try mounting as a user. You can unmount the ssh share with "sudo killall ssh" 

Now make sure the directory was unmounted.

Now try mounting as a user.

I hope that works ...

Wow... heh, I can't believe I didn't think of that. Thanks for the tip. I must have thought sshfs  only worked as root. Everything is working great now!

---

