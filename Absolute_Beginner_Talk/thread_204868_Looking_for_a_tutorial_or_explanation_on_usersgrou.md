---
title: "Looking for a tutorial or explanation on users/groups/permissions/etc"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by lastexyle on 2006-06-27
Google's not being very helpful and the whole thing has got me stumped. The paragraph on help.ubuntu.com wasn't very helpful either. So if anyone could point me in the right direction I'd be very greatful.

Things in particular I'm interested in:
What exactly are groups?
What are all the various other users on my system (dhcpd, etc) for?
How come when I create a user, it also creates a group with the same name?
Why is my user not in it's own group (eg, when I create "username", "username" is not part of the group "username" according to the GNOME user and group manager.
How come when I create another group, add myself to it, create a file as root, set the file's group to my new group and set the group permissions to read/write, I still can't read or edit the file as my normal user (I thought that was the point)
How come when I create a folder/file as myself, I cannot set the file/folder group to the new group I just created and added 

myself to in the last question?


I'm guessing that either the GNOME users and groups manager doesn't work fully or I have absolutly NO idead what groups are and how they work.

Thanks!

EDIT:
One other thing: is it possible to make it so that I create a file, the default permission are Owner: Read, Write, Group: Read and Public: Read instead of just Owner: Read, Write (644 instead of 600)?

---

### Post by Zimmer on 2006-06-27
See the tuxfiles in the links below. Go to Working with files and take a look at permissions etc..

and here is a good starter, too
[http://www.linuxnewbieguide.org/chap11.php](http://www.linuxnewbieguide.org/chap11.php)

---

### Post by lastexyle on 2006-06-27
Thanks, I guess I wasn't as off as I thought I was... but, does that mean the "Users and Groups" program in gnome is broken then?

---

### Post by rccharles on 2006-06-27
[QUOTE=lastexyle]

What are all the various other users on my system (dhcpd, etc) for?
[/QUOTE]
They are background services.  There are a lot of them.  Google on the service name.

[QUOTE=lastexyle]One other thing: is it possible to make it so that I create a file, the default permission are Owner: Read, Write, Group: Read and Public: Read instead of just Owner: Read, Write (644 instead of 600)?[/QUOTE]

See the umask command:
umask 644
See:
[http://www.ss64.com/bash/umask.html](http://www.ss64.com/bash/umask.html)

To access the terminal and issue commands see:
[http://www.psychocats.net/ubuntu/terminal.html](http://www.psychocats.net/ubuntu/terminal.html)

Robert:)

---

### Post by sandwormblues on 2006-06-27
Observation:  For someone with command-line experience, ownership and permissions is a snap.  for someone with command line experience, it's actually faster to use the terminal than the gui.  

but someone without command-line experience is unable to administer their own computer.  which is why Apple will take over the world.  :twisted:

---

### Post by lastexyle on 2006-06-27
I know how to use the terminal, but I prefer to do things visually a lot of the time, and it just seems odd for Ubuntu to include what seems to be a mostly broken program.

Is there some setting I need to change to make files created in nautilus have 644 permissions? I typed in umask 022 but if I create a new file in nautilus, it still has 600 as the default permissions. creating with a file with, for example, nano saves it with 644 now.


Thanks for all your help.

EDIT: It seems if I make new, new file templates and set their permissions, they are created with those permissions. Does anyone know if there's a way to change the settings for the "empty file" option

EDIT: One more question: Users can be in more than one group, right? So what is the difference between the users group memberships and the user's "main" group?

Update: I still can't get this group stuff to work. I went into nautilus as root, create a file, set the group to www-data, set group permissions to rw. added my main user to the group www-data, and I still cant modify or open the file even though I'm part of the group it has access to. What gives?

---

### Post by Zimmer on 2006-06-28
[QUOTE=lastexyle]
Update: I still can't get this group stuff to work. I went into nautilus as root, create a file, set the group to www-data, set group permissions to rw. added my main user to the group www-data, and I still cant modify or open the file even though I'm part of the group it has access to. What gives?[/QUOTE]

Where was the file? If the parent directories to the file are restricted ( not eXecutable ) for that user group then it is possible  you will not gain complete access to the file. I am a little curious as to why you are trying to create files as root for use by 'other users' and as to 'where ' you are trying to locate them..

On the face of it the Linux/root relationship is one  that prevents (hinders?) USERS from  messing up the operating system files accidentally. Creating paths and permissions for users where they should not have those permissions seems a bit of a slippery slope......

As for Gnome's User/Group management program, I looked at it yesterday and, yes , it confused me ,too. Perhaps (and it would seem logical) it can only be used in root user mode ? Anyone know (or prepared to experiment ?)

---

### Post by Apple 101 on 2006-06-28
You have to provide your password to use the User/Group Management programme in GNOME (sudo).  It is easy enough to use, but don't go changing group numbers of deleting groups, as things will most likely suddenly stop working.

---

