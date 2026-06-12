---
title: "Some totally newbie questions"
date: 2005-11-06
forum: Absolute Beginner Talk
---

### Post by spdfrk on 2005-11-06
Hi!
I'm very new to Kubuntu 5.10 and Linux in general, I have some general questions about the system.

First I've made 2 user accounts in Kubuntu, for me and my girlfriend. I've enabled both accounts to access everything, root etc. etc. We don't need any security at home. However, I can't access her account with an admin login but she can access both. Why is this? I even created my account first... in the OS setup.

Another question is about the Adept-updater. I've enabled universe, multiverse and some other respositories. Will this enable unstable updates in the updater? All of a sudden I could receive 100 more updates, but are they safe to use?

Third and final question:
Since I've just left windows behind me and is using MS word in my studies I have lots of .doc files on floppy. When I try to mount these discs they're unreadable. Is there a workaround for this? I really need to access those floppys. :eek: 

Thanks in advance!

---

### Post by Kyral on 2005-11-06
Well, the repo question is easy to answer. Main, Restricted, Universe, Multiverse, and Backports(Not open in Breezy ATM) are all official repos, and are quite safe. What are these other repos though?

---

### Post by spdfrk on 2005-11-06
Thanks for the quick response!
I think I've opened one called dapper too...

---

### Post by Kvark on 2005-11-06
Dapper is under development and will be finished in April next year. So right now it is an unstable experimental prototype.


The problem with the floppy is probably that the floppy has a Windows file system (either umsdos or vfat) that Ubuntu doesn't detect automatically.

Try mounting it by typing this command:
mount /dev/fd0

Or try to specify that it has the umsdos file system:
mount -t umsdos /dev/fd0

Otherwise it can have the vfat file system so try this too:
mount -t vfat /dev/fd0

When you try one of those commands you will notice if it works on that the floppy appears on the desktop when properly mounted.


Remember to unmount the floppy before taking it out when you are done. Either by right clicking on it and choose unmount or by typing "umount /dev/fd0" (yes, without n in umount) in a terminal.

---

### Post by Mustard on 2005-11-06
On the question of admin access, are you saying that you can't view/access the files in her $HOME account?  A more elaborate description of the issue would make it easier to determine what the issue is.

---

### Post by spdfrk on 2005-11-07
[QUOTE=Mustard]On the question of admin access, are you saying that you can't view/access the files in her $HOME account?  A more elaborate description of the issue would make it easier to determine what the issue is.[/QUOTE]

I can access her files, after making her home open to group accounts (using her login).
But I can't access/edit her account settings, she can access mine tho.

---

### Post by spdfrk on 2005-11-07
[QUOTE=Kvark]Dapper is under development and will be finished in April next year. So right now it is an unstable experimental prototype.[/QUOTE]

Thanks, I'm removing those lines then.


[QUOTE=Kvark]Try mounting it by typing this command:
mount /dev/fd0[/QUOTE]

Didn't work, file system unreadable.

[QUOTE=Kvark]Or try to specify that it has the umsdos file system:
mount -t umsdos /dev/fd0

Otherwise it can have the vfat file system so try this too:
mount -t vfat /dev/fd0[/QUOTE]

When I tried these two commands i just get a list of help commands... :confused:

---

### Post by Kvark on 2005-11-07
[QUOTE=spdfrk]Thanks, I'm removing those lines then.




Didn't work, file system unreadable.



When I tried these two commands i just get a list of help commands... :confused:[/QUOTE]
Ops, guess I shouldn't write forum posts at 2am, those two commands should be;
sudo mount -t msdos /dev/fd0 /media/floppy0
sudo mount -t vfat /dev/fd0 /media/floppy0

---

### Post by Mustard on 2005-11-07
[QUOTE=spdfrk]I can access her files, after making her home open to group accounts (using her login).
But I can't access/edit her account settings, she can access mine tho.[/QUOTE]

I'm guessing a bit here without having the computer in front of me, but at the moment I am thinking that your account doesn't have sudo privileges (superuser privileges).  The easiest way I can think to check this would be to do this from her account.

```
sudo cat /etc/sudoers  #display the output of the sudoers file in terminal
```

Within the sudoers file you should see an entry for 'root' and then either an entry for her username or %admin (a group known as admin).  Not being familiar with kubuntu I am not sure how you might easily remedy this using the gui interface, but it can certainly be done through the terminal quite easily.  The explanation might be lengthy though, so I'll wait to see if you can confirm this.

If I guessed wrong, you can ignore all this. :)

---

### Post by spdfrk on 2005-11-07
[QUOTE=Mustard]I'm guessing a bit here without having the computer in front of me, but at the moment I am thinking that your account doesn't have sudo privileges (superuser privileges).  The easiest way I can think to check this would be to do this from her account.

```
sudo cat /etc/sudoers  #display the output of the sudoers file in terminal
```

Within the sudoers file you should see an entry for 'root' and then either an entry for her username or %admin (a group known as admin).  Not being familiar with kubuntu I am not sure how you might easily remedy this using the gui interface, but it can certainly be done through the terminal quite easily.  The explanation might be lengthy though, so I'll wait to see if you can confirm this.

If I guessed wrong, you can ignore all this. :)[/QUOTE]

# User privilege specification
root    ALL=(ALL) ALL

This is what I get!

---

### Post by spdfrk on 2005-11-07
[QUOTE=Kvark]Ops, guess I shouldn't write forum posts at 2am, those two commands should be;
sudo mount -t msdos /dev/fd0 /media/floppy0
sudo mount -t vfat /dev/fd0 /media/floppy0[/QUOTE]

sudo mount -t msdos /dev/fd0 /media/floppy0 worked, thank you for the effort!  Now I can start solving all other problems! :-)

---

