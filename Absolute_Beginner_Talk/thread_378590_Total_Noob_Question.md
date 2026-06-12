---
title: "Total Noob Question"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by bks on 2007-03-07
I keep seeing users referring to the cmd 'sudo'. Is it a cmd or is it a prefix and either way, what is it for?

---

### Post by Carnavan7 on 2007-03-07
Its a command that goes before another. It temporarily gives you root priviledges, e.g to install something/configure something. Once that task is complete, you revert to normal user priviledges. Hope that helps :)

---

### Post by schwascore on 2007-03-07
sudo is a command given in a terminal to temporarily gain root privileges.  For example, the following code shows how to install apache using apt-get:
```
sudo apt-get install apache2
```

By using sudo you are able to gain root privileges without actually logging in as the user root.  This helps keep your system safe by limiting root access only to times when it is specifically needed.

---

### Post by wpshooter on 2007-03-07
> **Carnavan7 said:**
> Its a command that goes before another. It temporarily gives you root priviledges, e.g to install something/configure something. Once that task is complete, you revert to normal user priviledges. Hope that helps :)

I believe you are evenutally reverted back to user privileges but NOT immediately.  I believe once you use SUDO you remain at root privileges until a certain time-out is attained.

---

### Post by bks on 2007-03-07
Thank you! I've been wondering that, but now I'm wondering, where is the root account? In distros like RedHat you can type 'su root' and there is an actual root account, but not with Ubuntu.

---

### Post by jordanmthomas on 2007-03-07
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
That should explain it pretty well.
Basically, Ubuntu's root password is locked by default.  You can unlock it using **sudo passwd root** but before you do, give the above a read.

---

### Post by bryan.taylor on 2007-03-07
You can configure a root account if you'd like to, but I don't think it's necessary.  If you'd like to issue several commands with root priveleges without repeating 'sudo' over and over, then try this:
```
sudo -i
```
That will give you an interactive session with root priveleges similar to 'su root'.

---

### Post by ltk5 on 2007-03-07
that's the best thing about ubuntu, you don't have to worry about root :D

---

### Post by bks on 2007-03-07
> **wpshooter said:**
> I believe you are evenutally reverted back to user privileges but NOT immediately.  I believe once you use SUDO you remain at root privileges until a certain time-out is attained.

The time out is 15 minutes.

---

### Post by bks on 2007-03-07
> **jordanmthomas said:**
> [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
That should explain it pretty well.
Basically, Ubuntu's root password is locked by default.  You can unlock it using **sudo passwd root** but before you do, give the above a read.

Thanks for the link, it all makes sense now and it is a good idea (locking the root acct, that is).

---

### Post by steve.horsley on 2007-03-07
Actually, the sudo command (think of it as SuperUser DO, kind of like Simon Says) only gives elevated privileges to the command that follows the word sudo. However, having established that it's really you at the keyboard by asking for your password, it will happily allow you to issue further sudo commands for the next 15 minutes before it demands your password again. Any other commands you execute during that time will only run with your normal user privilege unless you prefix them with sudo.

If you want to do a lot of work as root, there are lots of variations that do the same thing, but the one I tend to use is **sudo su**. This gets you a full root prompt despite the fact that the root account is locked and root cannot log in.

If you want to launch GUI apps with root privilege, use the prefix **gksu** instead of sudo. 
If you want to do lots of file management as root, use **gksu nautilus**. I change the background on root nautilus to red to remind me that it's the dangerous full-rights one.

---

