---
title: "Ubuntu will not start 2309, 2317"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by larry Gaminde on 2007-08-31
I was having an error message every time I tried to use Sudo command
it said something like
sudoers is 0666 and should be 0440
also Systems would not start
so I started to post here and there was a fix that said go to recovery mode and type 
chmod -R 0440 /etc
then
shutdown -r now
well now nothing will boot in recovery mode or gui mode I can get to a prompt root:none or something like this in recovery mode.

I keep getting errors of

init: rcS main process (2309) terminated with status 2
exec: 8 /etc/init.d/rc: permission denied
init: rc2 main process (2317) terminated with status 2

can this be fixed ??

---

### Post by larry Gaminde on 2007-08-31
> **larry Gaminde said:**
> I was having an error message every time I tried to use Sudo command
it said something like
sudoers is 0666 and should be 0440
also Systems would not start
so I started to post here and there was a fix that said go to recovery mode and type 
chmod -R 0440 /etc
then
shutdown -r now
well now nothing will boot in recovery mode or gui mode I can get to a prompt root:none or something like this in recovery mode.

I keep getting errors of

init: rcS main process (2309) terminated with status 2
exec: 8 /etc/init.d/rc: permission denied
init: rc2 main process (2317) terminated with status 2

can this be fixed ??

Should I just start reinstalling ubuntu, server and ftp over would this be better??

---

### Post by dstew on 2007-08-31
The command chmod -R 0440 /etc changed the permissions in the whole hierarchy of directories in /etc. This will result in a non-functioning system.

The file permissions are a critical element of the system, and should never be changed wholesale. Sweeping changes to file permissions, especially in system directories like /etc,  can have the same effect as deleting the files. The changed permissions will make the files invisible to the processes that need to access them. You may need to reinstall your system. 

By the way, do you have any guess as to why the sudoers file permissions were changed in the first place? Have you been trying to get access to files or programs by changing permissions? There is a good discussion of users and file permissions [here.]("http://www.linux.org/lessons/interm/c432.html")

---

