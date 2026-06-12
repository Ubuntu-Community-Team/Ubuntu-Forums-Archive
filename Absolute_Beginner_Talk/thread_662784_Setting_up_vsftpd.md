---
title: "Setting up vsftpd"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by Newmaniese on 2008-01-09
I believe I finally have vsftp installed and working securely, but it took me one heck of a time to figure it out and find a reference. The reason I am posting this here is for 2 reasons: 1) to share my new found knowledge of vsftp and 2) for the experts in the forum to review my steps and make sure they are, in fact, as secure as they can be.

My goal with vsftp was to create an ftp user that was chrooted (jailed) in a directory in my apache http folder and all communication to go through port 21. This username and password should not have shell or any other access on the computer. So to start I installed the program: ```
sudo apt-get install vsftpd 
```

This even launched the deamon for me. Immediately I wanted to change a few things on the config so stop the vsftp process and edit the config file:
```

sudo /etc/init.d/vsftpd stop
sudo vi /etc/vsftpd.conf

```

I changed these lines:```

# Turn off anonymous users
anonymous_enable=NO

# Turn on local users
local_enable=YES

# Users should be able to write
write_enable=YES

# I don't give access to port 20 so turn this off 
connect_from_port_20=NO

# chroot everyone
chroot_local_user=YES

```

With this configuration anyone who is a local computer user can log into ftp. I don't even want to tempt my web developers with ssh access to login with ftp and send out all their information with clear text. I want a dedicated ftp user with a home directory in the httpdocs folder and no shell access and set his password.
```

sudo useradd -d /var/www/path/to/chrooted/home/dir -s /usr/sbin/nologin ftpuser
sudo passwd ftpuser

```
Remember to change the permissions of the home dir to allow ftpuser to read and write into it.
```

sudo chown /var/www/path/to/chrooted/home/dir -R ftpuser
sudo chmod 775 /var/www/path/to/chrooted/home/dir

```
I only want that user to be able to login into the ftp so I create the file vsftpd.userlist in the /etc/ folder:
```

sudo vi /etc/vsftpd.userlist

```
and add the user/users I want to give ftp access
```

ftpuser

```
save the file and open the vsftpd.conf file again:
```

sudo vi /etc/vsftpd.conf

```
and add these lines to the end of the file
```

# the list of users to give access
userlist_file=/etc/vsftpd.userlist
# this list is on
userlist_enable=YES
# It is not a list of users to deny ftp access
userlist_deny=NO

```
'man vsftpd.conf' can give you a better handle on the different options in vsftpd.conf. 

Start up the vsftpd:
```

sudo /etc/init.d/vsftpd start

```

So now vsftpd is configured and you try to login with ftpuser and wait you get a permission denied error. What the?

The problem is with the shell set to /usr/sbin/nologin isn't letting the user log in, but I still don't want this user to have shell access. The trick here, and I would love an explanation as to why this isn't already done, is to add the nologin shell to the /etc/shells file:
```
sudo vi /etc/shells
```
It should look something like
```

...
/bin/ksh
/usr/bin/rc
/usr/bin/tcsh
/bin/tcsh
/usr/bin/esh
/bin/dash
/bin/bash
/bin/rbash

```
add a new line for the nologin shell:
```

/usr/sbin/nologin

```

There it is that is it. You set up a ftp user without shell access chrooted into a folder. 
To add to my organization I added the user to a group called ftpusers:
```

sudo addgroup ftpusers
sudo usermod -Gftpusers ftpuser

```
Hope that helps anyone with a similar problem as I had.

---

