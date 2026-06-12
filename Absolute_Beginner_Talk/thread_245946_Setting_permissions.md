---
title: "Setting permissions"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by Mcavity on 2006-08-28
Let me state whea I have done and where I'm stuck and maybe someone will point to what I'm missing. 

I installed a new hard drive into my system.
I used gparted to format the drive [ext3] 
I then used Disk manager to mount the drive to /home/mike/data

However I cannot write to this drive. Permissions are set so only root can write to ../data. How can I change this? and is there no way to do it without having to drop to a terminal window?

---

### Post by aysiu on 2006-08-28
One of these should help:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by taurus on 2006-08-28
Why not mount it thru /etc/fstab.  Edit /etc/fstab as

```
gksudo gedit /etc/fstab
```
and add this line to the end of it, assuming the new harddrive is /dev/hdb1...

```

/dev/hdb1   /home/mike/data   ext3   defaults   0   2

```
Then, unmount it and mount it again and see what happens.

```

sudo umount /home/mike/data
sudo mount -a

```

---

### Post by kinematic on 2006-08-28
hmmmm....same post appears twice.

---

### Post by kinematic on 2006-08-28
the easiest thing is:

sudo chown root:mike /home/mike/data

that set ownership to root and makes it a part of the group mike to wich you will belong or you can set ownership to mike by changing root to mike in that command.
next is:

sudo chmod 774 /home/mike/data

that lets root read/write/execute....group mike can read/write/execute and others can read.
and if you want to know more about permissions here's a good link
[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by Mcavity on 2006-08-28
Ok well so far no luck. I must be missing something
I think its a little sad that something that shoudl be so simple requires that I drop to the terminal. Ubunto is sooo close to desktop ready but something like this should not be a chore..

tried this
mike@mike-desktop:~$ sudo chown root:mike /home/mike/data
Password:
mike@mike-desktop:~$ sudo chmod 774 /home/mike/data
mike@mike-desktop:~$ sudo chmod 777 /home/mike/data

the permission have not changed though

---

### Post by kinematic on 2006-08-28
actually it doesn't require e terminal.....i just think it's easier and faster ;) 
 but since it didn't work open nautilus as root(gksudo nautilus)and change the permissions with the checkboxes.
and another thing....now that i think about it i'm not sure if you're automatically added to the group mike during installation because i really don't remember so you might want to check by going to system>aministration>users and groups.

---

### Post by annda on 2006-08-28
actually, "root:mike" means user=root, group=mike, so i think you shoud do it the other way round.

---

### Post by taurus on 2006-08-28
And what's wrong with the "mike:mike" option then???

---

### Post by kinematic on 2006-08-28
> **annda said:**
> actually, "root:mike" means user=root, group=mike

that's what i said.....owner is user root and it belongs to group mike.
and as a fellow forum member pointed out to me yesterday(bohdi something :rolleyes: )it's safer to make root the owner and set the rest of the permission with the use of groups.
that's why i also said
> sudo chmod 774 /home/mike/data
root can read/write/execute,group mike can read/write and execute and others can read.
but mike:mike also works

---

### Post by annda on 2006-08-28
sorry, i posted too hastily, without giving details on why i think the solution may not work.

you are absolutely right, kinematic, root ownership is a good thing. however, i think it might be better to set the group to admin, not user_name - only because it doesn't work for me, so i agree that it may not be a valid argument for other people. i have a group with the same name as my username, but for some reason i had to manually add myself to that group.

kinematic, you rightly pointed out the need to check user/group relations, but i skipped that step because i falsely assumed i'm a member of my own group.

sorry for the confusion. to others reading this, learn from my mistakes - try exactly what people suggest and don't jump to conclusions (like i did).

---

