---
title: "Locked my keys in my car?"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by visionthing on 2007-12-24
Hi
I did something stupid. In an attempt to test something I tried to add myself to the root group but forgot the -a option. So now that the only group I am in. And no admin permissions now to fix it by adding myself back to the admin group.

I did see a thread suggesting to boot through grub menu and then it will go to root prompt and it can be fixed from there. Now when I try that it asks for root password, which I don't know so I don't get anywhere this way. I think Ubuntu makes it a random password....

Any thoughts? I hope I am missing something simple

Thanks!!!

---

### Post by taurus on 2007-12-24
Boot into recovery mode from GRUB menu and at the prompt, try

```
adduser username admin
```
where username is your login name.  Then, reboot with

```
shutdown -r now
```

---

### Post by visionthing on 2007-12-24
Hi
I can't get that far. It I boot into recovery it asks "enter root password or control D to continue" I dont know what Ubuntu set the root password to. So I have to do a control D which just boots me into regular ubuntu

---

### Post by scizzo on 2007-12-24
You can't login with your normal user even?

I mean the first user that you created? Since that user should have sudo rights and you should be able to sudo to do stuff?

---

### Post by taurus on 2007-12-24
> **visionthing said:**
> Hi
I can't get that far. It I boot into recovery it asks "enter root password or control D to continue" I dont know what Ubuntu set the root password to. So I have to do a control D which just boots me into regular ubuntu

Did you create a password for root?

Otherwise, you have to boot from the LiveCD, mount your harddrive where / is, then edit /etc/group to add your username to groups adm & admin.

Assuming your / partition is /dev/sda1 on your harddrive, do these from the LiveCD.

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
gksudo gedit /mnt/ubuntu/etc/group
```

---

### Post by visionthing on 2007-12-24
Hi
I can login the normal screen as myself but I no longer have sudo rights. Presumably since I am not longer a part of the admin group.

I tried booting from live cd, but if I attempt to modify the etc/group file it says I do not have permission. And since I cannot run as root since I don't know the password lol......

It might be a reinstall which is not the end of the world. All a part of learning. (not using minus a bad. not setting the root password so I know it bad lol)

But open for any other ideas too

Thanks for the help! :-)

---

### Post by taurus on 2007-12-24
How did you edit /etc/group from the harddrive?  Did you run the command that I provided?

```
gksudo gedit /mnt/ubuntu/etc/group
```

---

### Post by SOULRiDER on 2007-12-24
I believe you need to add yourself to the wheel group.

---

### Post by visionthing on 2007-12-24
I did try this:
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hdb1 /mnt/ubuntu (hdb1 is name of the drive ubuntu is installed on on my pc)
gksudo gedit /mnt/ubuntu/etc/group

It opens a group file. But it not the one on my local Ubuntu install. Its like its a group file from the live CD or somewhere else. It did let me modify it. Of course I then went to the /etc/group file on my local install and opened it (read only) and the indeed the changes where not there.

---

### Post by taurus on 2007-12-24
Wait, you want to add yourself to the one on your harddrive, /mnt/ubuntu/etc/group, NOT on the LiveCD, /etc/group.  

What's the output of this command then?

```
cat /mnt/ubuntu/etc/group
```

---

### Post by visionthing on 2008-01-02
Thanks. Had to leave after that and do a quick fix so I ended up reinstalling. thanks though!

---

