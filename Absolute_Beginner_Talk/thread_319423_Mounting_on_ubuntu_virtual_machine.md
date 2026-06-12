---
title: "Mounting on ubuntu virtual machine"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by lance_klusener on 2006-12-15
Hello guys , 


I have ubuntu running as a virtual machine on 2 windows machine , now i want to mount the /home directory of one ubuntu onto other. I am trying to use the mount command . So how do i do it , since the attempts uptil now have been unsuccesful.

I assume that unix used NTFS to i tried the -t ntfs option . I have included the name of the host i am trying to mount in the /etc/hosts file.

---

### Post by Bachstelze on 2006-12-15
As you certainly know, VMWare stores the virtual disks of your virtual machines in .vmdk files on the host. Each .vmdk file represents a drive, so you certainly have two. You can either use the same virtual disk on your two virtual machines or - since you already crated them both - add, say, the virtual disk of vm #1 to vm #2, just like you would add the disk of one computer into another. To do that, your VM must be powered off, go to the VM Settings > Hardware tab, click the Add button.

---

### Post by lance_klusener on 2006-12-15
But the thing is i dont have enuff space to copy around the vmdk files , so the only solution according  to me is to mount . How do u specify a port number in a mount command

---

### Post by Bachstelze on 2006-12-15
You don't need to copy them. The second VM will use the existing file just the same way as the other. Just like you can have two disks in the same PC, the same VM can use several virtual disks. I don't know if two VMs can use the same virtual disk at the same time though, maybe you should create another virdtual disk where you will store all the suff you want to share between yout two VMs.

To use mount, you'l have to setup a NFS share before. You have to remmeber that a virtual machine behaves just the same as a real PC. Do you think a PC can mount a partition which is in another PC just by runing mount without setting up something else ?

---

### Post by lance_klusener on 2006-12-15
"To use mount, you'l have to setup a NFS share before." : _How do i do this_

 I am trying the mount -t ntfs command , i dont think this is the correct way though .

---

