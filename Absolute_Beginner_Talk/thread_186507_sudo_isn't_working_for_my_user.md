---
title: "sudo isn't working for my user"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by legolas on 2006-06-02
Hello all.  I want to thank all you guys for chipping in and helping out the know-nots.  I got another one for you if you are ready.  
I am trying to install SCIM for Japanese support for a user on my puter.  I have it installed on my side, but it will not give me sudo privleges or let me start the synaptic package manager if I log in to the users side.  How do I get the sudo to work when I log in for a different user?

---

### Post by LAurel on 2006-06-02
When you log in as another user and run a command with sudo, you need to confirm with the other user's password, not your own.

Other than that, check if the other user has the necessay privileges: System->Administration->Users and Groups, select the user, then Properties, then User privileges. Enable Executing system administration tasks if it's not enabled already, and anything else you might want the user to be able to do.

---

### Post by Breuls on 2006-06-02
I'm guessing the user you're talking about is not the user you created when installing the computer? That account gets sudo priviliges by default. If you need another account to have sudo privileges, you need the first account to make that happen.

What you have to do, when you have the account 'foo' that has sudo privileges and the account 'bar' that doesn't, is this:

1. Log in as foo.
2. Add 'bar' to the admin group with this command:

```
sudo usermod -Gadmin bar
```

3. Log out as foo, and log in as bar.
4. Try a sudo command, like 'sudo date'. It will show the date, but it will onl work if bar has sudo privs.

Now, understanding that you really need 'bar' to have those priviliges probably means you have no access to foo. If that's the case, there's nothing you can do.

---

### Post by vidak on 2006-06-02
you could edit the sudoers file, which tells the system who are able to use the sudo command. this can be done using
sudo visudo
. Read also 
man sudo
man visudo
man sudoers

---

### Post by legolas on 2006-06-02
Thanks guys!  Cool thing about linux, there are about 8 ways to do something, and you can do anything!

---

