---
title: "firestarter /sudo"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by findik1 on 2006-04-07
Hi, I wanted to check whether firestarter is working, and set automatically on all the time according to this forums and :
[http://doc.gwos.org/index.php/Firestarter_Guide#Intruduction](http://doc.gwos.org/index.php/Firestarter_Guide#Intruduction)
but sudo password does not work!

For example I type sudo /etc/init.d/firestarter status in different user than root. It asks password. Then I type the password that I entered during the Linux install. It says wrong password. Then I typed that spesific user account password, no error but nothing happens. Any idea?

Thanks

---

### Post by Sef on 2006-04-07
> For example I type sudo /etc/init.d/firestarter status in different user than root.

Did you set up a root account?

---

### Post by findik1 on 2006-04-07
no I did not, I thought no need for that in ubuntu?

[QUOTE=Sef]Did you set up a root account?[/QUOTE]

---

### Post by Mustard on 2006-04-07
It sounds like you might have used the expert install method for installation? Oh..I think I see, the HOW TO you were reading seems to get you to edit the /etc/sudoers file.  I can only assume you have made some error in this and now your sudo priviliges have been lost.

I'm going to post this HOW TO up here anyway, because I'm going out this afternoon and it sounds like you might need it regardless...

Use the **'Recovery Mode'** from the Grub menu at startup.

Recovery mode will drop you to a root prompt.  If you don't see the GRUB menu at startup then you probably have to press the ESC key to view it, as its sometimes hidden and only revealed when you hit the ESC key.

Once at the root prompt you can use this command to edit the /etc/sudoers file..

```
visudo  #this command does on thing.  It opens the sudoers file for editing
```

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

### Post by trent dillman on 2006-04-07
be aware: some ubuntu boxes have 'admin' instead of 'adm'

---

### Post by Mustard on 2006-04-07
[QUOTE=trent dillman]be aware: some ubuntu boxes have 'admin' instead of 'adm'[/QUOTE]

I'll edit the HOW TO I have on my little wiki to reflect this, because it could be confusing otherwise.  It's a good point to bring up.

-edit-

I'll put the edited version here so you can check it out. :)

---

### Post by findik1 on 2006-04-13
method1 worked for me, thanks

[QUOTE=Mustard]I'll edit the HOW TO I have on my little wiki to reflect this, because it could be confusing otherwise.  It's a good point to bring up.

-edit-

I'll put the edited version here so you can check it out. :)[/QUOTE]

---

