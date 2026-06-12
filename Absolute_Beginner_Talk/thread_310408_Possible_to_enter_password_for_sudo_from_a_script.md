---
title: "Possible to enter password for sudo from a script?"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by wrybread on 2006-12-01
I'm trying to write a shell script that invokes some commands as sudo, and I'd like to automate the password. I know I can do this by entering my username in the sudoers, but I'd rather do it just for this script.

Something like sudo -password "whatever" mkdir /usr/whatever

Is there some hidden switch for entering the password? I know the password is readable in plain text and all that, I'm not worried about it in this case.

Thanks for any help.

---

### Post by lloyd_b on 2006-12-01
AFAIK, there's no way to automate password entry in sudo.  I believe that this is an intentional security feature (basically, to prevent what you're trying to do).

Is there a reason why you can't run the shell script via sudo?  If you invoke the script as "sudo {script}", then all commands within the script will run with root permission.

If you just don't want to have to type the password (and you don't mind creating a security risk):

"sudo chown root {script}"
"sudo chmod +s {script}"

This will make the script "suid root", which means that the script will always run with root permissions, regardless of who runs it.  As mentioned above, THIS IS A SECURITY RISK - having ANY programs on a system set as "suid root" is generally a bad idea.  Use at your own risk!!!!

Lloyd B.

---

### Post by zigford on 2006-12-01
man sudoers

the sudoers file holds the configuration of sudo and can be configured to allow certain apps to run from sudo that won't ask for password

---

