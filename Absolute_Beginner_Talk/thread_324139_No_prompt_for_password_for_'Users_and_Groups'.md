---
title: "No prompt for password for 'Users and Groups'"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by mgvbstar on 2006-12-23
Hi. I am running Edgy and I noticed when I run sudo or gksudo comands I am prompted for my password.  However, when I do System->Administration->Users and Groups, I am not prompted for my password and I am able to change my password and the root password without ever having to enter my password the I have to when I run for example 'gksudo nautilus'.  I feel like this is very insecure.  Is there any way I can make ubuntu prompt me for  my password when I go to 'Users and Groups'.  Thank you.

---

### Post by scrooge_74 on 2006-12-23
Before that did you enter your password at any given time in the prior 15 minutes? usually sudo will remember your password for that time

---

### Post by mgvbstar on 2006-12-23
Thanks for the quick reply. I had just logged in.  In fact, I did System-Administration->Synaptic Package manager and I was prompted for my password so at this time sudo did not remember my password.  I clicked cancel on the password prompt for synaptic, then went to users and groups and I was not prompted for my password so I don't think it's because sudo is remembering my password.

---

### Post by Sef on 2006-12-23
Is it only users and groups that you have problems with?

---

### Post by mgvbstar on 2006-12-23
Yes.  All the other administrative items in the administration menu, like firestarter, login window, synaptic, software sources, etc. prompt for a password. Users and groups seems to be the only one with free access.

---

### Post by scrooge_74 on 2006-12-23
Sounds like something that need to be patch or a small bug, did you make any changes somewhere else?

---

### Post by mgvbstar on 2006-12-23
The only thing I had done recently was to follow [this HOWTO]("http://www.ubuntuforums.org/showthread.php?t=192281&highlight=network+manager+pam") to PAM_keyring so network manager would stop asking me for my keyring password.  However, I tried removing this but it made no difference.  I have no idea whats wrong.  /usr/bin/users-admin is owned by root and belongs to group root so I shouldn't be able to execute it, right?

---

### Post by Circus-Killer on 2006-12-23
i just tried on my machine, same thing, looks like a common problem.

i go to users and groups, doesnt ask for password. i CHANGE ROOT password.
leave. use su to gain root access with set password.
left that. went to synaptic, and it asked for my password, so its not that its remembered my password.

---

### Post by kd7swh on 2006-12-23
make sure the user isn't a member of sudo, admin, or root (groups) and it should prompt you for a password. Once you have entered it in a session it may not prompt you for it again in the same session.

---

### Post by Circus-Killer on 2006-12-23
> **kd7swh said:**
> make sure the user isn't a member of sudo, admin, or root (groups) and it should prompt you for a password. Once you have entered it in a session it may not prompt you for it again in the same session.

yeh, as stated above, thats not the problem. every other admin app is asking for a password except users and groups.

---

### Post by kd7swh on 2006-12-23
my /usr/bin/users-admin had 777 permissions and that is why other users could use it.

re-chmod to fix it:

sudo chmod 700 /usr/bin/users-admin


see if that works

---

### Post by Circus-Killer on 2006-12-23
ahhhh no, now it wont let me in at all. just sais permission denied, without asking for password. (switched back to 777)

---

### Post by kd7swh on 2006-12-23
maybe 700 is too strict, keep playing with the permissions and you will find something that works.

755 maybe

---

### Post by miceyman on 2007-02-11
My roommate was being a bastard and kept changing my password and giving himself root access, and I couldn't figure out HOW this program was escalating its privileges without entering my password. 

What I did to work around this was rename users-admin to users-admin-fixed and change its permissions to 700. Then I changed users-admin to just contain "gksudo users-admin-fixed" so it would escalate to root when it should and you can run your program as desired. Here're the commands to use:

As root,

mv /usr/bin/users-admin /usr/bin/users-admin-fixed
chmod 700 /usr/bin/users-admin-fixed
echo "gksudo users-admin" | cat > /usr/bin/users-admin
chmod 755 users-admin

Seems to work for the moment. Not sure if there's a reason that this might be a bad idea, but at least my roommate can no longer mess around with my account. :)

---

