---
title: "Linux file permissions"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by muguwmp67 on 2007-01-31
On the AS/400 we had the capability to assign permissions to an object (program) that would be adopted by the current user.  In other words, I could use a sysadmin system command in a CL program (script) and assign that program sysadmin authority.  Any user then could run the program, and it would work correctly, even though the user didn't have any specific or group  to the particular command.

Is there a way to do this in linux?  I'm using wlassistant on my laptop, but it can only run with sudo privileges.  I would like to be able to give this laptop to someone, but I do not want them to access root at all.  Can I give wlassistant root privleges without them needing to run it from sudo?

TIA

---

### Post by IYY on 2007-01-31
You could use chown to change the owner of a file (a program is just an executable file) to any user you'd like.

Then, there is the command chmod that will change the permissions. With it, you can allow all users on the system to execute a command without even changing the owner. For example,

sudo chmod uog+x myprogram

will allow the owner, the group and others to execute the program.

---

### Post by muguwmp67 on 2007-01-31
Looking at the object and its permissions, I see the owner is root.  Group and others have read and executable permission to the file.  

I think the reason it needs sudo though is to modify configuration files for wireless connections.  

In a nutshell, I would like anyone to be able to use the command, but have the command run as if it were root, regardless of who used it, and without them having to type in a password each time.

I'm well aware that this is a potential security hole, but I would rather do it this way than to provide users with permission to the directories or files that it needs, which to me is a more serious breach.

---

