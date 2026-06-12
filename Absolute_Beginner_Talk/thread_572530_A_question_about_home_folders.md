---
title: "A question about /home/ folders"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by CVNChaotic on 2007-10-10
I didnt want to highjack a similar thread, but if that would have been preferred please let me know.

A question was asked about sharing /home between different linux installs from a seperate partition. This made me think of Windows users on a network with their profiles being stored on the server. 

If there a way to move /home/%user% to a network share? Lets say I have several 7.04 installs on a network, same software etc. I log in on one machine and save something to my desktop, log off and get on my laptop later. I should then have what I saved. Roaming profiles as it were....

Is this possible?

I am fairly new to linux on the desktop, so maybe I am WAY off base...

---

### Post by Naatan on 2007-10-10
I know its possible, you'd simple mount the network share and set it as your homefolder,

the catch comes from having it mounted before you actually login.. and that's where my knowledge stops..

I'm 95% sure it's possible tho

---

### Post by Lord Illidan on 2007-10-10
> **Naatan said:**
> I know its possible, you'd simple mount the network share and set it as your homefolder,

the catch comes from having it mounted before you actually login.. and that's where my knowledge stops..

I'm 95% sure it's possible tho

Edit the /etc/fstab maybe?

I am not an expert on networks though, can't help that much either. Also, if you are using wifi, you might get problems, as network-manager requires you to login before you can access the wireless internet. Of course, a script could fix this issue.

---

### Post by red_Marvin on 2007-10-10
I guess that you could use nfs for that by setting up an nfs server and add/edit the correct line in /etc/fstab on the client.

---

### Post by Whiffle on 2007-10-10
My school does this with nfs.  Works great.  The home directories are all on a central nfs server, and each of the systems mounts that share for the /home directories.  Its totally transparent to the user  and is wonderful because all your settings get saved no matter which computer you log in to.  Way better than the way they have windows setup, where internet explorer asks all of its annoying questions every time because things don't get saved from  session to session.

Theres some good ubuntu nfs tutorials around here that would be helpful.

---

### Post by thisllub on 2007-10-10
I have had the same home partition on this computer for about 2 years. It has survives at least 6 medium term changes of distro and another dozen trials.

---

### Post by bodhi.zazen on 2007-10-10
nfs ftw :lolflag:

The only potential problem with a shared /home across distros is that the config files, or .gnome can sometimes conflict. Although rare, it can be problematic.

I suggest a nfs /data partition mounted in /mnt or /media leting each distro have it's own /home for config files.

You can link from /home to /data if you like.

---

### Post by CVNChaotic on 2007-10-10
I'm not to concerned about different distos. I would have the same disto/version on the entire network. 

I'll have a look at the nfs tutorials and see what I can come up with. Thanks for the replies!

---

### Post by Golyadkin on 2007-10-10
Just hopping in here to say thanks for the idea. I like the idea of operating independent home directories. However, it still feels a bit fragile though, I will read more about it.

---

### Post by CVNChaotic on 2007-10-10
I have several computers around the house, many more than any sane person should have I reckon....oh well.

When my wife logs in to anything other than her computer she gripes about not "having her stuff". When I ran an Domain on win2k3 with roaming profiles she loved it and got used to it. 

From some searching it looked like a pipe dream on linux, but I think I was asking the wrong questions. 

When I get her back on ubuntu I would love to give her flexibility on the network again. Not to mention I hate losing functionality, which is what I have done just to get out from under M$.

---

### Post by CVNChaotic on 2007-10-10
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

This looks like the ticket. Thanks everyone!

---

### Post by jfinkels on 2007-10-10
> **CVNChaotic said:**
> 

When my wife logs in to anything other than her computer she gripes about not "having her stuff". When I ran an Domain on win2k3 with roaming profiles she loved it and got used to it. 


You could set up a thin client server and thin client terminals if you've got a bunch of old not-so-powerful computers. That's obviously significantly more complex than necessary, though.

---

