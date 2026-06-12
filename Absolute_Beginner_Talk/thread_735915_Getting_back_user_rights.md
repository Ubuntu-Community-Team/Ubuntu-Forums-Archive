---
title: "Getting back user rights?"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by Morticutor UK on 2008-03-26
So I just removed some of my user rights, thinking that I can access them through the root whenever I needed them.  But now I've changed my mind and I don't have access to them (specifically the synaptic program and the users/groups thing).   

How do I get them back?

---

### Post by arochester on 2008-03-26
Use a program called visudo which is expressly for that purpose.

Copied from [http://ubuntuforums.org/archive/index.php/t-150021.html](http://ubuntuforums.org/archive/index.php/t-150021.html)

"Use the 'Recovery Mode from the Grub menu at startup.

Recovery mode will drop you to a root prompt. If you don't see the GRUB menu at startup then you probably have to press the ESC key to view it, as its sometimes hidden and only revealed when you hit the ESC key.

Once at the root prompt you can use this command to edit the /etc/sudoers file..

visudo #this command does on thing. It opens the sudoers file for editing

My sudoers file looks like this. Note the last line where I give my user sudo privileges. This is the line that would need to be added by those who, for whatever reason, don't have sudo privileges.

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

Defaults !lecture,tty_tickets,!fqdn

# User privilege specification
root ALL=(ALL) ALL
mustard ALL=(ALL) ALL


You can see my username on the bottom line. You would need to add your username to the bottom as I have done.

Assuming your user name was "bob'', then the line that would need to be added would be..
bob ALL=(ALL) ALL

This is just one way of doing it. Some sudoers files are set up with an admin group called 'adm'. Users are then added to the adm group, and a line in the sudoers file that looks like this below gives members of the 'adm' group admin access.
%adm ALL=(ALL) ALL

If you decided to do it this way you would create the line above at the bottom of your sudoers file then do this command (substituting your username in the appropriate place)..

adduser your_username adm"

---

### Post by nick_h on 2008-03-26
If you still have sudo access then you can run the users/groups program from the command line using:
```
sudo users-admin
```
and synaptic using:
```
sudo synaptic
```

---

### Post by The Cog on 2008-03-26
People are guessing and coming up with wildly different theories to what you did. Exactly how did you remove the rights - what did you do?

---

