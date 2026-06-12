---
title: "sudo chown Permission denied???"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by D_Ronin on 2007-06-30
Greetings,

Here is the situation... I have two computers and I am trying to mount a folder via sshfs.

I followed the instructions on ubuntuguide and it did not work.  No biggie I can live with that for now.  What I find very annoying is that in the process of following those instructions, the folder which was destined to be linked had it's permissions changed.  Here is where I get confused.

My folder is now owned by the user root and the group root

Allright so I try to change the ownership by typing: **sudo chown dronin:dronin /home/dronin/remote_folder_name**

And I get a permission denied... Since when is sudo denied stuff?

My problem is probably something very simple but I am still too much of a noob to figure it out.

---

### Post by tgm4883 on 2007-06-30
Are you trying to change permissions on the local system or the remote system?

Perhaps your not in the sudo group on the remote system?

---

### Post by D_Ronin on 2007-06-30
I am trying to change the permission on the local system.

The folder that is locked is the folder I created locally in order to link to another folder on the remote system.

The link is not working since I cannot see the content of the folder on the remote system.

---

