---
title: "nfs-kernel-server problem and /etc/exports prob"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by cinderella on 2006-09-28
hi i am trying to use an ATMEL fingerprint identification board that runs under linux OS (kernel version 2.4.19 rmk7.

(PLEASE give me a step by step way of solving this problem cos Im the dumbest newbie)

In the manual I was told that minimal configurations are required on the linux PC. The manual says the following:

[COLOR="DimGray"]This configuration should be performed as root. The nfs server should be started. For that, add the following line in the /etc/exports file:

/nfsshare *(rw,all_squash)

Once this is done, start the NFS server:
[PC_DEV]> /etc/rc.d/init.d/nfs start[/COLOR]

This is what I :
[COLOR="Red"]bulletproof@Bulletproof:~$ sudo gedit /etc/exports
Password:[/COLOR]

Then I typed in my password and then I typed /nfsshare *(rw,all_squash) and then saved the exports file. this is what the file looks like:

[COLOR="Red"]# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
/nfsshare *(rw,all_squash)
[/COLOR]

 Then I realised that I did not do this under root but under my home directory do then I did this and got errors:

[COLOR="Red"]root@Bulletproof:~# sudo gedit /etc/exports
cannot open display: (null)
Run 'gedit --help' to see a full list of available command line options.
root@Bulletproof:~# gedit /etc/exports
cannot open display: (null)
Run 'gedit --help' to see a full list of available command line options.
root@Bulletproof:~#[/COLOR]


ALSO please tell me how do I ensure that nfsshare exists???

---

### Post by Average Joe on 2006-09-28
I am afraid that I cannot help too much with the nfs server. However, to create/edit text files as root with gedit, you should always use:
```
gksudo gedit /whatever/file
```
instead of sudo gedit.

And everything you do that starts with 'sudo' you do as root, so the first time you made your /etc/exports file, you did it as root already. The second time you tried it, you got the error message because root cannot open a screen, since it is user bulletproof that started the x-session (graphical user interface). Therefore user root cannot control it (i.e. open new windows).

---

### Post by cinderella on 2006-09-29
> **Average Joe said:**
> I am afraid that I cannot help too much with the nfs server. However, to create/edit text files as root with gedit, you should always use:
```
gksudo gedit /whatever/file
```
instead of sudo gedit.

And everything you do that starts with 'sudo' you do as root, so the first time you made your /etc/exports file, you did it as root already. The second time you tried it, you got the error message because root cannot open a screen, since it is user bulletproof that started the x-session (graphical user interface). Therefore user root cannot control it (i.e. open new windows).

Hi I typed the following in my root shell

```
export DISPLAY=:0.0
```

so when I typed "gksudo gedit /etc/exports" it gave the following error:

```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(gksudo:11251): Gtk-WARNING **: cannot open display:
```

How do I solve this problem????

---

