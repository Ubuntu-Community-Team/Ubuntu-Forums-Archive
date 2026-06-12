---
title: "Users, Groups and Permissions"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by namelessone on 2007-03-02
I like to play old DOS games, so I have created a folder in /usr/share that contains a bunch of them and their dosbox configuration files. From time to time I find a "new" dos game that has been released as freeware, and I add it to this folder. It got kinda of annoying typing sudo all the time while I was working in this directory, so I decided to mess with permissions a little on it (a good excuse to learn more about unix permissions).

First I added group dos, and changed the ownership of /usr/share/DOS and all the files in it to root:dos. I then added myself to group dos, and changed the permissions of /usr/share/DOS and everything in it to 775 (owner and group can rwx, others only read and execute). I thought this would allow me, and any other user in group dos, to have control of everything in this directory without having to type sudo all the time. But apparently I thought wrong. I tried editing one of the dosbox configuration files without sudo, but it didn't work.

In the graphical users and groups thingy and in /etc/group, it says that I am a part of group dos. When I type groups at the terminal, it doesn't list dos as one of the groups I am a part of.

Can anyone help me?

---

### Post by taurus on 2007-03-02
What are the outputs of these commands from a terminal?

```
id
cat /etc/group
ls -la /usr/share/DOS
```

---

### Post by namelessone on 2007-03-03
Well, for some reason, when I started up my computer today, it was all working the way I thought it should work. So I don't know why it wasn't working before.

---

