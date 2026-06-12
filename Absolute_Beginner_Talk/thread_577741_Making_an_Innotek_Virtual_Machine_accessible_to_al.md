---
title: "Making an Innotek Virtual Machine accessible to all users"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-10-16
I created a virtual machine. I want all users to be able to use it. When I create it under my user name it does not show up in my daughters VirtualBox menu. When I create it under the root account only people with root access can use it. Right now the VM is in my home folder under .VirtualBox.  I have all ready created the vboxusers group and added everyone to it. What steps do I have to take to make this VM accessible to all users?

---

### Post by bodhi.zazen on 2007-10-16
Try making a directory :

/usr/share/VirualMachines

owned by root.vboxusers

Put your machines there & see if it helps ...

You may need to set the ownership/permissions of the machines as well.

---

### Post by swoll1980 on 2007-10-16
Is it possible to turn a innotek VM into a bootable iso file and mount it with VirtualBox

---

### Post by bodhi.zazen on 2007-10-16
You could delete ~.virtuabox for user #2 and link to ~/.virtualbox for user #1

```
sudo rm -rf /home/user2/.virtualbox
sudo chown -r user1.vboxusers /home/user1/.virtualbox
sudo chmod -r 770 /home/user1/.virtualbox
sudo ln -s /home/user1/.virtualbox /home/user2/.virtualbox
```

This should create a shared pool of virtual machines :twisted:

---

