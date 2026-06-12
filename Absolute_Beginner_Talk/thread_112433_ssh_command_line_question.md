---
title: "ssh command line question"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by Hotchilli on 2006-01-04
I want to contact a remote host via ssh
I wil use a proxy IP  address.
whAT would the command line look like please.

hc:smile:

---

### Post by earobinson on 2006-01-04
same as normal no?

---

### Post by AndyCooll on 2006-01-04
The basic code is:
```
ssh user@ipaddress
```

And this shouldn't need to change as far as I'm aware. If using remotely you might to tinker with firewalls and such like

:cool:

---

### Post by kedarm on 2006-01-24
Thanks Andy Cooll,

I did enter ssh user@ipaddress.
I was asked for my password, and I entered it (correctly ;) )!

Now, I was in the remote host. On entering the command 'ls', I could view all my files. However, I couldn't access any. I tried to copy the files onto my desktop, by giving the command 'cp filename address', but it gave an error.

How do you copy files or write files to a server you have connected to?
Thanks.

---

### Post by alamba on 2006-01-24
Buddy u're into the remote system now. You can't copy files from there to your desktop with "cp". Try "scp" instead. Basically to move files u'll need to FTP them (or preferable scp them).

Akshay

---

### Post by kedarm on 2006-01-24
So, what exactly should my command be?

For instance, if I want to copy a folder ABC to /home, what should I type in the promt once I enter the remote server?
I tried scp ' ABC /home '. It says omitting directory.

Also, how do I write to a folder in the remote server?
Thanks

---

### Post by rensu on 2006-01-24
Try this:
scp [file] name@server_ip_address_where_to_paste:~
(Write in the server where is the file what you want to copy.)

---

### Post by rensu on 2006-01-24
~ means the username /home/username directory

---

### Post by alamba on 2006-01-25
It might be easier for you to download a scp client to move files. Google or "scp client" and you might hit into one. I know there's one for windows called winscp. The interface looks and works like any other ftp client.

Akshay

---

### Post by cwaldbieser on 2006-01-25
[QUOTE=kedarm]So, what exactly should my command be?

For instance, if I want to copy a folder ABC to /home, what should I type in the promt once I enter the remote server?
I tried scp ' ABC /home '. It says omitting directory.

Also, how do I write to a folder in the remote server?
Thanks[/QUOTE]
The general form is:
scp user@host:/path/to/file user@host:/path/to/file

So if you want to copy a remote file to a local directory, you don't even have to log in with ssh.  Try:
```

$ scp user@remote:/path/to/file local-file

```

---

### Post by dimis on 2006-01-25
You can always open a terminal and use sftp that comes with your Ubuntu distro:
```

sftp user@ip_address

```
Now the commands:
[list]
[*] put filename
[*] get filename
[/list]
behave exactly the way you want them to behave. put places a file (named filename) from your local host (local directory) to the remote host (remote directory) and get brings to your local host a file (named filename) from the remote host. Ofcourse you can always use absolute paths when referring to filenames (make sure you have the appropriate permissions though).
For more info you can:
```

man sftp

```

---

### Post by kiru on 2006-01-25
scp is the original SSH file transfer mechanism. It is modeled on BSD rcp, a protocol with a 15+
year history which has no RFC. Its syntax is very simple:
scp [user@]host:/path/to/source/file /path/to/destination/file
Will copy a remote file to a local destination. To copy a local file to a remote destination, one
uses the opposite syntax:
scp /path/to/source/file [user@]host:/path/to/destination/file
In either of these cases, the source file may be a wild-card matching multiple files. If a patch is
left off the destination file specification, the remote user’s home directory is assumed. E.g.:
scp /home/djm/*.diff hachi:
scp does not support copying between two remote destinations very well. It is possible using the
following syntax:
scp [user@]host1:/path [user@]host2:/path
For this to work, host1 must be configured for password less access to host2 (see section 4). Also
little feedback is given to the user on whether the operation succeeded.
scp can also copy files recursively:
scp -r source-path [user@]host:/destination-path
scp -r [user@]host:/source-path /destination-path
While it is useful for simple file transfer tasks, it has a number of limitations. The most annoying
of these is poor handling of file which contain characters which may be interpreted by the shell
(e.g. spaces). For example:
[djm@roku djm]$ scp "hachi:/mp3/J.S Bach/Matthaus Passion 0101.ogg" /tmp
cp: cannot stat ‘/mp3/J.S.’: No such file or directory
cp: cannot stat ‘Bach/Matthaus’: No such file or directory
cp: cannot stat ‘Passion’: No such file or directory
cp: cannot stat ‘0101.ogg’: No such file or directory
In these cases you need to double-escape the characters in question:
scp "hachi:/mp3/J.S.\ Bach/Matthaus\ Passion\ 0101.ogg" /tmp
Another problem inherent to scp is that it needs to be able to find a scp binary at the remote end.
Usually such commands are correctly installed in the remote systems $PATH, but if they are not
then transfers will fail:
[djm@roku djm]$ scp hachi:/tmp/foo /tmp
bash: scp: command not found

---

