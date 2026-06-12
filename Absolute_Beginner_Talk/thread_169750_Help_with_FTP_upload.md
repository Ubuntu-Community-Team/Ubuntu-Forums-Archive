---
title: "Help with FTP upload"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-05-03
it's my first time using ftp with terminal. I can connect to my website easily, but I can't upload anything. 

I don't know where I went wrong ... I simply go to the directory to which I need to upload my files using ```
ftp> cd /public_html/directory
```
the I use put ```
ftp> put /home/isos/Desktop/Thunderousday.mp3
```
As you can see, I am trying to upload an mp3 file, and the terminal outputs the following:
```
local: /home/isos/Desktop/Thunderousday.mp3 remote: /home/isos/Desktop/Thunderousday.mp3
200 PORT command successful
553-Can't open that file: No such file or directory
553 Rename/move failure: No such file or directory

```

Where did I go wrong?
Hope somebody has a solution.
Thanks

---

### Post by cgjones on 2006-05-03
Once you are in the FTP directory that you want to upload to, try this:
```

put /home/isos/Desktop/Thunderousday.mp3 .

```

---

### Post by Isoss on 2006-05-03
That's what I did! I wrote that in my thread ... why it didn't work?

---

### Post by cgjones on 2006-05-03
Did you have the period at the end? Also, if you weren't in the local directory when you started ftp, try this:
```

cd /home/isos/Desktop

```
Then ftp into the remote computer, change to the directory you want and try this:
```

put Thunderousday.mp3 .

```
On a side note, if you have SSH access to the webserver, you could try this:
```

scp /home/isos/Desktop/Thunderousday.mp3 *username*@*hostname*:/public_html/directory/

```

---

### Post by Isoss on 2006-05-04
Hey, I don't have SSH access to the webserver ... what else can I do? It's still not working. I go to the directory in my website, then I use "put" then the destination to the file which is on the Desktop and it keeps giving me the same errors!

---

### Post by pochu on 2006-05-05
Use gFTP:
```
sudo aptitude install gftp
``` Then go to the Internet menu and open gFTP

---

### Post by aysiu on 2006-05-05
Are you using the terminal to **learn** FTP by terminal...? Or do you not realize there are plenty of graphical FTP applications out there?

---

### Post by Isoss on 2006-05-05
Actually I know and I am using GFTP and it's just cool .. but sometimes I prefere commands and I just wanna learn the terminal ways.

---

### Post by patrick295767 on 2006-05-05
think gftp !!  :-) 
That's the best !

---

### Post by pochu on 2006-05-05
[quote=Isoss]Actually I know and I am using GFTP and it's just cool .. but sometimes I prefere commands and I just wanna learn the terminal ways.[/quote]

Have you tried this?
```
man ftp
```

---

### Post by Isoss on 2006-05-06
it worked. I had to be on the same directory from which I needed to upload my files. I think everything is fine now concerning ftp, but still it bugs me that I have to upload file by file ... I know that gftp oders the "put" command for each file in the upload process like this:
put 1.mp3
put 2.mp3
put 3.mp3
etc ...
isn't there any command that can just upload the whole folder? or some way to order these commands manually in terminal as gftp does?

---

### Post by pochu on 2006-05-06
I don't know with ftp, but with other apps, you can do *.mp3 , and it takes all the .mp3 files, or *.* , and it takes all the files...

Have a look and tell us

pochu

---

### Post by Isoss on 2006-05-06
[QUOTE=pochu]Have you tried this?
```
man ftp
```[/QUOTE]

Yes I did, but it wasn't suficient. I know the commands, but sometimes it just needs a hint to know "how" to use each. cuz in manuals you only can get to know each related command does, but doesn't show how! ...

Anyway, it finnaly worked. I am uploading my files now ... and thanks.

---

### Post by tsrjzq on 2006-05-06
gftp is not very well, lftp is better though it is based on command line. with script files, you can do anything you want to.

---

### Post by Isoss on 2006-05-06
[QUOTE=pochu]I don't know with ftp, but with other apps, you can do *.mp3 , and it takes all the .mp3 files, or *.* , and it takes all the files...

Have a look and tell us

pochu[/QUOTE]

This doesn't work. when I do like *.wma it only uploads the first file ordered by name.

---

### Post by souki on 2006-05-06
try this
```
 mput *.mp3
```

if you want a better command line tool, try lftp
it has command expansion, history and much

if you want to automate transfers, try sitecopy

---

### Post by Isoss on 2006-05-06
Thanks guys .. I'll try everything you've suggested. thank you 4 being helpfull, you just make me love linux.
Thanks a lot.

---

### Post by cwaldbieser on 2006-05-06
[QUOTE=Isoss]Thanks guys .. I'll try everything you've suggested. thank you 4 being helpfull, you just make me love linux.
Thanks a lot.[/QUOTE]
From the terminal, you can do this:
```

ftp>bin
ftp> lcd mp3s
Local directory now /home/user/mp3s
ftp> prompt
Interactive mode off.
ftp> mput *.mp3

```
Here I illustrated the lcd (local change directory) command, prompt (turn interactive mode on/off), and mput (upload a bunch of files matching a pattern).

Simple command line ftp doesn't have any recursive folder upload because in the ye old days, you would just tar & gzip your folders before transfering them to save time.  Then you's telnet over to the box and unzip & untar the tarball.

---

