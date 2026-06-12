---
title: "how do i open proftpd?"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2006-04-17
I just installed proftpd but when i type "proftpd" in the terminal, i get a lot of error messages.  Is there a way to turn proftpd on?

---

### Post by aktiwers on 2006-04-17
Did you type:

```
sudo gproftpd
``` 

?

---

### Post by racermike1967 on 2006-04-17
I get the following message:
sudo: gproftpd: command not found

---

### Post by racermike1967 on 2006-04-17
I get the following message when I try to turn on proftpd using the terminal with the command:  proftpd

localhost.localdomain - PRIVS_ROOT: unable to seteuid(): Operation not permittedlocalhost.localdomain - PRIVS_ROOT: unable to setegid(): Operation not permittedlocalhost.localdomain - PRIVS_RELINQUISH: unable to seteuid(PR_ROOT_UID): Operation not permitted
localhost.localdomain - PRIVS_RELINQUISH: unable to setegid(session.gid): Operation not permitted
localhost.localdomain - PRIVS_RELINQUISH: unable to seteuid(session.uid): Operation not permitted
localhost.localdomain - mod_delay/0.4: error opening DelayTable '/var/run/proftpd/proftpd.delay': Operation not permitted
localhost.localdomain - unable to set daemon groups: Operation not permitted
localhost.localdomain - unable to set uid to 65534, current uid: 1000

---

### Post by aktiwers on 2006-04-17
Hmm how did you install it?
I just installed it and " sudo gproftpd" works fine. Also "gproftpd" works fine in the terminal.

Did you install it this way?

Download file.
```
wget http://frodubuntu.free.fr/ubuntu/gproftpd-8.2.2_8.2.2-1_i386.deb
```

Install file.
```
sudo dpkg -i gproftpd-8.2.2_8.2.2-1_i386.deb
```

Run program.
```
sudo gproftpd
```

This works painless for me.

EDIT:
Fixed some spell mistakes.

---

### Post by Wardhog on 2006-04-17
Isn't proftpd the server daemon executable?

If so, it looks like it's complaining about the settings for it.  That's where you'd need to take corrective action.  Do "man proftpd", and hopefully it'll tell you where the config file for proftpd is, and then you can go about fixing those errors you see.

---

### Post by racermike1967 on 2006-04-17
[QUOTE=Wardhog]Isn't proftpd the server daemon executable?

If so, it looks like it's complaining about the settings for it.  That's where you'd need to take corrective action.  Do "man proftpd", and hopefully it'll tell you where the config file for proftpd is, and then you can go about fixing those errors you see.[/QUOTE]


I don't understand how to fix this as you say.  I took a look at the config file using vi but did not know how to fix it.  Do you know how?

---

### Post by racermike1967 on 2006-04-17
[QUOTE=aktiwers]Hmm how did you install it?
I just installed it and " sudo gproftpd" works fine. Also "gproftpd" works fine in the terminal.

Did you install it this way?

Download file.
```
wget http://frodubuntu.free.fr/ubuntu/gproftpd-8.2.2_8.2.2-1_i386.deb
```

Install file.
```
sudo dpkg -i gproftpd-8.2.2_8.2.2-1_i386.deb
```

Run program.
```
sudo gproftpd
```

This works painless for me.

EDIT:
Fixed some spell mistakes.[/QUOTE]


I just did it the way you said and i get the graphical interface but at the same time i also get a GProFTPD information box with the following comment:

Cant open the securitylog here:
 /var/log/secure

What should I do?

---

### Post by Wardhog on 2006-04-17
[QUOTE=racermike1967]Do you know how?[/QUOTE]

No, not off the top of my head.  
- I don't know how you want your FTP server to behave
- I've only ever used vsftpd

Keep in mind, this is guesswork, accuracy not guaranteed:
It looks like you've got entries in the config file that tells proftpd to run as the "root" user.  Try to find where this is set in the config file, and set it to run as some other user, such as yourself, or a purpose-created user called "proftp".

In cases like this, use Google.  Plug "proftpd configuration" into Google, and you should get the information you need.  Granted, it'll be a bit of work to sift through and understand the info, but that's one of the joys of Linux, right? :) 

If you have more specific questions, I (and pretty much everyone else on these forums, I've found) am willing to help.

Also, I have a question : Is gproftpd a version of proftpd with a GUI frontend showing things like current connections and various settings?
Edit : Took some of my own advice and found it on Google.  Cool, a whole suite of graphical frontends for lots of servers.

---

### Post by racermike1967 on 2006-04-17
I got tired of working with proftpd and decided to try a simple one like Pure-FTPd.  What do you think of this compared to the one you are using: vsftpd

---

### Post by Wardhog on 2006-04-17
[QUOTE=racermike1967]I got tired of working with proftpd and decided to try a simple one like Pure-FTPd.  What do you think of this compared to the one you are using: vsftpd[/QUOTE]

Sadly, my experience doesn't cover Pure-FTPd either.

Do you have a specific functional idea for an FTP server, or just experimenting?

---

### Post by racermike1967 on 2006-04-17
I have several large files that I would like my friend to be able to download from me.  That is the main purpose.  The vsftpd in synaptic package manager is an older version that the one available.  How would I install the most recent version?  Could you tell me how to do this step by step?

---

### Post by Wardhog on 2006-04-17
[QUOTE=racermike1967]I have several large files that I would like my friend to be able to download from me.  That is the main purpose.  The vsftpd in synaptic package manager is an older version that the one available.  How would I install the most recent version?  Could you tell me how to do this step by step?[/QUOTE]

Newer version numbers don't necessarily mean better for you.  Stability is what would suit best in your case, so my advice is to stick with the "Ubuntu official" vsftpd.

Once installed, edit the file /etc/vsftpd.conf.  This is a very well commented file, and should be very intuitive to modify.  If you have any questions once you've done this, feel free to post them and hopefully I'll be able to provide help that's a bit more specific.

Modify this file with a view to creating a server that does not allow anonymous logins, runs as a purpose-created user that is not used anywhere else on your system, and tells your friend to stop leeching files upon login just for giggles.

BTW, you want your friend to connect to you via the internet, or is he/she going to come around to your house with a laptop and an ethernet cable?

---

### Post by racermike1967 on 2006-04-17
I would like my friend to connect to me via the internet.  Also, i used this site to help me set up the config file:  [http://www.ubuntuforums.org/archive/index.php/t-91887.html](http://www.ubuntuforums.org/archive/index.php/t-91887.html)

Do you think that it was ok?  Also, after doing this and starting vsftpd, is there a way for me to access my server from the same computer that it is running from?  Since I started vsftpd, how do I know what the address of the site is?

---

### Post by Wardhog on 2006-04-18
[QUOTE=racermike1967]I would like my friend to connect to me via the internet.  Also, i used this site to help me set up the config file:  [http://www.ubuntuforums.org/archive/index.php/t-91887.html](http://www.ubuntuforums.org/archive/index.php/t-91887.html)

Do you think that it was ok?  Also, after doing this and starting vsftpd, is there a way for me to access my server from the same computer that it is running from?  Since I started vsftpd, how do I know what the address of the site is?[/QUOTE]

It should be ok, it's a little loose security-wise, but if you don't leave that server up and running forever, you should be ok.  Shut the vsftpd server down once your friend has gotten the files.

Copy the files you want to give him/her into /home/ftp

Finding the address of your server from the internet can be a little tricky.  You yourself can log into your own ftp server to test it by doing :
ftp localhost

It's likely your computer has an IP address of 192.168.0.1 or similar.  This address will be of no use to your friend.  You need to know what your ISP considers as your address, and give this address to your friend.
To find this address, your router or modem should have some kind of administration software which the external (sometimes called WAN) address can be retrieved from.
The IP address you want will NOT look like :
192.168.0.x
10.x.x.x
or - 
127.0.0.1

It will look a bit more like : 200.136.79.228 (note this is an example only)

EDIT : Or you could just go to : [http://www.whatismyip.com/](http://www.whatismyip.com/)    

Give this address to your friend, and get him to connect to the FTP server at the IP address you specify.
Do you have a router/firewall?  If so, you'll have to Google "port forwarding", to get your router to forward your friend's FTP request to the correct port on your PC.
If your friend wants to connect to a.b.c.d port 21 (standard FTP port), it will arrive at your router, not your PC.  You have to tell your router to forward the request off to <your PC's IP address> port 21.

---

### Post by ayyapan on 2006-05-26
hi,

I had the same problem. I did an ugly fix, but it worked. 

I created an empty secure file:

[INDENT]sudo vim /var/log/secure[/INDENT]

then you just need to write and close the file, just type

[INDENT]:wq[/INDENT]

after it I changed the access to everyone (this is where you create a securitybreech..)

[INDENT]chmod 777 secure.[/INDENT]

This worked for me but I wasnt really concerned about security. I think a better way would be a change owner to the user who starts the deamon, but i'm not sure.

---

