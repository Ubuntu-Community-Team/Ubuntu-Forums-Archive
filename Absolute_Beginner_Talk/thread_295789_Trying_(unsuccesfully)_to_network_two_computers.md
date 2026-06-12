---
title: "Trying (unsuccesfully) to network two computers"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by Naegling23 on 2006-11-08
Ok, so I have successfully set up beryl to run on AIGX, have mythtv up and running great, but I have one problem that I cannot seem to fix.  I cannot manage to share files between two computers.  I have one running kubuntu and another ubuntu (both edgy).  All I want to do is share files in my home directory with the other computer.  Thats it, I dont need them to syncronize...yet anyway.  So how do I do this?  What debs do I need, I cant seem to get it to work with samba or the unix file sharing system.  Am I missing something?  Ive tried google, and searching the forums, and to no luck.  Can anyone walk me through sharing a folder on a network between two computers?  This should be a simple task, but it has proven to be anything but.

Thanks for the help.

---

### Post by chriscando on 2006-11-08
I think the best way is to go over the SSH protocol. To do this you would install the openssh-client and openssh-server packages. Then the program konqueror (package konqueror) is really nice since you can just type in the address bar sftp://ipaddress_of_other_computer and you can directly login and copy/paste files.

An even better solution with ssh is the package sshfs where you can mount a directory from one computer so it looks just like a folder on your local computer but it is really just the networked drive. If you want more info on how to do this let me know.

---

### Post by Naegling23 on 2006-11-08
thanks for the reply, as soon as I get home, Im going to try the ssh thing.  I like the sshfs, might try that one too.  Will there be any problems with permissions?  Will I have to give the guest user permissions, or can they log in with my username to the folders.  (its my wifes computer, so I dont care about sharing the username/password)

---

### Post by chriscando on 2006-11-08
When logging in over ssh you will have all the same permissions as the user you log in as. So anything thing that a user could normally do can be done remotely.

One thing I forgot to mention is that openssh-server and client needs to be installed on both computers.
```
sudo apt-get install openssh-client openssh-server
```

To test that its working, try logging in via ssh:
```
ssh user@ipaddress
```
If all goes well you will have a command prompt at the remote computer. You can even run applications from the other computer and have them display on your screen by using:
```
ssh -X user@ipaddress
```
then just type the command of any program you want to run.

---

### Post by balaram on 2006-11-08
I"m using Ubuntu 6.06 (Dapper) and I used the instructions from this website to set it up with 4 computers. It worked like a charm for me. One last thing, its even easier if you happen to have an old network hub and a couple of spare network cards, then you can avoid any possible conflicts with your internet connections, in otherwords leave your router out of it, it's easier but not necessary, you can go through your router if need be but for me at least it caused some IP problems. [http://users.bigpond.net.au/hermanzone/p11.htm](http://users.bigpond.net.au/hermanzone/p11.htm)

---

### Post by dmizer on 2006-11-09
if you just want to share files over your local network, there's no need to slow your connection down with encryption like ssh.  and samba is way painful to set up.  as long as both computers are linux, use nfs.  try the forth link in my sig to set up nfs.  took me all of 15 minutes of effortless configuration before i was able to share files at blazing speeds.

---

### Post by Naegling23 on 2006-11-14
Ive been following that guide for nfs all week, I cant seem to figure it out.  It shouldnt be hard, but Im just completely confused.  Neither computer wants to connect at all.
Im going to give the ssh a shot, sounds easy enough

---

### Post by dmizer on 2006-11-16
what kind of problems are you having? errors? what's confusing to you?

perhaps my post in this thread: [http://ubuntuforums.org/showthread.php?t=299373](http://ubuntuforums.org/showthread.php?t=299373) may clear a few things up for you?

ssh alone will not allow you to mount the share.  the way chriscando describes it, may look easy.  but that's not actually "sharing" the files.  it will only allow you to VIEW the files on the remote computer.  if you want to use the files on your local machine, you'll have to do one of the following:
1) mount the remote computer using sshfs and fuse (actually more difficult to configure than NFS) which won't allow you to automatically mount every time you boot
2) use another command to copy the file over the network using scp in order to get local access to it.

ssh is an extremely powerful tool, but if all you want to do is share files, ssh is not your answer unless you absolutely need an encrypted protocol.

---

