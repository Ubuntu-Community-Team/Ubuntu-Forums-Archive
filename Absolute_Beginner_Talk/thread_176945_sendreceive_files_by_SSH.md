---
title: "send/receive files by SSH"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by Compact on 2006-05-15
Is there any way to send/receive files by SSH? I'm using PuTTY and the ubuntu default ssh server.

---

### Post by richbarna on 2006-05-15
Sure is :)
Type this command (better if you are root):-
> scp <file name> <computer>@ipadress:/place/
For example :-
> scp prog.deb john@213.85.33.21:/user1/
I do this from a desktop to a laptop, from root to root. A password request comes up, type password (root), and file transfers.

---

### Post by NoUse on 2006-05-15
You need the Putty SCP client which is available at their website.

If you want a GUI client for SSH, ssh.com has one.
[http://ftp.ssh.com/pub/ssh/SSHSecureShellClient-3.2.9.exe](http://ftp.ssh.com/pub/ssh/SSHSecureShellClient-3.2.9.exe)

---

### Post by patrick295767 on 2006-05-15
All replies you need are there :[http://ubuntuguide.org/#scpfromubuntu](http://ubuntuguide.org/#scpfromubuntu)
  
Greetings !!

---

### Post by richbarna on 2006-05-15
Was my guide not easy enough? :-
> sudo scp Afile.ZIP otheruser@190.160.1.30:/home/otheruser/

This is a basic console command using default ssh.
Are you using Putty from a Windows Box ? If so, look at this :-
[http://tsb.blogdns.org/2005/09/05/ubuntu-howto-ssh-public-keys-putty/]("http://tsb.blogdns.org/2005/09/05/ubuntu-howto-ssh-public-keys-putty/")

Oh, and you will need to set up your ssh Public/ Private keypair:-
> ssh-keygen -t dsa

---

### Post by cgjones on 2006-05-15
There shouldn't be any reason to scp as root unless you are trying to copy something from or to outside your user's home directory.

---

### Post by richbarna on 2006-05-15
...or to the root directory of the other pc.
root - root
root - user
user to root X

---

### Post by russellnation on 2008-01-25
here is how I sent a large file (3.7 GB) to my desktop because my dvd burner on my notebook was not working :(
>greg@ubuntu:~$ scp '/home/greg/Desktop/LinuxMCE_0704_Quick_Install_DVD.iso' >greg@192.168.0.3:/home/greg/

then the password for the desktop (receiving end)

then wait!
cool and easy. This was the first time I have tried this, and it seemed really easy. 
Thanks to all who posted

---

### Post by nemilar on 2008-01-25
You might find this tutorial to be helpful, if you want to access remote files often:

[http://www.techthrob.com/tech/sshfshowto.php]("http://www.techthrob.com/tech/sshfshowto.php")

It will let you mount a drive over SSH, and act as if it's a local drive (so you can copy files via drag and drop, edit them, etc).

---

