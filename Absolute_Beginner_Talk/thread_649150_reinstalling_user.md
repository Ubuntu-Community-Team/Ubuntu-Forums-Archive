---
title: "reinstalling user"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by jrev on 2007-12-24
Hi all,
I suppressed the admin right of my first user in ubuntu feisty 7.04
How do I give back this right to my user ?

When I reboot in recovery I am asked for the root password and if I give the sudo password of my first user I get :
Login incorrect

How do I know the root password ?

I probably have to modify a file in my system but which one ?

when I type " ***id my_user ***" I see my user is missing the 117 (admin) group

---

### Post by taurus on 2007-12-24
Did you create a password for root account?

Otherwise, you have to do it from a LiveCD.  Boot your machine with the LiveCD, mount the partitio of your harddrive where / is, then add your login name to group adm & admin in /etc/group of the harddrive.

---

### Post by jrev on 2007-12-24
> **taurus said:**
> Did you create a password for root account?

No I used the normal install

Otherwise, you have to do it from a LiveCD.  Boot your machine with the LiveCD, mount the partitio of your harddrive where / is, then add your login name to group adm & admin in /etc/group of the harddrive.

I booted from the knoppix 5.1.1 live CD and mounted the / 

But I don't know which file to modify to correct this 

the /etc/group file is OK but when I type 

***id my_user *** 

the group 117 (admin) is missing



Thanks for your detailed answer

---

### Post by taurus on 2007-12-24
Since you can't boot your machine to recovery mode, you have to modify /etc/group from the LiveCD.

Boot it with the LiveCD.  Then, open a terminal and run, assuming your harddrive where / is located is /dev/sda1.

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
gksudo gedit /mnt/ubuntu/etc/group
```
Now, add your login name to the end of groups adm & admin.  Save it and reboot.  See if you can run sudo now.

---

### Post by jrev on 2007-12-24
I didn't see there were two places to modify in /etc/group

the second place admin was empty 

I change it and check and be back 

Thanks That was it ! I now got access to the whole admin menu with synaptic 

I 'll note the end of the exercice (I did it on purpose without knowing the right answer )

problem solved

---

