---
title: "sudoers problem"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-07-23
I have two users lex1 and admin.

today i let admin become a sudoer.

now some hours later logging into lex1 i find 
lex1 is not in sudors file this will be reported

Now for some reason lex1 is not a suoer

see sudoers file below: 

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

# Members of the admin group may gain root privileges
admin   ALL=(ALL) ALL

system_admin ALL=(ALL) ALL

---

### Post by steve.horsley on 2006-07-23
Your sudoers file appears to have been modified. Normally, it allows members of the admin group to do anything. This is normally done with this line:
**%admin ALL=(ALL) ALL**

Someone appears to have removed the percent symbol from the start of the line so that it permits the user admin rather than members of the group admin.

I am guessing that this was yourself. If you wanted to grant sudo rights to user admin as well as user lex1, the right thing to do would be to add user admin to the admin group. There is a command to do this but I don't know what it is (maybe useradd?). You can do it by editing the file /etc/group, and then replacing the percent sign in /etc/sudoers. Your line in /etc/group would look something like this:
**admin:x:112:lex1,admin**

---

### Post by catlett on 2006-07-23
To add lex1 to the administrator group
```
sudo adduser lex1 admin
```
To add lex1 to sudoer file 
```
export EDITOR=gedit && sudo visudo
```
Then add this line to the end of the file
```
 lex1        ALL=(ALL) ALL
```
For any other user, just replace lex1 with the user's name that you want to add to the sudfoers file or administrator group.

---

