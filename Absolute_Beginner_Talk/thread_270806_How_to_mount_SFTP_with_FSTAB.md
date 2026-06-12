---
title: "How to mount SFTP with FSTAB"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by thornomad on 2006-10-03
Hello,

I wanted to automatically mount an SFTP connection by adding an extra line to my /etc/fstab file ... but I don't know what to write!  I have been searching google and these forums but can't come up with anything.  Does anyone know the correct syntax to use ?

Thanks,
Damon

---

### Post by llamakc on 2006-10-03
[http://fuse.sourceforge.net/sshfs.html](http://fuse.sourceforge.net/sshfs.html)

---

### Post by thornomad on 2006-10-03
Thanks for that link ... before I go downloading and whatnot, is that needed to accomplish the mount ?  Or is it simply a "better" way to do it ?

---

### Post by llamakc on 2006-10-03
Install sshfs from the repositories: it is already in there.

sudo apt-get install sshfs

cd /usr/share/doc/sshfs/

Check out the README in there.

Make a directory somewhere like:

mkdir /home/YOURUSERNAME/remote
```

sshfs IP.ADDRESS.OF.OTHER:/DIRtoMount /home/YOURUSERNAME/remote
```

Done.

---

### Post by llamakc on 2006-10-03
Doh!

```

ken@schlitz:~$ sshfs 192.168.0.100:/home/ken/ /home/ken/llama
fuse: failed to exec fusermount: Permission denied

```

Don't forget to do this before mounting:

```

sudo adduser YOURUSERNAME fuse

```

You may have to logout/login before being able to use fusermount. I did.

---

### Post by llamakc on 2006-10-03
And your fstab would look like:
[FONT=Verdana,Arial,Sans-Serif]
[/FONT]```
sshfs#user@host:/    /home/you/remote    fuse    defaults    0 0
```

---

### Post by llamakc on 2006-10-03
If you need help with the directories in fstab we'll need to know WHAT directory you want to mount and where you want it to end up.

---

### Post by thornomad on 2006-10-03
Hi, thanks for the quick reply (and detailed instructions).  Installed very easily!  Excellent.  However, after creating the new directory on the local machine when I run the command:

sshfs myname@192.169.1.200:/home/remotehost/dir /home/localhost/testdir

I get an error saying "fuse: failed to exec fusermount: Permission denied".  I tried running it as sudo, which worked, however, then when I try to cd to my /home/locahost/testdir I get a "permission denied" warning.

Do I need to change permissions on the new folder (or on something) before I do the mount step ?

Thanks,
Damon

---

### Post by llamakc on 2006-10-03
do the adduser tip above, and logout and back in.

When you created the directory /home/localhost/testdir you did it as user, and not root: correct? If you created that dir as root, root owns it. You'll have to chown it if that happens.

It will certainly work. I just mounted my home directory on my server from my desktop box without a problem.

---

### Post by thornomad on 2006-10-03
Got it! Thanks!  Wow ... neat-o!  Solved all my problems!

Two quick questions:

1. Do I have to use that command each time I login unless I make the changes to my "fstab" ?  (is a pretty simple command, to be fair ... I don't mind typing it)

2. I tried and failed on a couple directories (using the sudo command) ... do I have those mounted and do I need to "unmount" them or will it take care of itself (and I can delete the tests) on a re-login?

Again: THANKS AGAIN !  This is excellent.

---

### Post by llamakc on 2006-10-03
1. Yes, unless you change your /etc/fstab you would run that at each instance you want it mounted. In BASH (the default shell in the Terminal) you can type ctrl+r (control key and letter r) to bring up a search of your terminal history. At that point start typing "sshfs" and you should see the rest of the command appear. Hit enter. Saves you some keystrokes.

I'd probably put it in as a bash alias with a catchy name I'd remember, myself.

2. Problems with other directories would depend on each one you were trying. Share an example, if you can.

---

### Post by thornomad on 2006-10-03
Answers to my own questions:

1. have to use the sshfs command every time there is a restart (logins seem to persist)

2. on a restart the directories I botched are returned to normal

Plan to try to the fstab bit in the future.  THANKS again!

---

### Post by thornomad on 2006-10-03
Thanks again!  (I didn't notice your reply because was refreshing and overlooked the second page that was added.)

---

### Post by jpkotta on 2006-10-03
For future reference: [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

---

### Post by llamakc on 2006-10-03
Thanks jpkotta. I had to re-learn the steps as I was helping. I should have known to look there first.

Great link. Thanks for adding it to the thread.

---

### Post by thornomad on 2006-10-04
I noticed that, after a restart, I am getting this error:

fusermount: failed to open /dev/fuse: No such file or directory

I looked around online and found a fix at: [http://fuse.sourceforge.net/wiki/index.php/SshfsFaq](http://fuse.sourceforge.net/wiki/index.php/SshfsFaq)

mknod -m 666 /dev/fuse c 10 229

However, I have to add that code each time I restart before I call the sshfs function ... was going to create an entry in my .bash_aliases file to shorten the sshfs call, can I call this mknod first ?  I am not sure how to get them both to run under the same alias.

---

