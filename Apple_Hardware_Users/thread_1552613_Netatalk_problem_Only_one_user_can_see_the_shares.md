---
title: "Netatalk problem: Only one user can see the shares"
date: 2010-08-13
forum: Apple Hardware Users
---

### Post by Gantlett on 2010-08-13
Hello everyone.

I'm using a Ubuntu Desktop 10.04 32-bit machine as my file server. It is sharing a few folders stored on a USB NTFS drive using Netatalk. The client machine is running MacOS 10.6.4.

I have only one user on the Ubuntu machine, but the Mac machine has two users. I wish to share the same network share between the two Mac users, while both are logged in (they switch between one another without logging the other one out).

I created a login item on both Mac user accounts to automount the Ubuntu shared folder and used the same Ubuntu user account for authentication on both Mac accounts.

This is the problem:
When the first Mac user logs in, the shared folder automatically mounts with no problems. However, when the second user switches to their account (without logging out the first user) the automount mounts the folder with a red "No Access" sign on the folder. The only way to resolve it is to eject the mount and manually remount.

This is not the end of the world, but I would like to resolve this issue if possible, so that the users get a smoother experience.

The way I tried to resolve this:
I thought that maybe Netatalk does not allow the same user to connect more than once from the same IP, so I set up an additional user on the Ubuntu machine. However, when I connect to the Ubuntu server using the new user for authentication, the only share available for the user is their home folder. The other shares are not available.

I therefore tried to configure permissions using the AppleVolumes.default by explicitly giving all users the "allow" permission for all shares and restarting the Netatalk service, however the new user still has access to nothing but their home folder.

How can I share the same shared folder between multiple users?

Thanks in advance.

---

### Post by Gantlett on 2010-08-18
Guys if anyone can help me with this one I'd greatly appreciate it. 
I tried sharing the folder using Samba but I'm experiencing a similar issue where only one user has access to the shares.

Please help! ](*,)

---

### Post by linuxopjemac on 2010-08-18
I would try here:
[http://sourceforge.net/projects/netatalk/forums/forum/26981](http://sourceforge.net/projects/netatalk/forums/forum/26981)

---

### Post by tiresia on 2010-08-18
> **Gantlett said:**
> I tried sharing the folder using Samba but I'm experiencing a similar issue where only one user has access to the shares.

This means that it should be a network configuration issue. Do you experience this problem with the same user, or just with the second one you log in?

---

### Post by Gantlett on 2010-08-20
Allow me to clarify:

I'm managing the system with the user that was created during the Ubuntu system install process. This user (let's call it user1) can share and view shares with no problems, SMB and AFP.

However, the additional user I've added, user2, cannot view any AFP shares other than their own home folder. Thanks.

---

### Post by BrutalSpoon on 2010-10-12
I've got this exact same problem. I suspect that if I were to log into "user2"'s account on the ubuntu side and to mount the drives there then user2 would be able to see all the folders but user1 wouldn't.

Did anybody else figure this out?

---

### Post by Rick Myers on 2011-06-02
Sorry to be un-timely here, but I may be able to offer some help for future reference. SMB and AFP being totally different, I can "see" a common thread that may be a source of the issue - group membership.

Both protocols need to authorize users for access (obviously). From what I've seen in this thread it sounds as though the user/group ownership conflicts. We're running a production 10.04.2 server with both protocols.

In our situation, to minimize permission issues, all shared files and directories are owned by a "common" user and the group "users". In our case each user is a member of the "users" group. File permissions are 0775 on everything in the shares.

To maintain consistency of permissions and group ownership we've done the following:

Netatalk AppleVolumes.default entry;
/directory/to/share "ShareName"  allow:@users rwlist:@users options:usedots,upriv perm:0775 veto:/lo

Samba Share;
Our general section includes "security = user".
[ShareName]
	writable = yes
	path = /directory/to/share
	force group = users
	guest ok = no
	create mask = 0775
	force user = user1
	comment = Shared Files
	directory mask = 0775

As you can see the above configuration creates new files/directories forcing the group in both protocols to be "users". Creation/perm mask is 0775. In the case of Netatalk only members of the "users" group may access. Prior to adding "allow:@users rwlist:@users" we had similar odd behaviour to what's been described previously in this thread.

Using the above config we provide common share points to Mac (AFP or SMB) and Windows (SMB) users.

One caveat with the config is file naming compatiblity. But that's a discussion for another thread.

HTH

---

### Post by Gantlett on 2011-06-02
Guys thanks for the help. 

I have since moved to Samba and never looked back! 

With Samba this issue doesn't exist. In fact, Samba works flawlessly. The Samba shares are available with no problems on the Mac when both users are logged in. They also work on a media player and on another Windows machine with two local user accounts for the same two people that use the Mac.

---

