---
title: "Transfere files via FTP"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-04-26
with terminal, I could reach to the public_html folder of my site.

1. I need to upload some files from my PC using terminal. what is the command?
2. is there any FTP program that can browse the folders graphically and help me do all the ftp work?

Thanks for your help.

---

### Post by nanotube on 2006-04-26
for commandline work, you can use command "ftp" from a terminal, or command "lftp". if your remote server has ssh, you are better off using "sftp" since that is encrypted and thus more secure.

for graphical stuff, you can install package "gftp", that will give you a nice gui client. to install the package, run
```
sudo apt-get install gftp
```
have fun. :)

---

### Post by jazzmuzik on 2006-04-26
FTP is unsafe for uploading. Use rsync with ssh instead. It's good.

```
rsync -avz -e ssh /files/to/upload/* youracct@yourisp.com:public_html/
```

Or try to use sftp (secure ftp).

---

### Post by Isoss on 2006-04-26
alright ... I am new to linux ... what is encrypted? can u explain this sftp thing?

and I would also know how to do the upload files to public_html ... I used ftp and connected to the server successfully. so I need to know the commands that will allow me to do all the FTP work with commands.

and thanks for the program. :)

---

### Post by jazzmuzik on 2006-04-26
Encrypted means the data is scrambled at your computer, sent to the remote computer and then unscrambled. Encrypted communications provides a bit of protection from both people on your local network or between computers on the larger Internet.

FTP is an old and good standard for transferring files. SFTP is the same as FTP but it uses a secure (scrambled/encrypted) method of transferring data. So it's better.

The same thing is true of telnet, which was used to log into remote computers. Almost nobody uses telnet anymore because it became too easy to hack. Instead people use ssh for remote logins.

nanotube mentioned the gftp program, which will work, but it also has an SFTP mode and I suggest you use that.

---

### Post by nanotube on 2006-04-26
[QUOTE=Isoss]alright ... I am new to linux ... what is encrypted? can u explain this sftp thing?

and I would also know how to do the upload files to public_html ... I used ftp and connected to the server successfully. so I need to know the commands that will allow me to do all the FTP work with commands.

and thanks for the program. :)[/QUOTE]

the basic commands for any command line ftp are "get" to get a file from remote machine, and "put" to upload a file to remote machine. will work on ftp as well as sftp. for more info, you can try "man ftp" to get a manual.

but just like others suggest, for security purposes it is really better to use sftp rather than plain ftp, if you can.

---

### Post by patrick295767 on 2006-04-27
mc

or 

gftp 

are the 2 very best !

(kbear works very fine too but can be buggy... )

---

### Post by Isoss on 2006-04-27
Thanks guys .. that was really sufficient and useful.
Thanks again.

---

### Post by Isoss on 2006-04-27
Ok ... I went to terminal and typed sftp and the output were as following:
```
root@ubuntu:/home/isos# sftp nourelalam.org
Connecting to nourelalam.org...
ssh: connect to host nourelalam.org port 22: Connection refused
Couldn't read packet: Connection reset by peer

```

WHY IS THAT?! when I type ftp it asks for logins and it connects to the server! ... so why sftp isn't working the same way?

---

### Post by nanotube on 2006-04-27
apparently they are not running an ssh server there, so you cannot use sftp. i guess you are stuck using plain ftp, then. or even better, email the admin of the server, and ask if they are running ssh, and if not, why not. :)

---

### Post by Isoss on 2006-04-27
Ok, I will contact my server ... thanks.

---

