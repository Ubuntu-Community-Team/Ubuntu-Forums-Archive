---
title: "Apache Discussion - I want to &quot;chmod 777 /var/www/share&quot;"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2007-01-26
Hello!

This is a question for "apache" Web Server.
_I want to do the following_:

I would like to create a Folder under "/var/www" & name it "share".
That specific Folder I want it to give read/write/execute rights to everyone - i.e. chmod 777!
I want people from the Net come & drop-in their files...
However, I want this Folder to have a limited size!
(I don't want people from the Net to drop-in a 50GB file...)
I want people to be able to drop-in small sized files (Limit Folder "/var/www/share's" Capacity = 1GB total).

_Questions_:
1. Is this possible?
How can I limit the size of this Folder?

2. How will users from the Net upload their Files?
(I have never done this & do NOT know how this is done... - is it through FTP & how is it done? - provide a step-by-step please...)

3. How could I implement a "request" (from the users side) for a username & password (i.e. add authentification) to be able to drop inside that folder, their files?

Thanks.

---

### Post by lamego on 2007-01-26
The type of system you are trying to implement is usually done with FTP, using a public ftp account with write privileges.
I guess you can setup ftp based account management with some of the available ftp services.

---

### Post by dvarsam on 2007-01-26
[QUOTE=lamego]The type of system you are trying to implement is usually done with FTP, using a public ftp account with write privileges.
I guess you can setup ftp based account management with some of the available ftp services.[/QUOTE]

So, you are saying that I can Limit the Folder "/var/www/share's" Capacity to 1GB total, by using FTP?
How is this done?
I understand that you can upload files through FTP, but I have never done this... :oops:
I also thought that to upload files through FTP you need to know the user name & passwords of the Site you are loggiing-in...
I have NOT set any passwords...
So, what do I type in the FTP boxes, requiring those data?

> I noticed the following:

1. IF from the Ubuntu's Menu, I select "Places\Connect to Server..." I get a "Connect to Server" window.
2. Under "Service Type" I have the following FTP options:

a. Public FTP - this requires NO Password
b. FTP (with login) - here I am required to enter a Username & Password to log-in

_Questions_:
1. How do I Limit the "/var/www/share" folder's Capacity to 1GB total?

2. Where (& how) do I setup a Username & Password authentification for the Client users (that log-in through FTP) to be permitted to modify the "/var/www/share" folder's contents?

3. Adding files/folders to a Web Site Server, works simply by drag&dropping files through an FTP connection?

Thanks.

---

### Post by lamego on 2007-01-26
1.
If you are going to use FTP there is no sense in using /var/www, you can use /home/ftp, or /home/user, and you will need to check your FTP Server configuration file for the quota config.

2. FTP allows anonymous access which means you don't need to supply any user and pass.

3. Why do you need the web server at all ? Yes you can drag files if from windows explorer, or you can use an FTP Client (assuming most of your client will be windows users).

---

### Post by dvarsam on 2007-01-26
[QUOTE=lamego]
1. If you are going to use FTP there is no sense in using /var/www, you can use /home/ftp, or /home/user, and you will need to check your FTP Server configuration file for the quota config.

2. FTP allows anonymous access which means you don't need to supply any user and pass.

3. Why do you need the web server at all ? Yes you can drag files if from windows explorer, or you can use an FTP Client (assuming most of your client will be windows users).[/QUOTE]

Sorry, for not knowing much... :oops:

1. You say that I need to check the FTP Server configuration...
I am using "apache" as Web Server.
Are you talking about "apache's" configuration or some other program I need to install?
So, I can NOT do that from within Apache... & I need to install some other program for FTP upload capabilities?

2. Wait one moment...
But IF from Ubuntu's Menu, I select "Places\Connect to Server...", under "Service Type", there is an option for "FTP (with login)"...
Isn't that considered a log-in through FTP?
How come it does NOT exist, while it is called "FTP (with login)"...?

3. Then how do I do this, what program/packages do I need to install in order to be able to do this? Sorry for being too dumb... :)

Thanks.

---

### Post by lamego on 2007-01-26
> 1. You say that I need to check the FTP Server configuration...
I am using "apache" as Web Server.
Are you talking about "apache's" configuration or some other program I need to install?
So, I can NOT do that from within Apache... & I need to install some other program for FTP upload capabilities?
Apache is a web server, a web server is used to serve web pages, it can also be used for serving files but it is not really required if you don't need to provide web contents.
You need to install an FTP Server, search for them on the repositories, there are several options, then you must read the manual for the FTP server that you are going to use, set the options that best fit your needs.

. Wait one moment...
> But IF from Ubuntu's Menu, I select "Places\Connect to Server...", under "Service Type", there is an option for "FTP (with login)"...
Isn't that considered a log-in through FTP?
How come it does NOT exist, while it is called "FTP (with login)"...?
I am not on nautilus right now, but I am almost sure the is an anonymous ftp login option on the Connect to server.

> 3. Then how do I do this, what program/packages do I need to install in order to be able to do this? Sorry for being too dumb... 
```
apt-cache search ftp server
```

---

### Post by dvarsam on 2007-01-26
[QUOTE=lamego]Apache is a web server...
...it can also be used for serving files but it is not really required if you don't need to provide web contents.[/quote]

When you mean "share", does that include "uploading" files?
Cause the word of "share" implies "giving out"...
I want to "upload" -i.e. "drop files inside"...

> You need to install an FTP Server, search for them on the repositories, there are several options, then you must read the manual for the FTP server that you are going to use, set the options that best fit your needs.

IF I wanted to stay/remain/implement this, through "apache", is there a HowTo available to do this?
I would NOT want to have:

1. an apache server
2. an FTP server.

I like things simple.
IF I can do both, with _one_ of these programs, then I would be quite happy!

> I am not on nautilus right now, but I am almost sure the is an anonymous ftp login option on the Connect to server.

You are probably referring to the simple "Public FTP" option (I previously stated...)


> apt-cache search ftp server

Thanks, but I feel it could be better IF I keep my Ubuntu NOT stuffed with many Server software...
That is why I am thinking to install _only_ apache (& not both apache & FTP server on a single machine).
Any ideas?

P.S.> BTW, is it possible to have 2-3 Server applications (e.g. apache & FTP or more) installed on a single Ubuntu machine?

---

### Post by Moldz on 2007-01-26
I've done something similar in the past.  I used VSFTP to provide FTP service to a group of people.  You install the software, create some virtual users, assign a directory for upload like /home/ftp, and viola!

Now you should consider some security.  DO NOT allow anonymous FTP uploads.  You don't want anyone on the net storing questionable files on your box.  

You could also create a separate partition for your FTP folder of 1GB size.  Then no one will be able to fill up all your disk space and crash your machine.  Or you could setup quotas to limit disk space use.

---

### Post by Pobega on 2007-01-26
> I would like to create a Folder under "/var/www" & name it "share".
mkdir /var/www/share
> That specific Folder I want it to give read/write/execute rights to everyone - i.e. chmod 777!
chmod -R 777 /var/www/share
> I want people from the Net come & drop-in their files...
The best thing here in my opinion would be to learn a bit of PHP. You can learn it from [http://php.net/](http://php.net/), specifically [here](http://us2.php.net/manual/en/features.file-upload.php). If you want to do this with FTP though, you'd have to ask someone else.
> However, I want this Folder to have a limited size!
(I don't want people from the Net to drop-in a 50GB file...)
I'm not sure how to put a limited size on the folder, but you can always limit the filesize of the uploaded files.
> I want people to be able to drop-in small sized files (Limit Folder "/var/www/share's" Capacity = 1GB total)
Same as above.

---

### Post by dvarsam on 2007-01-26
[QUOTE=Moldz]I've done something similar in the past.
I used VSFTP to provide FTP service to a group of people.
You install the software, create some virtual users, assign a directory for upload like /home/ftp, and viola!

Now you should consider some security.
DO NOT allow anonymous FTP uploads.
You don't want anyone on the net storing questionable files on your box.[/quote]

I guess that I will have to experiment with this...

[quote=Moldz]You could also create a separate partition for your FTP folder of 1GB size.
Then no one will be able to fill up all your disk space and crash your machine.
Or you could setup quotas to limit disk space use.[/QUOTE]

This is very smart!
And cool too!
I will try to work this out & post back...

Thanks.

---

### Post by dvarsam on 2007-01-26
[QUOTE=Pobega]The best thing here in my opinion would be to learn a bit of PHP. You can learn it from [http://php.net/](http://php.net/), specifically [here](http://us2.php.net/manual/en/features.file-upload.php).[/quote]

Very good link!
Thank you!

[quote=pobega]If you want to do this with FTP though, you'd have to ask someone else.[/quote]

I prefer to stay with "apache", but I will also try FTP for educational purpose.


[quote=pobega]I'm not sure how to put a limited size on the folder, but you can always limit the filesize of the uploaded files.[/QUOTE]

This is a smart workaround!
Very good!
I also liked the idea user "Moldz" suggested - i.e. to create a Partition of 1GB and hopefully link this to the apache web server.
So, users won't be able to upload big files...
At the same time, imposing a limit the way you said, won't be necessary...
But then, I wonder whether that is possible to link apache with a diff partition...
Thanks.

---

