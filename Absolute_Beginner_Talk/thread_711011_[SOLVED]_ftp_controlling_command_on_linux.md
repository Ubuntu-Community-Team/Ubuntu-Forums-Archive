---
title: "[SOLVED] ftp controlling command on linux ?"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by jualansandal on 2008-02-29
Hello all, 
I would like to ask about ftp controlling command on linux, because I want to move files from a folder  in ftp site to another folder(still in the ftp site).

Anyone could give me solution ?, thanks before

---

### Post by jeffus_il on 2008-02-29
Have you got write access to the site?
Can you ssh to the site and use the mv command?
Here is a link about using the ftp rename command:
[http://www.webcom.com/help/ftp/rename.shtml](http://www.webcom.com/help/ftp/rename.shtml)

---

### Post by jualansandal on 2008-02-29
yes, I have write access to the site,
is it necessarily to ssh to the site ?

---

### Post by jeffus_il on 2008-02-29
No, ssh is not necessary, it would have been an easy way to run the move (mv) command and solve your problem.
Did you have a look at the link I posted?

---

### Post by justleen on 2008-02-29
the GUI way:
in nautilus (the filebrowser) you can enter the FTP address, and logon.

Open a second window, logon to the ftp site too

Copy and paste the folders where you want them.


Tip: you can create shortcuts to the FTP site... less typing!

---

### Post by louieb on 2008-02-29
ftp (file transfer protocol) on Linux is the same as ftp on Windows. There are ftp clients such as Filezilla on window or gftp (and many more).
 
You can ftp from the command line in both windows and Linux too. 
use **man ftp** in Linux of** ftp --help** in widows. Lots of options to many to describe here.  

An easy way to do it is Places>Connct to Server>FTP with logon. 
Give it your logon info - and away you go.

---

### Post by jeffus_il on 2008-02-29
The thread originator wants to move a file on the remote machine, read the original post! He knows what ftp is. Is there a remote rename with filezilla? I'm sure he won't want to do a get and put over the internet just to move a file. The move should be done on the remote machine, not over the net. 

Just tested move with filezilla, a right click on the file gives the rename option, and running it does a mv (move) command. The sftp log does it. By the way I tested using an sftp connection, not an ftp one, if someone can test it against an ftp server it would help.

---

### Post by Oldsoldier2003 on 2008-02-29
> **jeffus_il said:**
> The thread originator wants to move a file on the remote machine, read the original post! He knows what ftp is. Is there a remote rename with filezilla? I'm sure he won't want to do a get and put over the internet just to move a file. The move should be done on the remote machine, not over the net. 

Just tested move with filezilla, a right click on the file gives the rename option, and running it does a mv (move) command. The sftp log does it. By the way I tested using an sftp connection, not an ftp one, if someone can test it against an ftp server it would help.
yes you can enter custom commands in filezilla. therefore you can move files without downloading them...

---

### Post by jualansandal on 2008-03-02
thanks all, sorry for leaving this thread .
Could I execute the filezilla command(s) from console, because I would like to make it working continuously(with cronjob).
Maybe I'll read about filezilla first.

---

### Post by jualansandal on 2008-03-02
I just read about FTP Raw Command, could it be applied in linux console ?

---

### Post by jualansandal on 2008-03-03
finaly, I had this solution to move the file :

```

ftp -n ftpsite <<!
quote user myUsrName
quote pass myPassword
binary
rename source_dir/file_toberenamed destination_dir/file_toberenamed
quit
!

```

but I still have question, 
How to move all of the files in a specified folder(maybe looping command in the script)?

thanks

---

### Post by jualansandal on 2008-03-03
anyone ?

---

### Post by jualansandal on 2008-03-03
I made this script to move the file in ftp server internally

```

ftp -n ftpsite <<!
quote user myUsrName
quote pass myPassword
binary
prompt off
for filename in 'ls *.ZIP';do
   rename "/source_dir/${filename}" "/destination_di/${filename}"
done
quit
!

```

but it is failed, anyone could help me please ?

nb: the error is : We only support non-print format,

---

### Post by jualansandal on 2008-03-03
anyone ?
thanks before

---

### Post by jualansandal on 2008-03-03
Still waiting for any help

---

### Post by ghostdog74 on 2008-03-03
you can't do that in an shell FTP here document. anything inside <<EOF till EOF is "considered" FTP commands. FTP protocol doesn't understand for loops. For better control of FTP protocols, you can use languages that support FTP protocols better, like [Perl/]("http://search.cpan.org/~gbarr/libnet-1.22/Net/FTP.pm")Python..even others.
Otherwise, if you stiill want to do in shell, you can do your file renaming locally, then tar the directory up , bring it over to the other side, and then from the other side , untar into the desired directory

---

### Post by jualansandal on 2008-03-03
thanks,
but how about ftp client software, do you have a suggestion one that free and could handle scheduling task for download,upload and moving files in ftp server ?

---

### Post by jualansandal on 2008-03-04
O, I just found an idea, but I dont know whether it will be able to applied or not.
My Idea is to create a file in local folder that contains the filename , so the looping is not using the remote folder as source anymore, but it will be taken from the file(text file containing list of filename that just transferred).

Could it be applied to my problem ?

---

