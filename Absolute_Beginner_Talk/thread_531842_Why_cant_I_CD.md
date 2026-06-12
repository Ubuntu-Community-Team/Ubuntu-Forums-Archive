---
title: "Why cant I CD?"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by baracuda68 on 2007-08-22
Hi
Why cant I cd to my Downloads folder?
It is in my /home/bob(user name) folder.

I can get to it ok using the GUI (konquerer)

bob@bob:~$ cd /downloads
bash: cd: /downloads: No such file or directory
bob@bob:~$ cd /Downloads
bash: cd: /Downloads: No such file or directory
bob@bob:~$ cd /home
bob@bob:/home$ cd /Downloads
bash: cd: /Downloads: No such file or directory
bob@bob:/home$ cd /home/bob
bob@bob:~$ cd /home/bob/downloads
bash: cd: /home/bob/downloads: No such file or directory
bob@bob:~$ /home/bob/Downloads
bash: /home/bob/Downloads: is a directory
bob@bob:~$ cd /Downloads
bash: cd: /Downloads: No such file or directory
bob@bob:~$ cd:/downloads
bash: cd:/downloads: No such file or directory
bob@bob:~$ cd/downloads
bash: cd/downloads: No such file or directory
bob@bob:~$ cd/Downloads
bash: cd/Downloads: No such file or directory
bob@bob:~$ sudo cd /bob/Downloads
Password:
sudo: cd: command not found
bob@bob:~$ cd /downloads
bash: cd: /downloads: No such file or directory
bob@bob:~$ d /downloads
bash: d: command not found
bob@bob:~$ cd /downloads
bash: cd: /downloads: No such file or directory
bob@bob:~$ cd /Downloads
bash: cd: /Downloads: No such file or directory
bob@bob:~$
bob@bob:~$ CD/HOME
bash: CD/HOME: No such file or directory                 



Any Idea?:confused:

---

### Post by Ek0nomik on 2007-08-22
Stop putting the '/' in front of the directory.

Remember, / is a directory itself.

Try:

```
cd /
```

See, it works.  By you typing 'cd /downloads', you are trying to get into the directory /downloads, not /home/username/downloads.

See the difference?

The ~ can also be interpreted as /home/username.  As an example, type:

```
cd /
cd ~
cd /
cd /home/bob #On this last command you can watch the terminal turn from / to ~, even though you typed /home/bob
```

---

### Post by mlentink on 2007-08-22
try 
```
cd downloads

```
Putting a slash in front of the directory means you expect it to be in the 'root' of your filesystem, yet you said it was in your home directory
Also: filenames (and therefore also directory names are case sensitive.

---

### Post by baracuda68 on 2007-08-22
Thanks all...
Because of you I figured it out!
I guess it is also case sensitive, too
Downloads directory-not downloads...

Thanks.

---

