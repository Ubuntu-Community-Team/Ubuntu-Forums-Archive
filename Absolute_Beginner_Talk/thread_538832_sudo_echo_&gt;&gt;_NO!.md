---
title: "sudo echo &gt;&gt; NO?!"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by ant2ne on 2007-08-30
> 
antsvr@antubuntu:~$ echo "/home/antsvr/nfs.test.share 192.168.1.0/24(rw,no_root_squash,async) #WORKING" >> /etc/exports
bash: /etc/exports: Permission denied
antsvr@antubuntu:~$ 
 
:confused:
> 
antsvr@antubuntu:~$ sudo echo "/home/antsvr/nfs.test.share 192.168.1.0/24(rw,no_root_squash,async) #WORKING" >> /etc/exports
bash: /etc/exports: Permission denied
antsvr@antubuntu:~$ 
 :mad:

How do I do this without chown/chmod? I hate doing that in the root

---

### Post by vexorian on 2007-08-30
is echo the only command that doesn't work with sudo?

you can just add echo blah blah to some .sh script and run the script with sudo, quite lame I think.

---

### Post by Majorix on 2007-08-30
```
echo "/home/antsvr/nfs.test.share 192.168.1.0/24(rw,no_root_squash,async) #WORKING" | sudo tee -a /etc/exports
```

If that doesn't work do it with this:
```
sudo gedit /etc/exports
```
and then add the line manually.

---

### Post by bogolisk on 2007-08-30
> **ant2ne said:**
> :confused:
 :mad:

How do I do this without chown/chmod? I hate doing that in the root

The problem is the redirection (thus open the file for write) is done by the original shell, which doesn't have permissions to write to /etc/exports,  and not sudo-ed program)
```

sudo sh -c 'echo "/home/antsvr/nfs.test.share 192.168.1.0/24(rw,no_root_squash,async) #WORKING" >> /etc/exports'

```

This way sudo will launch the shell (sh) which in turn will have the correct privileges to open the file /etc/exports for write.

---

### Post by justleen on 2007-08-30
beat me to it :)

your doing a "not sudo echo"

---

### Post by ant2ne on 2007-08-30
WTH?

That is confusing. I think I almost go the theory could someone explain in more detail?

---

### Post by sumguy231 on 2007-08-30
> That is confusing. I think I almost go the theory could someone explain in more detail?
Echo itself doesn't do the writing (file redirection), the shell does. So giving it sudo privilege doesn't do any good. The working method uses tee to redirect output and gives it the privilege it needs to append to /etc/exports.

---

### Post by bogolisk on 2007-08-31
> **ant2ne said:**
> WTH?

That is confusing. I think I almost go the theory could someone explain in more detail?

non working method: joe user runs
```

sudo echo "foo" >> /etc/exports

```
The actions performed:
[list=1]
[*] the current shell forks a subshell (to run sudo echo 'foo')
[*] the subshell, **running as joe user, opens /etc/exports for writing.**
[*] the subshell redirects its stdout to (the opened file) /etc/exports
[*] the subshell execs 'sudo echo "foo"'
[*] ...
[/list]
The 2nd step failed because the shell process owned by joe user doesn't have permissions to open /etc/exports for writing.



working method: joe user runs
```

sudo sh -c 'echo "foo" >> /etc/exports'

```
The actions (to be) performed:
[list=1]
[*] the current shell forks a subshell (to run sudo ...)
[*] the subshell execs 'sudo ....'
[*] the sudo process forks a child.
[*] the child raises its privileges to root and runs the command 'sh -c "echo foo >> /etc/exports"
[*] the sudo's child process, sh running as root, interprets its command line "echo foo >> /etc/exports".
[*] sh, **running as root, opens /etc/exports for writing**
[*] ....
[/list]
This works because the shell that interprets the "echo foo >> /etc/exports" (and open /etc/exports for writing), is running with root privileges.

---

### Post by Majorix on 2007-08-31
I agree that the proposed method is confusing. I too am confused by the looks of it. You could consider the method I offered though, and if you need anything about it explained just ask.

---

### Post by 5-HT on 2007-08-31
> **ant2ne said:**
> :confused:
 :mad:

How do I do this without chown/chmod? I hate doing that in the root

Try: ```
echo "/home/antsvr/nfs.test.share 192.168.1.0/24(rw,no_root_squash,async) #WORKING"| sudo tee -a /etc/exports
```cheers,

---

