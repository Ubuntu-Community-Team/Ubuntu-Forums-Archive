---
title: "correct syntax for scp on different ssh port"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by lunaz on 2007-09-20
probably missing something obvious but i'm not sure what i typed wrong, my ssh server is not on port 22.

```

luna@badassness:/media/sda4/2007-09-20--21.27.10$ scp -P 4245 192.168.1.100:/var/www/missoulalug/00001.jpg
usage: scp [-1246BCpqrv] [-c cipher] [-F ssh_config] [-i identity_file]
           [-l limit] [-o ssh_option] [-P port] [-S program]
           [[user@]host1:]file1 [...] [[user@]host2:]file2
luna@badassness:/media/sda4/2007-09-20--21.27.10$ 

```

---

### Post by dwhitney67 on 2007-09-21
Use that -P option like you have it.  Don't forget to add the trailing '.' to mark your copy-destination or insert your source!


scp -P <remote port> <source> <dest>

---

### Post by lunaz on 2007-09-21
it changed me to root then after i typed in my server's pw it told me permission denied.

```

luna@badassness:~$ cd /media/sda4
luna@badassness:/media/sda4$ cd 2007-09-20--21.27.10
luna@badassness:/media/sda4/2007-09-20--21.27.10$ sudo scp -P 4245 00001.jpg 192.168.1.100:/var/www/missoulalug/
root@192.168.1.100's password: 
Permission denied, please try again.
root@192.168.1.100's password: 

```

---

### Post by dwhitney67 on 2007-09-21
The first password you need to type is _your_ local sudoer password.  Then you will be prompted for the root password for the remote server to complete the transaction.  Make sure that you type the remote server's root password correctly.

---

### Post by digen on 2007-09-21
What is the file permissions of the file 00001.jpg you're trying to SCP ? 

My first guess if you wouldn't need to sudo. Since you're using sudo it's promting you for the root password of the machine 192.168.1.100 and not the root password of your local system. 

scp -P 4245 00001.jpg 192.168.1.100:/var/www/missoulalug/

Execute the above command and it should prompt you for the password of the user luna on 192.168.1.100. 

However, considering the location where you're trying to copy the file, ideally you would need root permissions. 

scp -P 4245 00001.jpg root@192.168.1.100:/var/www/missoulalug/

The above command will work after you enter the root password of the machine 192.168.1.100

---

### Post by lunaz on 2007-10-08
hm, thanks for the replies..i don't have the root acct turned on on any comp, so i tried luna, but it said permission denied :(

---

### Post by dwhitney67 on 2007-10-08
I can think of two situations that may be the culprit of your error.  Either 1) you are attempting to transfer a file owned by user A to a destination on the remote system not owned by user A, or 2) you are attempting to transfer a file in which you do not have read-permissions to access the local file.

I will not delve further into these 2 possibilities because I think these are self-explanatory and easy to comprehend.

A third possibility is that user A is attempting to transfer a file to a system in which there is not an account for user A.  You may be prompted for a password, but you will see the "permission denied" message after typing what you think is a valid password.

Do any of these scenarios fit your situation?

---

### Post by lunaz on 2007-10-08
thanks for the help!

i just tried to scp a test.txt file after changing /missoulalug's owner to luna:www-data instead of root:root. then i tried a picture, and that worked after i did chmod 775 on it.

next question: how do i upload files/folders without having to change the permissions / owners after each session?

---

### Post by dwhitney67 on 2007-10-08
If I understand you correctly, to you want to transfer files from one system, where the file has an owner of luna:luna, but on the destination an owner of luna:www-data.

I believe you will need to set the "sticky" bit for the groupID on the destination folder.  Read this [thread]("http://www.linuxquestions.org/questions/linux-newbie-8/setting-file-directory-permission-with-sticky-40467/") to determine if this fits your case.

If it doesn't fit your case, then please provide a clear listing of the following:

1.  UserID/groupID information of the user performing the secure-copy.
2.  Permissions of the file being transferred.
3.  Permissions of the destination folder

---

