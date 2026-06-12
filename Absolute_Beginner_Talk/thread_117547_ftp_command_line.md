---
title: "ftp command line"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by wizzkid on 2006-01-15
I want to use a command line ftp access thru terminal. but I need help with the command.

I was able to login to ftp by typing ftp ftp.ftpsite.com... username anf password. now I need to know the command for the following.

1. download remote folder to local pc. (eg. i want to download graphics folder together with its sub-directories) using get command

2. upload local folder to remote site (eg. upload graphics folder together with its sub-directories) using put command.

3. deleting folder together with its subdirectories

4. renaming files or folders

guess this is all what i need as of this moment. thanks

---

### Post by pertti on 2006-01-15
[QUOTE=wizzkid]I want to use a command line ftp access thru terminal. but I need help with the command.

I was able to login to ftp by typing ftp ftp.ftpsite.com... username anf password. now I need to know the command for the following.

1. download remote folder to local pc. (eg. i want to download graphics folder together with its sub-directories) using get command

2. upload local folder to remote site (eg. upload graphics folder together with its sub-directories) using put command.

3. deleting folder together with its subdirectories[/QUOTE]

I don't know about this three.

[QUOTE=wizzkid]4. renaming files or folders[/QUOTE]

```
rename oldname newname
```

---

### Post by Celenb on 2006-01-15
I believe "get" is the command to download, and "put" is the command to upload.

If it won't allow you to "get" or "put" whole directories/folders, try the -r arguement, ie "get -r(or maybe -R) foldername".

---

### Post by thava on 2006-01-15
i never used ftp, but i use ncftp its a nice tool. its also support  tab completion

to install ncftp:
sudo apt-get install ncftp

a)connect to ftp sever:
type in terminal:
ncftp -u username hostname -p

> 1. download remote folder to local pc. (eg. i want to download graphics folder together with its sub-directories) using get command

get -r foldername

> 2. upload local folder to remote site (eg. upload graphics folder together with its sub-directories) using put command.

type in terminal:

ncftpput -u username hostname remotefoldername localfoldername

> 3. deleting folder together with its subdirectories
rm -r foldername


> 4. renaming files or folders
rename file/foldername
guess this is all what i need as of this moment. thanks

rename file/foldername

/ Thava

---

### Post by cwaldbieser on 2006-01-15
[QUOTE=wizzkid]I want to use a command line ftp access thru terminal. but I need help with the command.

I was able to login to ftp by typing ftp ftp.ftpsite.com... username anf password. now I need to know the command for the following.

1. download remote folder to local pc. (eg. i want to download graphics folder together with its sub-directories) using get command

2. upload local folder to remote site (eg. upload graphics folder together with its sub-directories) using put command.

3. deleting folder together with its subdirectories
[/QUOTE]

I don't think the FTP protocol itself provides for doing these kind of recursive subdirectory operations.  The simple terminal ftp client doesn't implement them.  Lots of more sophisticated FTP clients execute multiple FTP commands on your behalf to do this, though.  E.g. lftp.

---

### Post by wizzkid on 2006-01-15
OKay! Thanks,,, Im using gftp, though it a good software also.. :) will try lftp :)

---

