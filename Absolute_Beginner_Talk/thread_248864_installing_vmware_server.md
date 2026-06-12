---
title: "installing vmware server"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by j0eb0b on 2006-09-01
I just downloaded and extracted vmware server to my desktop.  I tried to run a .exe called vmware-install.pl from terminal using "sudo aptitude vmware-install.pl" and was prompted for my password.  I then got the error "this aptitude does not have Super Cow Powers".  This is almost the coolest error message i have ever gotten.  How can I get Super Cow Powers and install vmware server?

Thanks,
Joe

---

### Post by NetworkGuy on 2006-09-01
Just type sudo ./vmware-install.pl to start the install.

---

### Post by j0eb0b on 2006-09-01
> **NetworkGuy said:**
> Just type sudo ./vmware-install.pl to start the install.

I loved the error message and thats why i made the post.  There is a little more to installing VMware than the command you stated (although it is a correct command).  Following is the tutorial I found that got me working.

[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

Thanks,
Joe

---

### Post by ebtech on 2006-09-01
I tried everything in the tutorial and it was working fine till I tried to run the install file, I type sudo ./vmware-install.pl and it asks for password, i give it and it says command not found.  I try just ./vmware-install.pl and it says permission denied.  what did I do wrong???

---

### Post by chrisccoulson on 2006-09-02
Is it marked as executable? Try:

```
chmod +x vmware-install.pl
```

---

### Post by j0eb0b on 2006-09-02
> **ebtech said:**
> I tried everything in the tutorial and it was working fine till I tried to run the install file, I type sudo ./vmware-install.pl and it asks for password, i give it and it says command not found.  I try just ./vmware-install.pl and it says permission denied.  what did I do wrong???

Did you paste the password from the VMware registration response?

---

### Post by bluevoodoo1 on 2006-09-02
> **ebtech said:**
> I tried everything in the tutorial and it was working fine till I tried to run the install file, I type sudo ./vmware-install.pl and it asks for password, i give it and it says command not found.  I try just ./vmware-install.pl and it says permission denied.  what did I do wrong???

Is the file on your desktop?
```
cd ~/Desktop
```

before...
```
sudo ./vmware-install.pl
```

---

### Post by j0eb0b on 2006-09-02
I just reread your problem and my post.  I think your problem is that you have not navigated to the directory where vmware-server-distrib is located.  In my case i extracted everything to my desktop.  So I had to navigate from Root to Desktop to vmware-server-distrib.  Your terminal session should look like this (depending on where you extracted vmware):

j0eb0b@ubuntu:~$ sudo su
root@ubuntu:/home/j0eb0b# cd Desktop
root@ubuntu:/home/j0eb0b/Desktop# cd vmware-server-distrib
root@ubuntu:/home/j0eb0b/Desktop/vmware-server-distrib# sudo ./vmware-install.pl

Hope this helps.

---

### Post by phenest on 2007-03-03
I'm having the same problem. I've had this installed before with no problems. I have just downloaded the latest version and extracted but all I get is: Permission denied. Also, it doesn't ask for a password neither.

---

