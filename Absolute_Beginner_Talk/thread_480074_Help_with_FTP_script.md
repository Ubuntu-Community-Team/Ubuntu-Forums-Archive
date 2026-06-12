---
title: "Help with FTP script"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by dav-coms on 2007-06-21
Hey guys,

This has been frustrating me out all today!!!! I need to make a script or something to connect to a ftp server, change the ftp directory, delete a file, upload a updated version (as the ftp service that my hosting uses has problems with overwriting files on ftp), close connection, quit. I have tried all sorts of different things but when its nearly works there always is a problem!

So if you could help me out that would be excellent!!!

Thanks,
David.

---

### Post by st0nes on 2007-06-21
Hi there.  Try this:-

```
JOBLOG=<*You need a log file*>
export JOBLOG
remoteHOST=<*Remote host name or IP*>
remoteUSERID=<*Remote log in user ID*>
remotePASSWD=<*password to log into remote machine*>
export remoteHOST remoteUSERID remotePASSWD

echo "user $remoteUSERID $remotePASSWD\n cd <*remote directory you want to change to*>\n
delete <*file you want to delete*>\n put <*file you want to transfer*>" | ftp -n -v $remoteHOS
T > $JOBLOG

ftp_cnt=`grep "226 Transfer complete." $JOBLOG | wc -l`

if [ $ftp_cnt = 1 ]
then
      echo " FTP was successful to server " $remoteHOST >> $JOBLOG
else
    echo " FTP FAILED to server " $remoteHOST >> $JOBLOG
     exit 1
fi
```

You need to replace the italic text in angle brackets with your own filenames &c (without the angle brackets)

Hope this works.

Cheers

---

### Post by dav-coms on 2007-06-21
I fixed it up with my own setting and it just didn't work! It made a log file and just said couldn't connect to ftp server. Though when I run it in the terminal it comes up with 4 "Not connected." and a "10: T: not found". I can connect to the ftp manually through windows and ubuntu linux and I'm running ubuntu 6.10 if that helps in anyway!

Thanks again!

---

### Post by st0nes on 2007-06-21
Could you post your completed script and the contents of the log file?

---

### Post by st0nes on 2007-06-21
I'll be offline for an hour or so, but will look again when I get home.

---

