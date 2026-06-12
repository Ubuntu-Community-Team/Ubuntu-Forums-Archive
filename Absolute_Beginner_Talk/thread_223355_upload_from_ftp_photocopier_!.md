---
title: "upload from ftp photocopier !"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by justicerulesok on 2006-07-26
Hello,

We have a photocopier that scans to ftp directories & need to set it up to scan to a location on the Ubuntu machine.

The PC has samba & can be seen a part of the windows network, but when we scan it says unable to access the location.

the destination is smb://ubuntu/MyFiles/scanfolder

I can on any pc go in & put a document in or take one out.

any suggestions?

Justice

PS thanks to everyone who has been answering all my noob posts over the last few days.

---

### Post by halfvolle melk on 2006-07-26
Does the photocopier support/understand the smb-protocol(samba)?

edit:
If I remember correctly Windows implements smb like this:
```
\\ubuntu\MyFiles\scanfolder
```
The photocopier may onderstand that.

In addition, if ftp works, why not use ftp to scan to that folder? I'm sure you can set it up to be accessable with both samba and ftp.

---

### Post by justicerulesok on 2006-07-26
ummm...probably not.

Is there a quickish easyish way of doing this?  my contract runs out on Friday & if I get it to work I get another contract in a few weeks - & if I dodn't - I don't.

---

### Post by bluenova on 2006-07-26
I don't understand? Samba and ftp are 2 differnt things. Just setup an ftp server using something like proftpd to set it up and then point the photo copyer to the path of the ftp server like [ftp://192.168.0.123/path/to/the/storage/place/](ftp://192.168.0.123/path/to/the/storage/place/)

Samba is for accessing a windows network from Linux

---

### Post by justicerulesok on 2006-07-26
I have spent 3 days trying to set up an ftp server and failed.  I installed gftp but don't know what to do with it!

---

### Post by bluenova on 2006-07-26
Sorry, I meant proftpd not gftp sorry.

Take a look here for the howto:
[http://www.ubuntuforums.org/showthread.php?t=79588](http://www.ubuntuforums.org/showthread.php?t=79588)

---

### Post by halfvolle melk on 2006-07-26
> **justicerulesok said:**
> I have spent 3 days trying to set up an ftp server and failed.  I installed gftp but don't know what to do with it!
```
sudo apt-get install pure-ftpd
```
:)

edit: pure-ftp with a dash.

---

### Post by justicerulesok on 2006-07-26
I've tried that and proftp.  I basically have no idea what ftp is.  I seem to get a front end for connecting to something & downloading but no server service running to alow anything else to connect to me.

I guess I'm not explaining it very well because no one (yet) has a solution for me.

EDIT _ I've just installed GProFTPD but how do I run it as root?

---

### Post by halfvolle melk on 2006-07-26
proftp is a client ie. to access a server.
proftpd is a server that serves to clients.

---

### Post by bluenova on 2006-07-26
Both pure-ftp and proftpd and gproftpd (for the GUI front end) are ftp servers. The server is the place that files can be uploaded or downloaded to/from. Any computer that shares files is running some kind of server. The reason for FTP is because thats the protocol your photocopier supports.

The 'd' at the end of proftpd stands for daemon which is the Linux name for server. Sorry a lot of terminology here.

---

### Post by justicerulesok on 2006-07-26
I now have GProFTPD but how do I run it as root?  what is the command?

Do I then put in the IP address etc of the ubuntu pc or the main network server?

---

### Post by bluenova on 2006-07-26
proftpd should load on startup if you do a reboot. For the IP address it should be the IP of the computer with the ftpserver, i.e. the computer you are on now.

---

### Post by bluenova on 2006-07-26
Best thing to do is setup a user called photocopier and set it's location to the place you want the files to be stored. Then on the photocopier, use just the IP address of the ftpserver like [ftp://192.168.0.123](ftp://192.168.0.123) and use the username you just setup, that way the files will be stored in that users folder.

---

### Post by justicerulesok on 2006-07-26
I have rebooted & then restarted & I get this ..

Cant write the new proftpd.conf here:
 /etc/proftpd.conf 
Run GProFTPD as root

Cant open shells for writing /bin/false here:
 /etc/shells 

it then opens but every time I press a button I get the above messege.

I do really apreciate your help.

---

### Post by bluenova on 2006-07-26
Do you get that when the computer boots or when you run gproftpd? If it's just for the setup when running gproftpd run it from the terminal:
```
sudo gproftpd
```

---

### Post by justicerulesok on 2006-07-26
I get the messege when running gproftpd not at startup.

I have now run it through the terminal & got it up (I think) how do I check the service is running ok?

it says offline but when i press the green online button nothing happens

---

### Post by justicerulesok on 2006-07-26
I have just realised that when doing stuff on the GUI the terminal runs in the background it says this...

** (gproftpd:6020): WARNING **: Couldn't find pixmap file: gproftpd.png

(gproftpd:6020): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
VHOST USER WAS CHANGED !!!
End of changed VHOST........
Standard SERVER USER WAS CHANGED !!!
Vhost or anon END
 - no such group 'nobody'
 - Fatal: Group: Unknown group 'nobody'. on line 20 of '/etc/proftpd.conf'
 - no such group 'nobody'
 - Fatal: Group: Unknown group 'nobody'. on line 20 of '/etc/proftpd.conf'
 - no such group 'nobody'
 - Fatal: Group: Unknown group 'nobody'. on line 20 of '/etc/proftpd.conf'
 - no such group 'nobody'
 - Fatal: Group: Unknown group 'nobody'. on line 20 of '/etc/proftpd.conf'
 - no such group 'nobody'
 - Fatal: Group: Unknown group 'nobody'. on line 20 of '/etc/proftpd.conf'
 - no such group 'nobody'
 - Fatal: Group: Unknown group 'nobody'. on line 20 of '/etc/proftpd.conf'
 - no such group 'nobody'
 - Fatal: Group: Unknown group 'nobody'. on line 20 of '/etc/proftpd.conf'
 - no such group 'nobody'
 - Fatal: Group: Unknown group 'nobody'. on line 20 of '/etc/proftpd.conf'
administrator@ubuntu:~$ sudo gproftpd

** (gproftpd:6327): WARNING **: Couldn't find pixmap file: gproftpd.png

(gproftpd:6327): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
 - no such group 'nobody'
 - Fatal: Group: Unknown group 'nobody'. on line 20 of '/etc/proftpd.conf'
administrator@ubuntu:~$


I don't know what it means but it looks bad :-(

I'm not ready to cry yet ... maybe tonight...

---

### Post by bluenova on 2006-07-26
Try running

```
sudo /etc/init.d/proftpd start
```

And the service should then be running. To see if it's working try to log in with a client like gftp

:edit: Hmm, not sure about those errors, but if it works I wouldn't worry about it.

---

### Post by justicerulesok on 2006-07-26
administrator@ubuntu:~$ sudo /etc/init.d/proftpd start
Starting ProFTPD ftp daemon: proftpd - no such group 'nobody'
 - Fatal: Group: Unknown group 'nobody'. on line 20 of '/etc/proftpd.conf'
administrator@ubuntu:~$


I think 'nobody' is the problem lol (am I nobody?)

---

### Post by bluenova on 2006-07-26
According to [this thread](http://www.ubuntuforums.org/showthread.php?t=79588) it should be nobody, but you could try changing it to 'root' 'sudo gedit /etc/proftpd.conf' find 'user nobody' and change to 'user root'

I have to go now, but post back if you still have problems, someone else might be able to help. Also take a good look through the howto thread:
[http://www.ubuntuforums.org/showthread.php?t=79588](http://www.ubuntuforums.org/showthread.php?t=79588)

---

### Post by justicerulesok on 2006-07-26
thanks for your help.  I'm about to go home so I'll give it a try & post tomorrow AM with the results.

cheers :-)

---

### Post by justicerulesok on 2006-07-27
changing user to root instead of nobody eliminated error messeges & gave me 'server is online' :-) :-)  

However :-( when putting the path into the photocopier we get unable to access error.

Could this be something to do with my HDD permissions?

---

### Post by halfvolle melk on 2006-07-27
Yes, it has to do with write permissions. You can try the first option of this link:
[https://help.ubuntu.com/community/FtpServer](https://help.ubuntu.com/community/FtpServer)

---

### Post by justicerulesok on 2006-07-27
my problem is that despite lots of help & how too's I cant change the permissions on my hdd.  I just keep getting errors.

---

### Post by halfvolle melk on 2006-07-27
Please provide concise information. What did you try to do? What exactly is the error message you get upon what action from what how-to? etc.

---

### Post by justicerulesok on 2006-07-27
ok this is the cofig file from inside gproftp 
```
 ServerType standalone
DefaultServer on
Umask 022
ServerName "10.80.70.39"
ServerIdent on "My FTPD"
Bind "10.80.70.39"
ServerAdmin Admin@this.domain.topdomain
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49152 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
User root
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress on
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 30
TransferRate STOR 40
TransferRate STOU 40
TransferRate APPE 40
SystemLog /var/log/secure
#gp_random_username_length 6
#gp_random_password_length 6
#gp_randomize_case lower
#gp_useradd_root_path /home/ftp
#gp_useradd_upload_path /upload
#gp_html_path /var/www/ftp.html
#gp_welcome_name welcome.msg
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol TLSv1
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gproftpd/gproftpd.pem
</IfModule>
<Limit LOGIN>
  AllowUser photocopier
  DenyALL
</Limit>

<Anonymous ~ftp>
 User            ftp
 Group            nogroup
 UserAlias          anonymous ftp
 DirFakeUser on ftp
 DirFakeGroup on ftp
 RequireValidShell      off
 MaxClients         10
 DisplayLogin        welcome.msg
 DisplayFirstChdir      .message
</Anonymous>
```

I am trying to an anonymous user who can read & write (ie scan a file directly from the photocopier to the ubuntu machine).

When i click on the user i get this messege > The user could not be found, this is a bug or /etc/proftpd.conf has errors.
run a syntax check to find out if there are any problems.

the error when i syntax scan this is ```
 - Fatal: Group: Unknown group 'nobody'. on line 20 of '/etc/proftpd.conf'
```

the server service is running ok.

what other info do you need?

Thanks to everyone for trying to help :-)

Justice.

---

### Post by halfvolle melk on 2006-07-27
Did you set a password for photocopier? What happens if you try to access the account from any machine on the same subnet with
```
ftp://photocopier@10.80.70.39
```
with Internet Explorer for instance. By doing so you can check in the server is working at all.
For the anonymous account it should just be
```
ftp://10.80.70.39
```
I'm not to sure about these 'nobody' errors you're getting and I'm not too sure about the config file either. I'd try this one:
[http://www.proftpd.org/docs/configs/anonymous.conf](http://www.proftpd.org/docs/configs/anonymous.conf)

---

