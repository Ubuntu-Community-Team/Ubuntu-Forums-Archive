---
title: "proftpd i want to stop anonoymous"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by treborblack on 2006-09-14
users from downloading from the upload directory. have tried transfering items one at a time from the allow to deny lists and am now lost and confused asto what command will stop downloads. below is the relevent section of my conf file

<Directory /home/ftp/upload>
<Limit  STOR LIST RETR NLST MDTM SIZE STAT CWD XCWD PWD XPWD CDUP XCUP>
AllowAll
</Limit>
<Limit DELE APPE STOU SITE_CHMOD SITE_CHGRP RNFR RNTO MKD XMKD RMD XRMD>
DenyAll
</Limit>
</Directory>

Thanks for reading

---

### Post by davmac on 2006-09-15
I don't use it myself but there is a half decent config howto at [http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-ConfigFile.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-ConfigFile.html)

Hope this helps,

Dave Mac

---

### Post by Slychilde on 2006-09-15
[This]("http://www.ubuntuforums.org/showthread.php?t=79588&highlight=proftp") guide is awesome, if you haven't found it, yet.

I am not 100% sure how to do that, so I'll give you an example, using a modified version of my upload settings.

If you want to flat out deny anon users,  do something like this and add users you want to allow into FTP.

```
<Limit LOGIN>
AllowUser me
AllowUser otheruser
AllowUser otheruse1
DenyALL
</Limit>
```

Directory only.  The DenyAll should block them from looking in there (I think, try it out. it won't hurt)

```
<Directory /some/dir/ftp/upload/>
Umask 022 022
AllowOverwrite on
	<Limit RMD DELE>
	AllowUser me
	DenyAll
	</Limit>

	<Limit READ STOR CWD MKD>
	DenyUser Anonymous
	AllowAll
	</Limit>
</Directory>
```

It can get a bit tedious adding each user if you have a big system, though.

---

### Post by Scorpuk on 2006-09-15
I used [this guide]("http://www.ubuntuforums.org/showthread.php?t=79588") to setup my proftpd server 


I think this might be what you are looking for, for directory rights:

```
<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>
```


on my server there are no annonymous users but for my logon user he can upload to the upload directory and only download from the download directory.

---

### Post by Scorpuk on 2006-09-15
bah got beaten :)

---

