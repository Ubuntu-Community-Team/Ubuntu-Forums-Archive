---
title: "scp or sftp problems"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Red-Shield on 2008-01-19
i want to copy an entire directory/folder i prefer to use sftp but mabey it cant copy an entire directory so what about scp here is what i have tried and still nothing i am using ubuntu ultimate 7.10:

red-shield@FederalReserve:~$ scp serial-killer@192.168.1.101
usage: scp [-1246BCpqrv] [-c cipher] [-F ssh_config] [-i identity_file]
           [-l limit] [-o ssh_option] [-P port] [-S program]
           [[user@]host1:]file1 [...] [[user@]host2:]file2
red-shield@FederalReserve:~$ scp -r /home/serial-killer/baby_pics serial-killer@192.168.1.101/home/red-shield/Desktop
cp: cannot stat `/home/serial-killer/baby_pics': No such file or directory
red-shield@FederalReserve:~$ scp -r /home/serial-killer/baby_pics serial-killer@192.168.1.101:/home/red-shield/Desktop
serial-killer@192.168.1.101's password: 
/home/serial-killer/baby_pics: No such file or directory
red-shield@FederalReserve:~$ scp -r /home/serial-killer/Desktop/baby_pics serial-killer@192.168.1.101:/home/red-shield/Desktop
serial-killer@192.168.1.101's password: 
/home/serial-killer/Desktop/baby_pics: No such file or directory
red-shield@FederalReserve:~$ scp -r /home/serial-killer/Desktop/baby_pics red-shield@192.168.1.101:/home/red-shield/Desktop
red-shield@192.168.1.101's password: 
Permission denied, please try again.
red-shield@192.168.1.101's password: 
Permission denied, please try again.
red-shield@192.168.1.101's password: 
red-shield@FederalReserve:~$ scp -r ~/home/serial-killer/Desktop/baby_pics serial-killer@192.168.1.101:/home/red-shield/Desktop
serial-killer@192.168.1.101's password: 
/home/red-shield/home/serial-killer/Desktop/baby_pics: No such file or directory
red-shield@FederalReserve:~$

---

### Post by isparkes on 2008-01-19
Are you sure that the baby pics are there, and that you have the rights to read them?

ls -la  /home/serial-killer/baby_pics

if this gives you an error, the files are not there, and it's nothing to do with SCP.

If there is a complicated structure to copy, I usually make a tar of it, and just transfer the one file. It'll be quicker too...

By the way, you seem a bit confused about the "~". This is a shortcut to your home directory "/hone/serial-killer". It can also be used to reference the home directory of any other user by using "~otherusername/..."

---

### Post by isparkes on 2008-01-19
Are you sure that the baby pics are there, and that you have the rights to read them?

ls -la  /home/serial-killer/baby_pics

if this gives you an error, the files are not there, and it's nothing to do with SCP.

If there is a complicated structure to copy, I usually make a tar of it, and just transfer the one file. It'll be quicker too...

By the way, you seem a bit confused about the "~". This is a shortcut to your home directory. It can also be used to reference the home directory of any other user by using "~otherusername/..."

---

### Post by Red-Shield on 2008-01-19
yes i am sure that they are there i think there is a problem with the scrip that i am using or something if you feel there is not let me know i am using ubuntu ultimate edition  7.10 can you use sftp for transfer of the directory i want to pull a full folder through  all ports are forwarded i like to use ssh it is quick and convient and also secure even if it is old please help if it can be done with sftp that would be better


red thanx

---

### Post by qpieus on 2008-01-19
Your commands don't make any sense. For example this```
serial-killer@192.168.1.101/home/red-shield/Desktop
```
indicates you are trying to copy to the 192.168.1.101 machine as the user serial-killer, but to red-shield's Desktop. Unless serial-killer has write access to red-shield's home, this will not work. I bet that's why you are getting the various errors. Some of your other commands have similar problems. 

If you want to transfer the files to /home/red-shield/Desktop on the 192.168.1.101 machine, then you'd have to use a syntax like this:```
*red-shield*@192.168.1.101/home/red-shield/Desktop
```

It looks like you are dealing with 2 user names here and the one user is trying to write to the other's home.

---

### Post by Red-Shield on 2008-01-22
thank you that could be the problem the commands are a bit diffrent in the two protocols i am using i am more familure and like SFTP in the above string i was using SCP what i am looking for is a way to copy a directory using SFTP if it can be done but i bet that you are right there probley is a conflict of intrest in the permissions in my way so thank you for the info i want to copy a whole folder/rirectory containing videos or pictures or what ever but i want an SSH protocal  to do it with i was thinking that there wasargument that could be used -R recursive or something to that tune

---

### Post by scorp123 on 2008-01-22
> **Red-Shield said:**
> thank you that could be the problem the commands are a bit diffrent in the two protocols i am using i am more familure and like SFTP in the above string i was using SCP what i am looking for is a way to copy a directory using SFTP if it can be done but i bet that you are right there probley is a conflict of intrest in the permissions in my way so thank you for the info i want to copy a whole folder/rirectory containing videos or pictures or what ever but i want an SSH protocal  to do it with i was thinking that there wasargument that could be used -R recursive or something to that tune How about using some punctuation??

Besides, the manual is your friend: ```
man scp
```

---

### Post by qpieus on 2008-01-22
I'm not familiar with sftp, but scp can do exactly what you want - copy stuff between machines via ssh. rsync can also do that task very easily.

There's many examples of how to use scp or rsync on the web, so I won't explain it here (unless you really can't follow the guidance available).

One thing about scp though that is rather irritating - if you try to copy a sym link with scp, it will copy the files that are linked to, rather than copying just the sym link. That caused me some problems one time.

---

### Post by scizzo on 2008-01-22
Example1:

```

Example: remotelogin@remotehost:path/to/send/to

*Don't forget the : between the host and path*

user@something: scp filetosend remoteuser@remotehost:/full/path/

```

You can also use lftp or yafc or gftp to send over the file through sftp:

---

