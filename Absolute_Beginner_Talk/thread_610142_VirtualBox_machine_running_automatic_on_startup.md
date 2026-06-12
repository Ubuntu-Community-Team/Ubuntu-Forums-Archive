---
title: "VirtualBox machine running automatic on startup"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by micdhack on 2007-11-11
I ve create on ubuntu server feisty fawn a windows xp machine with virtualbox. I added my user to the vboxusers groups and runned this command:

```
VBoxManage startvm WindowsXPSP2 -type vrdp

```

All worked fine and my machine works perfectly which is a sock since a setuped it on my laptop first and then moved it on the  server.
Now what i want to do is make it run automatically on server boot so that i can ssh on my server and logout and the machine will be still be up and running.

Also i want to ask since this is a server and i have to run virtualbox machine with -vrdp parameter is rdp connections to the server on? Im using windows tools to connect to the server so i dont need rdp to be on.

---

### Post by Dr Small on 2007-11-11
> **micdhack said:**
> I ve create on ubuntu server feisty fawn a windows xp machine with virtualbox. I added my user to the vboxusers groups and runned this command:

```
VBoxManage startvm WindowsXPSP2 -type vrdp

```

All worked fine and my machine works perfectly which is a sock since a setuped it on my laptop first and then moved it on the  server.
Now what i want to do is make it run automatically on server boot so that i can ssh on my server and logout and the machine will be still be up and running.

Also i want to ask since this is a server and i have to run virtualbox machine with -vrdp parameter is rdp connections to the server on? Im using windows tools to connect to the server so i dont need rdp to be on.
Why not just setup a server without VirtualBox ??

---

### Post by micdhack on 2007-11-12
because i cant afford paying two servers one for windows and one for ubuntu and there are some applications that can only run on windows platform so i need to use the virtual machine for them.

---

