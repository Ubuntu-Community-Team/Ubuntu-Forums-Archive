---
title: "Synaptic doesent work."
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-07-03
When I opened Synaptic today I got this error: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

I then typed dpkg --configure -a in the terminal, but when I did this I got a message which said I wasent a superuser.

Whats wrong?

---

### Post by lamego on 2006-07-03
Has the message says you need to run the command as superuser.
To run a command as root/superuser do:
```
  sudo command
```

Also read about [sudo]("https://help.ubuntu.com/community/RootSudo") on the wiki.

---

### Post by Denis on 2006-07-03
I've never used the command myself, but the manual (man dpkg) says this about dpkg --configure -a: 
```

dpkg --configure package ... | -a | --pending
              Reconfigure an unpacked package.  If -a or  --pending  is  given
              instead  of  package, all unpacked but unconfigured packages are
              configured.

              Configuring consists of the following steps:

              1. Unpack the configuration files, and at the same time back  up
              the  old  configuration  files,  so that they can be restored if
              something goes wrong.

              2. Run postinst script, if provided by the package.

```

It looks like it is safe to do "dpkg --configure -a". 
You need to run this command as a **root user**, do this by typing "sudo" before the command. The command will look like this: "sudo dpkg --configure -a". You will be asked for your password.

---

