---
title: "Problem with additional hard drive"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by Over the hill on 2008-03-02
Hello

I have recently installed an additional 70GB hard drive to my Ubunto 7.10 system.
The installation seems to have gone OK , the drive is mounted to 'Media' and I am able to back up various folders and files to this drive. 

I have set the permissions and I can write to it OK but I cannot delete a file or directory (or create a directory)  on this drive by right  clicking on it. (The text  'Move to the deleted files folder' is greyed out.) I have to go into 'terminal' and do it manually.

I'm sure it must be something to do with 'permissions' but I just can't see it.

Any ideas.

---

### Post by pdub on 2008-03-02
I have a similar setup, my drive is mounted in /media/data. What I did was take ownership of the mount, like this.

```
sudo chown my_user_name /media/data -R
```

Put your username where is says my_user_name and your mount point.

---

### Post by logos34 on 2008-03-02
> **Over the hill said:**
> Hello

I have recently installed an additional 70GB hard drive to my Ubunto 7.10 system.
The installation seems to have gone OK , the drive is mounted to 'Media' and I am able to back up various folders and files to this drive. 

I have set the permissions and I can write to it OK but I cannot delete a file or directory (or create a directory)  on this drive by right  clicking on it. (The text  'Move to the deleted files folder' is greyed out.) I have to go into 'terminal' and do it manually.

I'm sure it must be something to do with 'permissions' but I just can't see it.

Any ideas.

You might want to follow [this guide.]("http://www.psychocats.net/ubuntu/mountlinux")

---

### Post by louieb on 2008-03-02
> **pdub said:**
> I have a similar setup, my drive is mounted in /media/data. What I did was take ownership of the mount, like this...

Thats one way to do it. The other is to change permissions.
Changing permissions is useful if you what to share the drive with more that one user. To give all users permission to do whatever they want :
```
sudo chmod 777 /media/data 
```Each user will still have ownership of any file they put on the drive.

---

### Post by Over the hill on 2008-03-02
Solved it !

Thanks for your help, Pdub, Logos34 and Louieb:)

---

