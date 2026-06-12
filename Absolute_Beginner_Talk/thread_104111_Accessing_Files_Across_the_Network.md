---
title: "Accessing Files Across the Network"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by tiris on 2005-12-15
I hope this question is not too advanced for this forum. I just started with Ubuntu Linux about a month ago but have never posted. I have up till now used the documentation to figure things out, but I have not been able to find documentation on this topic.

What I am trying to accomplish is this:
I have an Ubuntu server with LOTS of space and a desktop with LITTLE space (hard disk) and I want to use the SERVER to hold all of my files, and use the desktop to run the programs. 

The problem lies here:
Certain programs can’t find the files for some reason.

For instance:
[LIST]
[*]OpenOffice will open files with no trouble.
[*]XMMS displays the file name and doesn’t play the file (also gives no error about file access).

[*]The GIMP displays this error:

Gimp Message
Could not open '/home/tiris/sftp://tiris@10.103.80.65/home/tiris/DirectoryForLinuxBoxAtWrok/GreetingCard.xcf' for reading: No such file or directory

Gimp Message
Opening '/home/tiris/sftp://tiris@10.103.80.65/home/tiris/DirectoryForLinuxBoxAtWrok/GreetingCard.xcf' failed: Plug-In could not open image

[*]Totem displays this error:
Totem could not play 'sftp://tiris@10.103.80.65/home/tiris/Music/MusicOriginatingFromFolsom/TOOL/Lateralus/TOOL - 01 - The Grudge.mp3'.

There were no decoders found to handle the stream, you might need to install the corresponding plugins
[/LIST]

What do I need to do in order to access the files remotely?

Note: Remote connection was configured using Places>Connect to Server...

Any Suggestions?

---

### Post by NotJustANewbie on 2005-12-15
Why not use [TightVNC]("http://www.tightvnc.com/") or maybe have a try at making a thin client for your large machine: [http://en.wikipedia.org/wiki/Thin_client](http://en.wikipedia.org/wiki/Thin_client)

---

### Post by tiris on 2005-12-15
I don’t think that TightVNC is the right answer. I don’t want to open files on the sever. I want to open files from the server. The difference being that the files are housed on the server and the processing is done on the local machine.

As far as the thin client goes I haven’t really looked into that. I thought that it was for reusing sub par computers or something. All I am trying to accomplish is being able to open and/or edit files on the server without having to download/open/edit/upload.

Does any of this make sense? I am not that good with explanations.

---

### Post by NotJustANewbie on 2005-12-15
Ahhh... I understand.

You have to create a romote connection to your good machine. :)

```
:~$ telnet <ip of your server>
*login as required*
:~$ startx
```

Hope this helps although it might not be the complete explantion, you know where I'm coming from now.

---

### Post by tiris on 2005-12-15
you lost me there.

---

### Post by NotJustANewbie on 2005-12-15
okay, the server is your good machine (with all the data). To find your server's LAN ip, type "ifconfig" in a terminal of the server.

Then go to your client (machine you want to open the files from) and type this into your terminal:

```
:~$ telnet <ip of your server>
*login as required (will be your username and password on the server)*
:~$ startx
```

This should open your xserver on your server and you will be able to access the files like that. Just see if it works, if not, then look here: [http://www.comptechdoc.org/os/linux/howlinuxworks/linux_hlxwindows.html](http://www.comptechdoc.org/os/linux/howlinuxworks/linux_hlxwindows.html)

Hope you get things working!

---

### Post by tiris on 2005-12-15
Something is not right with telnet ssh works fine.

tiris@deskubuntu:~$ telnet 10.103.80.65
Trying 10.103.80.65...
telnet: Unable to connect to remote host: Connection refused
tiris@deskubuntu:~$ ssh 10.103.80.65
tiris@10.103.80.65's password:
Linux subuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Sat Dec 10 12:40:09 2005 from 10.103.80.103
tiris@subuntu:~$ logout
Connection to 10.103.80.65 closed.

---

### Post by curtis on 2005-12-15
Telnetd is probably not running.
I would suggest just using SSH though.

---

### Post by Mr. Electric Wizard on 2005-12-15
Ok, quick answer.
You can view the filenames with the network viewer thingy in Nautilus, but not really much more than that.
What you really need to do is Mount a Samba Share.
Share the file on the remote computer, then you need to run a SmbMount command in the terminal.
Search the forum for smbmount, and you should be able to get it going.  It's not too diffictult.

This is a cool way of doing it because after you have mounted the remote directory, it'll look like the directory actually is sitting on your Ubuntu box...
:p

---

### Post by tiris on 2005-12-15
[QUOTE=NotJustANewbie]okay, the server is your good machine... 

```
:~$ telnet <ip of your server>
*login as required (will be your username and password on the server)*
:~$ startx
```

This should open your xserver ...[/QUOTE]

This doesn’t do what I was looking for. This starts X11 on the server machine...meaning the music will be played on the server. I don’t want the music coming out of the server, I want the music coming out of the desktop.

SAMBA looks complicated. I will look into it but in the mean time isn’t there an easier way to do this?
Can I mount the network drive say to /mnt/server?
I don’t know if I can do this or where to begin.
This is a Linux server I thought that SAMBA is for interface to windows users.

Any Suggestions?

---

### Post by bscbrit on 2005-12-15
Yes you can.  If your server exports the relevant directory using NFS, you can mount it on your local box and it will behave as if the files are on your system.  

/etc/exports should contain the directories that you wish to export, who has what rights with them etc.  Try 'man exports' in a terminal.

Modify your local /etc/fstab to mount the server directory on you local machine:

server://dir/on/server /mount/it/here nfs

Is that more like what you wanted?

---

### Post by Herman on 2005-12-15
>  SAMBA looks complicated. I will look into it but in the mean time isn&#8217;t there an easier way to do this?
Can I mount the network drive say to /mnt/server?
I don&#8217;t know if I can do this or where to begin.
This is a Linux server I thought that SAMBA is for interface to windows users. Hi, check out the instructions on the SSH networking page in my 'sig link' site under this typing and see if that method appeals to you. It's for use between two Linux boxes. I use it all the time and it's extremely simple to set up, and is even very secure, as long as you have a good password set. :D  (Herman)

---

### Post by tiris on 2005-12-15
[QUOTE=Herman]Hi, check out the instructions on the SSH networking page in my 'sig link' site under this typing and see if that method appeals to you. It's for use between two Linux boxes. I use it all the time and it's extremely simple to set up, and is even very secure, as long as you have a good password set. :D  (Herman)[/QUOTE]

Herman,
Thank you for the suggestion, I read your site instructions and have determined that this is not a valid solution. As Mr. Electric Wizard mentioned before Nautilus will let you browse the files, and you can copy them to the local hard drive, but what I need is for the programs to 'think' that the files are local.

Next I will look into NFS then SAMBA to find a valid solution.

Thank you for the suggestion,

---

