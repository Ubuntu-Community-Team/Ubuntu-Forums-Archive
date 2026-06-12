---
title: "transferring  files from linux/linux on a trusted network"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by ice60 on 2006-08-18
hi, i wanted to ask about this before i totally screw it up.

i want to transfer files from an Ubuntu livecd, which i'm going to use to mount a broken breezy installation that won't boot, and tranfer files to the computer sitting next to it, running SUSE.

they are connected through the ethernet router. which protocol should i use? i was thinking of either scp or ftp (maybe gFTP??). 

and the other thing i really wanted to ask before i start the livecd is, do i need to install NFS or Samba first to use scp or ftp and do i have to edit something like allow.hosts? thanks

---

### Post by Thirsteh on 2006-08-18
I would recommend SCP, as it's generally faster and more secure than FTP, although it may require a bit of reading the help information before you can get a proper command-line for what you want.

FTP and SSH(SCP) do not require any other system processes except their respective daemons. They are both server applications, thus a server daemon needs to be running on the machine you wish to fetch information from -- while you use a client on a client on the target machine to fetch the files.

If you want to log in with a regular username and password while copying through SCP, you have to make sure that all files you are trying to copy are readable by whatever user you're logging in as. Search the forums or Google.com for 'CHMOD' for more information.

Also, bear in mind that the starting path of the path parameter in SCP is the user's home directory (~).

If you just want to get done quick:

On server machine:
sudo apt-get install proftpd
(doesn't matter what process option you choose, just choose what you think is best based on the description the setup gives)

On client machine:
sudo apt-get install gftp
gftp &

Connect to the server's IP with your username and password (not root, you can't log in as that) -- fetch the files.

Voila.

PS: "OpenSSH" and "ProFTPd" are the actual server daemons. "gFTP" is a graphical FTP client only, it does not serve files.

---

### Post by ice60 on 2006-08-18
OK thanks, Thirsteh. i'll try out SCP. i'll just have a look for a tutorial for it. but, i think i've got it. thanks.

i just saw the edit. thanks again :)

---

### Post by Thirsteh on 2006-08-18
No problem.

The man file for SCP should be sufficient for your needs: 'man scp'

I think there are examples there as well, as in most manfiles.

---

### Post by ice60 on 2006-08-18
i can't mount the breezy filesystem! 

this is the output of sudo fdisk -l
```
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3193    25647741    7  HPFS/NTFS
/dev/hda2            3205        3984     6265350    5  Extended
/dev/hda3            3985        4870     7116795   83  Linux
/dev/hda5            3205        3941     5919921    7  HPFS/NTFS
/dev/hda6            3942        3984      345366   82  Linux swap / Solaris

```

and i've attached a picture of the disk mannager.

i made this directory 
```
/mnt/data/
```
i think i want to mount hda3 so this is the command i tried to mount it with
```
sudo mount /dev/hda3/ /mnt/data/ 
```

and this is what it said
```
mount: special device /dev/hda3/ does not exist
       (a path prefix is not a directory)

```i know it says it doesn't exist, but i tried this too
```
sudo mount /dev/hda3/ /mnt/data/ -t ext3
```
and it still won't work. ](*,) 

can someone please show where i went wrong? thanks.

---

### Post by ice60 on 2006-08-18
oh, i did it. i had to take off a / like this
```
sudo mount /dev/hda3 /mnt/data/
```

---

### Post by ice60 on 2006-08-18
i'm having trouble logging in now :rolleyes: i can't work out the username and password for the Dapper livecd. 

does anyone know the username and password for the livecd, please?

i'm using proftpd on the livecd and trying to connect with gtp. i'm using port 21. thanks

[color=blue]EDIT[/color] OK, i just changed the password and i managed to get in. i'm a 1337 Haxor :-\"  :biggrin:

---

### Post by ice60 on 2006-08-18
Linux is so cool :cool: i transferred the whole home directory. i'm going to take the HDD out of the broken breezy install now and install Dapper \\:D/ thanks for all the help, Thirsteh.

---

### Post by Thirsteh on 2006-08-18
Wow, sorry I'm didn't catch the replies in time. Glad you got it working though!

Once again, my pleasure.

And yes, Linux is awesome.

---

