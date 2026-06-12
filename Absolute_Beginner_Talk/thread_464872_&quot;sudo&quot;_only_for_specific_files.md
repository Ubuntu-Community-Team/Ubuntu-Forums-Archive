---
title: "&quot;sudo&quot; only for specific files?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by dupa on 2007-06-05
I have this problem:

I have a user, that should be able to execute a script "helloworld" that requires "root" privileges.

But I don't want to give him full "sudo" access to everything, i just want that he can execute "sudo" on specific scripts..

simpleuser
sudouser

my idea is to create a script of this kind:

```

script.sh

simpleuser$ su sudouser -p=sudouserpass
sudouser$ sudo ./helloworld

```

And I wil set execution permission on script.sh for "simpleuser" and do not give read permission to prevent that he can see the "sudouser" password written in that file..

---

### Post by alanandhispc on 2007-06-05
but out of curiosity, won't anything that user puts in the script, with/out your knowledge, will then run with root?

EDIT: sorry i read that last bit about the permissions.



but still, if you give them sudoers permission to perform certain functions, they will have that privilege throughout the system won't they?

---

### Post by Skrynesaver on 2007-06-05
Perhaps you should take a look at the suid bit, if a file is owned by root and has this bit set, any user who can execute the script runs it with root's permission.

---

### Post by dupa on 2007-06-05
> **Skrynesaver said:**
> Perhaps you should take a look at the suid bit, if a file is owned by root and has this bit set, any user who can execute the script runs it with root's permission.

where can I find the suid bit? thank you

---

### Post by Skrynesaver on 2007-06-05
Normally you set permisions as
```
chmod 750 filename
```
if you want:
   The user to be able to read, write and execute
   The group to be able to read and execute
   All other users to have no permisions for the file.
If you want to set the SUID bit on such a file you
```
chmod 4750 filename
```

---

### Post by bikeboy on 2007-06-05
I think ' sudo chmod u+s ./helloworld ' will do that. It's mentioned early in the chmod manual.

Not sure if this will work with suid set, but it might be an idea to make sure only the owner of the file can write to it, that way alanandhispc's concern might be addressed.

edit: trumped by Skrynesaver with a 4 digit octal (number based) permission. I never did know how to suid with a octal mode before, thank you.

---

### Post by Dr Eigen on 2007-06-05
You need to learn how to use sudo properly!  ;)

You can set up specific users/groups to be able to run specific commands by editing /etc/sudoers.  See "man sudoers".


(Don't get me started on Ubuntu's crazy "let's tell everyone to use sudo without educating them about root permission and how to use sudo properly" policy!)

---

### Post by Dr Eigen on 2007-06-05
Oh, and suid is a really bad idea.  HUGE potential security hole.

---

