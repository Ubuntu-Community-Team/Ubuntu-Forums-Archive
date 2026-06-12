---
title: "How do you make a Script to Unmount drive on Log Off?"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by wtzup on 2007-08-02
No idea how to do this. I want to be able to have my Novel Client Drives unmounted when I log off an account. This will be used in a class room setting so thought maybe there is a way I can make a script to run a command to unmount a directory / Drive in "/home/user"  I have the novel Client working fine now.

Thanks for any help

James

---

### Post by milosz.galazka on 2007-08-02
If you are using bash, you can check it by using command

echo $0
/bin/bash

you can use  *~/.bash_logout* file to execute commands when login shell exits.

In any doubts check man page :)

---

### Post by wtzup on 2007-08-03
Great Looked at /etc/skel/.bash_logout but not sure how to unmount (umount) a directory. 

The Novel Client  (Spelled with only one l)  Mounts the home directory to /home/youruser/newmount

When you log off and back onto another the directory is still active. Though when the thin client reboots it no longer has the info. So looking at what options I can do in the .bash_logout file.

Thanks
James

---

### Post by misconfiguration on 2007-08-03
/.bash_logout is stored in your users' home dir.

Say my user is misconfig

vi /home/misconfig/.bash_logout
press i for insert mode
# ~/.bash_logout
umount /mnt/path/to/mount-point
clear

Cntrl-C
Shift + :
wq! <ENTER>

---

### Post by wtzup on 2007-08-03
Cool thanks for the fast reply. What is great about the Ubuntu community. 

Not sure if I can use umount. When I try I get   ... is not mounted (according to mtab)
The Linux NovelClient will pretend to mount it to the home directory. It does not add a real mount drive. Just a directory. So not sure how to remove it. Others have had problems with this.  I am using the bash_logout at /etc/skel as I will have upward to 50 users on this server. 

Back to searching.....

Thanks
James

---

### Post by milosz.galazka on 2007-08-04
Maybe you need to use  ncpumount?

See there [http://www.cendio.com/support/tag/novellfs.html](http://www.cendio.com/support/tag/novellfs.html)

---

