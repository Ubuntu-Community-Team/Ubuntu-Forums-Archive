---
title: "Interrupted adept. Problem"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by angel6700 on 2007-11-16
Hello, 

yesterday I make a great mistake with my system: (Kubuntu 6.06).

In adept, I marked for uninstall the package jasper, and in consequence, several other packages were also marked as uninstall to satisfy denpendences, ok... 
The problem came because I clicked on Apply instead of Preview Changes !!!! (more than 200 packages, and I don't know which ones, started to be uninstalled.

I quickly closed adept, but dpkg continued running in the background, so I typed 
```
ps -ef |grep dpkg
```
 and killed it.

Everything happened in 30 seconds... but, now, I do not know what to do, because, adept refuses to start. And I think that a 
```
dpkg --configure -a
or
apt-get upgrade
```
will try the removal.

Is there a way to know what pending changes exists? and /or cancel them?


Thanks a lot for your help.

BTW, the system is working well..

Regards, 

Angel.

---

### Post by Inxsible on 2007-11-16
if you used synaptic to remove packages, then you should be fine. when you remove a package, it only removes the dependencies associated with that particular package.
As you mention, your system is working fine.

If you still want to see what they were, i think they are listed in the section called 'Not Installed '(removeable)' when you click the Status tab on the bottom left.


I am not too sure on the exact wording, but you will see what I mean when you get there.

---

### Post by angel6700 on 2007-11-16
Thanks for your answer, but as I said, I used adept (the kubuntu equivalent to synaptic). And now, it says that another instance is running (or apt, dpkg or aptitude) and cannot commit changes.

I think that dpkg --configure -a could solve this problem, but I ignore what more could it do.

Is there a file where I can look for this information?

ok while writing this I looked at man dpkg. and the this file can be give me that info:
/var/lib/dpkg/status

see you later.

Angel.

---

### Post by Inxsible on 2007-11-16
There is another instance of adept running. if you have closed the app, but still get the same error, it might be that the process is still running in the background. Use the command 'top' to find the pid and then use ```
kill *pid*
``` to kill it

EDIT: better yet try this```
killall adept
``` if adept is the name of the process ( i am not entirely sure since i dont use KDE it could be adept-manager too) Basically ```
killall *packagename*
```

---

