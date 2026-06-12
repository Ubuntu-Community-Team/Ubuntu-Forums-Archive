---
title: "samba printer problems"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by snow_56767 on 2008-02-12
Hi,
   I've been trying to print on my friend's printer, but I'll start up Printing in 
System > Administration > Printing. And the first thing that pops up is a window saying:

  Password on LocalHost?

I enter my friend's password and root's and mine. It won't take any of them. To skip that step, I open Printing through the terminal as root. Thats really weird because it won't take root's password but when I'm root, It works! Weird. But then when I setup a printer, The terminal outputs everything and lists the error

```
No ID match for device smb://snowball:hailfire@COLLECTIVE/NYXBOX/EPSONonNyxBox
```

(My Friend is NyxBox) and when I try to print the computer thinks that I'm hooked directly
to the printer even though I hooked to a hub then the printer.
Help please! :cry:

---

### Post by bilge.tutak on 2008-02-15
I think the password it asks is not the OS user password you supplied. Actually it depends on the settings of Samba server. Try adding a user/create password for samba. 
```
$> smbpasswd -a "username"
```
will create a user with "username" and also will ask for the password. This should work for you.
If you already changed the samba server login type, this might not work.
Don't forget to restart Samba after adding the user.

---

### Post by snow_56767 on 2008-02-16
Hi,
   I did what you told me to do
```
$> smbpasswd -a "username"
```
And I got this output:
```
bash: -a: command not found
```
So I'm still stuck.

---

### Post by bilge.tutak on 2008-02-19
Do you have the smbpasswd command?

---

### Post by snow_56767 on 2008-02-22
I do have the smbpasswd command, its the only way I change my samba password.

---

### Post by bilge.tutak on 2008-02-28
Can you check your smbpassword options with
```
 smbpasswd --help
```
or something. I am not sure why its not accepting the command.

---

### Post by snow_56767 on 2008-05-10
Hi,
   For some reason when I upgraded to Hardy Heron, CUPS started to work. So now I am happy and bilge.tutak shouldn't have to try and solve my problem any more. Thanx Hardy Heron!

---

### Post by lerigan on 2008-05-10
Is it alright to upgrade from 7.10 to 8.04 directly, or is it better if you just format and install 8.04 from the ground up?

---

