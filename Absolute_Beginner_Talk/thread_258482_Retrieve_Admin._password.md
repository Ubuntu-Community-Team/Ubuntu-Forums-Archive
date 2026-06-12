---
title: "Retrieve Admin. password"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by Sundance on 2006-09-16
I just installed Ubuntu for the first time. I seem to have forgotten my admin. password or mistyped it and I can not log in as admin. How do I retrieve the password or change it?

Thanks,

Steve #-o

---

### Post by jpkotta on 2006-09-16
It is impossible to retreive the password.  You can change it by booting in "recovery mode" and doing ```
passwd
```

---

### Post by bodhi.zazen on 2006-09-16
> **Sundance said:**
> I just installed Ubuntu for the first time. I seem to have forgotten my admin. password or mistyped it and I can not log in as admin. How do I retrieve the password or change it?

Thanks,

Steve #-o

Ubuntu uses sudo rather then su.

Ex sudo <command>

Enter your log in password (you will not see text on screen as you type your PW).

If that fails (or if you like) you can set the root PW with ```
sudo passwd
```
Thus you do not need to re-boot to rescue mode.

HTH

---

### Post by aysiu on 2006-09-16
Read these two links:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Pumm4 on 2006-09-16
If you are using **LILO **(For GUI press *Ctrl-x* to exit the graphical screen and go to the **boot:** prompt). Now enter:
```
linux single
``` This will make you the "root" user without asking for a password. Once the system has booted, you can change the root password using the password command:
```
passwd
``` 
In GRUB is similar. Press 'e' at the GRUB prompt to select boot parameters. Select the line for the kernel you want to boot, and go to the end of it. Add "single" as a separate word, and then press ENTER to exit the edit mode. Once back at the GRUB screen, press "b" to boot into single user mode.

---

### Post by packhater on 2006-09-22
This does not seem to work. I am in the same boat! I don't know what happened but I installed it using dave and dave as the un and pw but it wont accept it. I tried using the above command and it wont work. In the red box it says Ubuntu which I think is the name of my install but I cannot use this command. I thik I may need to re install!

---

