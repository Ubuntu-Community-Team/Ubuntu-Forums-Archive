---
title: "Ad folder to FTP Server?"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-04-26
Hello guys!

I set up a FTP server not too long ago. I have created a user.

Now when I login to the server, this user gets to this folder:
/home/ftp/

Now, I have a 60gb folder on my other Harddisc. This is the folder:
/media/sda1/Mp3

Now I have set the permition to read and execute on the mp3 folder, and on all subfolders and files in it.

How do I make my user in /home/ftp/ 
View and download files from my mp3 folder, without copying the folder?

I want to make something like a shortcut to /media/sda1/Mp3 inside /home/ftp/, so that the user that logs on can download the files.

Is this possible? Or anything else similar that does the same?

EDIT:

Ups forgot to say, I use gproftpd. 
Thanks

---

### Post by nanotube on 2006-04-26
you can make a symbolic link, with the following commands:
```
cd /home/ftp
ln -s /media/sda1/Mp3
```
first command takes you to /home/ftp, then ln -s makes a symbolic link to your folder. a link is like a shortcut in windows. :)

---

### Post by aktiwers on 2006-04-26
Thanks this almost worked!
Now when I login the folder is there. But when I try to open it, it gives me an error messege.

It says:
> Alert

550 /Mp3: No Such file or directory

But when I use Nautilus it works as a shortcut.

Any ideas?

---

### Post by aktiwers on 2006-04-27
No one?

---

### Post by frodon on 2006-04-27
**Be careful** aktiwers using symbolink link to put a folder/partition inside a FTP server is a really bad idea on the security level and this feature is often disabled by many FTP servers because of that.
I strongly advice you to do it that way :

1- create a directory under /home/ftp called MP3 : ```
sudo mkdir /home/ftp/MP3
```

2- mount your MP3 directory in this directory : ```
sudo mount -o bind /media/sda1/Mp3 /home/ftp/MP3
``` That's all, if you have already some files in the /home/ftp/MP3 they will not be overwritten by the mount command so don't worry this command don't overwrite anything.

---

### Post by aktiwers on 2006-04-27
Thanks a lot Frodon! This worked out easly! :)

How do I delete the old mp3 folder, that was just a link?

---

### Post by frodon on 2006-04-27
A rm command will erase the link (and just the link ;) ), so delete it as usual.

---

### Post by aktiwers on 2006-04-27
Thanks! :)

Now I have one last question.

It seams like its onlu the 2 PC's in my appartment, that can connect to the FTP server. 

I use Mozilla to connect to the IP and type in username and password.
But when I send the link to my friend, it says the server doesnt contain any data?

Why is this?

---

### Post by frodon on 2006-04-27
When you say that i think first to a firewall/router problem.

If you have a router check that the port used by the ftp server is opened and allow tcp packets.
If you just run a software firewall like firestarter do the same.

Which FTP server do you use, is it an anonimous access or an access with username and password ?

---

### Post by aktiwers on 2006-04-27
Oh I just called my ISP, and they told me its because I share my IP with all the other people here. So I need to order my own IP address, then it will work. 

Now Im behind  a firewall, from them.
Thanks for the help :)

---

### Post by apricot on 2008-02-29
How to mount that point on boot-up?

---

### Post by aktiwers on 2008-02-29
Could you be a little more specific? :)
Mount what point, and from where?

---

### Post by apricot on 2008-03-01
How to mount this point in fstab:?

> **frodon said:**
> **Be careful**
2- mount your MP3 directory in this directory : ```
sudo mount -o bind /media/sda1/Mp3 /home/ftp/MP3
``` That's all, if you have already some files in the /home/ftp/MP3 they will not be overwritten by the mount command so don't worry this command don't overwrite anything.

---

### Post by apricot on 2008-03-01
The second question is:

How to make /home/ftp/MP3 folder accessable for anonymous user connection. In my case there is a mount point on /var/ftp/Mp3 to /media/hda5/Mp3, and it is not accessable for anonymous account, it says: Permission denied. Only /var/ftp folder is accessable for anonymous, is there a way to change it?


P.S. The shared mp3 folder is just for example.

---

