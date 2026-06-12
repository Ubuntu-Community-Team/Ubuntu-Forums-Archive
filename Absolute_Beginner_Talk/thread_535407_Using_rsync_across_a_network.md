---
title: "Using rsync across a network"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Matuku on 2007-08-26
Quick question that I couldn't seem to find an answer for; I want to setup rsync to sync my music collection between my Ubuntu Desktop and my Windows Laptop; I have the network all set up correctly and can see the folder I want to sync to in the network area but am unsure of the path I need to tell rsync to use. Do I need to give a path to the laptop folders and if so what would it be?

---

### Post by kevdog on 2007-08-26
Are you using samba to assist in this connection, or how are you seeing the remote windows folders from your linux box.  If you are mounting the windows share locally as a samba share, then the solution is easy.  More details would be great.

Ive also done this with unison/ssh as my roots using cygwin to another windows box:
root = C:/Documents and Settings/kevin/My Documents
root = ssh://marge/e:/archive/homer/kevin/My Documents

---

### Post by Matuku on 2007-08-26
Sorry should of said, yes using samba to connect between them (didn't realise there was another way really, just did it automatically). I'm not sure what other details you need so please, feel free to ask.

---

### Post by kevdog on 2007-08-26
Ok, Ive really only used unison (which is just a fancy gui/text interface on top of the rsync program), but what are the roots you want to sync?

The man page states:
rsync [OPTION]... SRC [SRC]... [USER@]HOST::DEST

If you have the remote directory mounted as a regular drive, then try
rsync [OPTION] /source_directory /destination_directory

Probably something like
rsync [OPTION] ~/source ~/smb_mount/dest_directory

That probably would work.  I remember way back when playing with rsync, but as the more files and directories I wanted to sync became larger and larger, I switched to unison.  Im not really gui crazy, but it does have a simple gui and the documentation is fairly good.

---

### Post by mostwanted on 2007-08-26
Why don't you use Grsync (the graphical frontend)? It simplifies matters tremendously.

---

### Post by lgambett on 2007-08-26
Issued on the "local" PC;

rsync -avz --delete -e ssh /myfolder/ user@remotepc:/myfolder

Samba is not needed, only openSSH server on the remote pc. With the --delete flag you will erase on the remote directory on the remote pc files that are not present on the local directory on the local pc. the / at the end of the "local" path instructs rsync not to create an additional directory level at destination.

I suggest you to give a good look at the Rsync howto, that is very good and can show you all the capabilities of this multi-function tool.

---

### Post by kevdog on 2007-08-26
Thanks for the post

All I was suggesting is that you need some type of connection to the remote machine.  This can be through samba (making rsync think it is a local directory), or through ssh, but this requires an ssh server to be run on the remote machine -- which then I would recommend cygwin if the remote machine is a windows box.  Im not sure which is more convenient, however for a local area connection, I tend to think samba may be a better alternative since most likely an encrypted connection is not needed and it spares the overhead of ssh, etc.  Also if your remote box is a windows box, uses samba saves you installation of an ssh server on the windows box and modifications of a firewall (these steps are easy, however take some time to go through if you have never done this before)

Any other thoughts on this??

---

### Post by Matuku on 2007-08-26
The main problem is that I don't know where Samba mounts the remote PC too within my file system, any guidance?

EDIT: If I browse to the file system of the laptop by using Places>Network>laptop and then right-click and select properties the location reads as smb://laptop but when using this in rsync it just says it's unable to do.

---

### Post by kevdog on 2007-08-26
What are you using to mount the remote file system.  I know there are a bunch of ways to do this, however I just made a script file that states the following:

#!/bin/bash
#Remote mount of 192.168.1.2
sudo mount -t smbfs -o rw,nosuid,nodev,username=<windows_user>,password=<windows_password>,uid=<local_unix_user>,gid=<local_unix_group>,umask=022 //192.168.1.2/<Windows_Share> /home/kevin/<Windows_Share>

What I did in my home directory: /home/kevin, was make a directory:
mkdir Windows_Share

And then mounted the remote file system to this directory.

Again there are more ways to do it than this, however I just tried to keep it simple.

With the above script, you have to make it executable, and then you can run it at the command line. (./<script_file_name>)

I hope this is satisfactory.

---

### Post by Matuku on 2007-08-26
I'm not entirely sure what I'm using to mount the filesystem; when I installed Ubuntu and connected to the network I set up a samba account (this was a while back I need to remember what I set it up as) and was able to access the files. Don't know much past that.

EDIT: Strange thing, I've just noticed, although I can access all the files, printers, etc on my windows boxes from the linux one, Samba is not a running process.

2nd EDIT: I've also noticed that my windows boxes aren't letting me browse my linux files anymore either; it appears that Samba has disappeared.

---

### Post by jimrz on 2007-08-26
> **Matuku said:**
> I'm not entirely sure what I'm using to mount the filesystem; when I installed Ubuntu and connected to the network I set up a samba account (this was a while back I need to remember what I set it up as) and was able to access the files. Don't know much past that.

EDIT: Strange thing, I've just noticed, although I can access all the files, printers, etc on my windows boxes from the linux one, Samba is not a running process.

2nd EDIT: I've also noticed that my windows boxes aren't letting me browse my linux files anymore either; it appears that Samba has disappeared.

make sure that you have the same workgroup (or domain) name on your your samba server (/etc/samba/smb.conf) that you are using on your win boxes

---

### Post by Matuku on 2007-08-26
Yep both are set as MSHOME the standard.

---

### Post by Matuku on 2007-08-26
Got it working again, can now see and access files on my Linux box from the windows ones but am still no closer to discovering the path needed to transfer files via the commandline (and can't seem to access the Network folder [although technically I don't think its a folder] when browsing for transfer folders in Grsync).

Would it be something like "///matuku_laptop" with more slashes than normal at the beginning or something?

---

### Post by misterspider on 2008-05-14
rsync -avz --delete -e ssh /myfolder/ user@remotepc:/myfolder

I cannot get this to work, I get a message "Name or service not known". Isn't the remotepc name just found at System -> Administration -> System Monitor, on the system tab?

---

