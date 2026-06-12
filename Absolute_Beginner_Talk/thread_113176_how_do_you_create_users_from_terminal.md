---
title: "how do you create users from terminal?"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by iand675@gmail.com on 2006-01-05
I've brought one more linux machine to life, but unfortunately setup for a non-root user during installation failed.

So I can access the terminal with root still by using ctrl+alt+F3, but how do I set up new users from here? Can anyone give me explicit step by step instructions?

---

### Post by Turtle.net on 2006-01-05
You can find all the information you need by typing ```
man useradd
``` in a terminal. Hope this help :)

---

### Post by Mustard on 2006-01-05
Just as an aside, did you use expert install?

Expert install doesnt set up the first user with sudo privileges, so its necessary to edit the /etc/sudoers file using the visudo command from a root prompt to give sudo privileges to the user.

Here is an example of my /etc/sudoers file as a reference...

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

I quite often use expert install myself, so the process has become quite familiar to me.  The addition of the last line with my username 'mustard' in it is all that's necessary to give my user account sudo privileges.

---

### Post by kairu0 on 2006-01-05
Generally,

```
adduser username
```

is all you need.

---

### Post by bulldogzerofive on 2006-01-06
I think you will have to add the -m flag to useradd if you want it to get a home directory as well.

---

