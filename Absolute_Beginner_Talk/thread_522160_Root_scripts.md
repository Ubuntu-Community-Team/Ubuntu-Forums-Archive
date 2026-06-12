---
title: "Root scripts"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by jonyboy1000 on 2007-08-10
Hi all,

This script logs in as root and changes the permissions of someone elses files.

But once the script runs su i have to type Exit in the command line and then it will run the rest of the script as not root.

I was wondering how to make a script log in as root and then run run the rest of the commands.



```
#/bin/bash
su                                                               # Script stops here
chmod 777 -R /home/jonathan           # I type exit in the terminal and script resumes
exit                                                            # Script cant execute previous command
```

---

### Post by 5-HT on 2007-08-10
why not just run the script as root and take out the su?

---

### Post by asmoore82 on 2007-08-10
a recursive chmod 777 is a very bad idea ... 7 = read,write AND execute
surely you have some files that aren't executables.

---

### Post by Inxsible on 2007-08-10
> **jonyboy1000 said:**
> Hi all,

This script logs in as root and changes the permissions of someone elses files.

But once the script runs su i have to type Exit in the command line and then it will run the rest of the script as not root.

I was wondering how to make a script log in as root and then run run the rest of the commands.



```
#/bin/bash
su                                                               # Script stops here
chmod 777 -R /home/jonathan           # I type exit in the terminal and script resumes
exit                                                            # Script cant execute previous command
```

When you type in su....it expects the root password from you. When you don't give that password and simply exit, it runs the script as non root. Seems logical to me.

BTW: 
>  This script logs in as root and changes the permissions of someone elses files. Does the "someone else" know you are doing this ? ;)

If not, that would amount to hacking and being unethical :)

---

### Post by asmoore82 on 2007-08-10
> **jonyboy1000 said:**
> This script logs in as root and changes the permissions of someone elses files.


Even WORSE!!

you don't want all of his files to become executable by everyone!!

i think you may be looking for something like...

```
chmod -R +rw [files]
```

---

### Post by jw5801 on 2007-08-10
"su" defaults to the root account and asks for a password for it. Since the root account is disabled by default, this password does not exist therefore an authentication failure is occurring. Try "sudo -s" as this will let you execute all following commands as root.

But, as is stated above, making all files in a directory, especially one such as your home directory, executable as a normal user is really not the best idea.

---

