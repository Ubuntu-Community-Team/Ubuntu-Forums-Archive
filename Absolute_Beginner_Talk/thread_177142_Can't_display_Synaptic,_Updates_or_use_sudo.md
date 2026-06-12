---
title: "Can't display Synaptic, Updates or use sudo"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by YesNoYes on 2006-05-15
Hi everyone.  Sorry if this is the n00best of n00b questions.  When I try to install updates, I am prompted to enter my password and then... nothing happens.  

Similarly, at the terminal, when I enter a sudo command and then my password when prompted, it just goes back to the prompt.  When I try something like **pwd** or **ls**, it works fine.  

When I try to open Synaptic, literally nothing happens when i click on it.  I just went and changed my user password, just in case, and it had no effect.  My root password worked when I did that.

Can anybody help me?

Thanks!

---

### Post by cgjones on 2006-05-15
Have you enabled the root account? Which password are you using with sudo, Synaptic, and Updates?

---

### Post by YesNoYes on 2006-05-15
Here's an example of what I've been doing:

a@ohnoes:~$ sudo passwd root
Password:
a@ohnoes:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

That's using the correct root password (the one I used to change the user password).  I've actually tried both with Synaptic etc.

Is there something else I should be doing?

Thanks for the quick response.

---

### Post by cgjones on 2006-05-15
To change the users password, all you need to type is **passwd**.

when you run apt-get, try this:
```
sudo apt-get update
```
And when asked for the password, try your user's password first.

---

### Post by YesNoYes on 2006-05-15
Thanks for the advice; unfortunately, this didn't even get to the password prompt.

a@ohnoes:~$ sudo apt-get update
a@ohnoes:~$

Also, I've been trying the user password but to no avail.  Basically, I can't access anything that requires a password except login.

But thanks anyway.

---

### Post by bluevoodoo1 on 2006-05-15
This might help...
[http://ubuntuforums.org/showpost.php?p=1011398&postcount=2](http://ubuntuforums.org/showpost.php?p=1011398&postcount=2)

---

### Post by Mustard on 2006-05-15
[QUOTE=YesNoYes]Thanks for the advice; unfortunately, this didn't even get to the password prompt.

a@ohnoes:~$ sudo apt-get update
a@ohnoes:~$

Also, I've been trying the user password but to no avail.  Basically, I can't access anything that requires a password except login.

But thanks anyway.[/QUOTE]

What output do you get when you type this command in terminal?

```
sudo whoami
```

---

### Post by YesNoYes on 2006-05-15
[QUOTE=Mustard]What output do you get when you type this command in terminal?

```
sudo whoami
```[/QUOTE]

I get:
```
a@ohnoes:~$ sudo whoami
Password:
a@ohnoes:~$ sudo get-apt update
a@ohnoes:~$ 
```

So basically, nothing happens after the sudo.

Regarding the post above, I did try the code they posted, though I believe their problem came about from running Synaptic and Update at the same time, whereas I've never been able to get either one to work.

This is what I got:
```
a@ohnoes:~$ cd/var/cache/apt/archives
bash: cd/var/cache/apt/archives: No such file or directory 
```

---

### Post by Mustard on 2006-05-15
Try this solution, as from the above output its seems like your /etc/sudoers file is not set up correctly to give your current user superuser privileges..

Use the **'Recovery Mode'** from the Grub menu at startup.

Recovery mode will drop you to a root prompt.  If you don't see the GRUB menu at startup then you probably have to press the ESC key to view it, as its sometimes hidden and only revealed when you hit the ESC key.

Once at the root prompt you can use this command to edit the /etc/sudoers file..

```
visudo  #this command does on thing.  It opens the sudoers file for editing
```

**Note**:- To save the sudoers file from visudo after editing you would use **ctrl + o**.  To exit visudo use **ctrl + x**.

My sudoers file looks like this.  Note the last line where I give my user sudo privileges.  This is the line that would need to be added by those who, for whatever reason, don't have sudo privileges.

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
mustard ALL=(ALL) ALL

```

**Method 1. Adding your username directly to sudoers**

You can see my username on the bottom line.  You would need to add your username to the bottom as I have done.

Assuming your user name was "bob'', then the line that would need to be added would be..
```
bob ALL=(ALL) ALL
```

This is just one way of doing it.

**Method 2. Adding a user to the administration group**
Note:If you are going to use this method, please ascertain whether an administration group is already set up.  See instructions below for viewing all the groups on your system.

Some sudoers files are set up with an admin group called 'adm' or sometimes it is called 'admin' (it can be called whatever you like really, but these two are fairly intuitive).  Users are then added to the adm group, and a line in the sudoers file that looks like this below gives members of the 'adm'  group admin access.

```
%adm ALL=(ALL) ALL
```

If your group is called 'admin' then it would look like this

```
%admin ALL=(ALL) ALL
```

You can find out what groups are setup on your system with this command..

```
cat /etc/group
```

If you decided to do it this way you would create the line above at the bottom of your sudoers file, using one of the examples above, save the sudoers file,  then at the root prompt do this command (substituting your username in the appropriate place and whatever your administration group is normally called)..

```
adduser your_username adm
```

or for the case of 'admin' being your administration group..

```
adduser your_username admin
```

---

### Post by ProjectGod on 2006-05-15
try this.

1. "sudo -K"
2. "sudo passwd root"
specify a password

3. "sudo gedit /etc/apt/sources.list"
when gnome editor opens up... remove the "#" from anything that looks remotely similar to a URL link... save the file exit

4. "sudo apt-get update"

try that...

---

### Post by Mustard on 2006-05-15
[QUOTE=YesNoYes]
This is what I got:
```
a@ohnoes:~$ cd/var/cache/apt/archives
bash: cd/var/cache/apt/archives: No such file or directory 
```[/QUOTE]

Just for you information with this command above you have neglected to put a space between the command 'cd' and the path to the directory '/var/cache/apt/archives'.  This has led to the command being interpreted as a path to a directory with the first directory in the path being a folder called 'cd', and the interpreter has correctly informed you that this path doesn not exist.

Your command should have looked like this..

```
cd /var/cache/apt/archives/
#note the space between the command 'cd'
#and the directory path
```

I notice this post is appearing on the second page of this thread, so I hope you don't miss my previous post, which shows a potential solution to your problem.

---

### Post by YesNoYes on 2006-05-15
Wow, that did it!  Thanks, Mustard.  Now I can really have some fun.

---

### Post by YesNoYes on 2006-05-15
And thanks for the additional info too. I have about 5hrs experience so far, so I appreciate corrections like that enormously.

---

### Post by Mustard on 2006-05-15
[QUOTE=YesNoYes]Wow, that did it!  Thanks, Mustard.  Now I can really have some fun.[/QUOTE]

Good luck and have fun. :)

---

