---
title: "user/password problems"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by deakmann on 2008-03-08
Hi,

I`ve managed to get locked out of Ubuntu. My machine was setup with a user called user and the password as password. I changed the password which seems to have caused problems. The next time I booted my machine logged in I got the message:-

user`s $HOME/.dmrc file is being ignored    then something about other users not being able to write to users home directory.

Once logged in I went to user/group admin and noticed that the password showing here was still the old one so I changed it to the new one. The next time I tried to log in it now refuses to accept either password and i`m locked out.

I had earlier tried to setup a new user but got the same message as above when logging in so I gave up and deleted it.

I`m wondering if the problem stemmed from setting up an FTP server , i set it up so I could transfer files from an old Debian install to my home/user directory?

I`ve got to say I find all this user permission stuff a real pain in the *** which is why on my old Debian install I always logged in as root (never had a problem with this in 3 years even though you apparently shouldn`t do it). 

Anyway can some one tell me how to log in and sort out these user issues.

Cheers

---

### Post by prixxie on 2008-03-08
Re: How to change my user name and password

A similar problem here --- can't do anyting without password.  Have tried "root"  Does not work.



I am running Hardy Heron 8.04 from live CD. Keeps asking for live session password to authenticate and to access hard drive. The user name is Ubuntu. I am trying to install on windows XP machine that has crashed due to virus :). Please help. Thank you.

Debbie

---

### Post by The Titan on 2008-03-08
I too had issues like this and it was answered on another forum.  Maybe do a google search.  But anyways, if you do ever manage to get back in you can always enable the root user with sudo passwd root

---

### Post by taurus on 2008-03-08
> **deakmann said:**
> Hi,

I`ve managed to get locked out of Ubuntu. My machine was setup with a user called user and the password as password. I changed the password which seems to have caused problems. The next time I booted my machine logged in I got the message:-

user`s $HOME/.dmrc file is being ignored    then something about other users not being able to write to users home directory.

Once logged in I went to user/group admin and noticed that the password showing here was still the old one so I changed it to the new one. The next time I tried to log in it now refuses to accept either password and i`m locked out.

I had earlier tried to setup a new user but got the same message as above when logging in so I gave up and deleted it.

I`m wondering if the problem stemmed from setting up an FTP server , i set it up so I could transfer files from an old Debian install to my home/user directory?

I`ve got to say I find all this user permission stuff a real pain in the *** which is why on my old Debian install I always logged in as root (never had a problem with this in 3 years even though you apparently shouldn`t do it). 

Anyway can some one tell me how to log in and sort out these user issues.

Cheers

Boot into recovery mode from GRUB menu, at the prompt, change user password again to something easy to remember.

```
passwd user
```
Then, change the ownership/permission of /home/user/.dmrc to you won't get that error/ignore message the next time you log in.

```
chown user:user /home/user/.dmrc
chmod 644 /home/user/.dmrc
```
Now reboot.

```
shutdown -r now
```

---

### Post by deakmann on 2008-03-08
chown user:user /home/user/.dmrc
chmid 644 /home/user/.dmrc

Ok, i`m able to log in now but i`m still getting the home file is being ignored message. The other odd thing is that when I go back into user admin the password is still showing as eight digits (presumably password) not the new password I setup.

I assume you meant chmod by the way as chmid was not accepted.

Cheers

---

### Post by taurus on 2008-03-08
Can you post the output of this command from a terminal, after you log in as user?

```
ls -la ~
```
And you are saying that the password for user didn't change at all even though you've changed it?

---

### Post by deakmann on 2008-03-08
Here is the output. The password did change but once logged in if I go to the user prefs the password is still showing as eight characters long (presumably the old password). The new password I setup is 7 characters long.


total 492
drwxrwxrwx 47 user user   4096 2008-03-08 15:17 .
drwxrwxrwx  6 root root   4096 2008-03-07 16:30 ..
drwx------  3 user user   4096 2008-03-05 20:32 .adobe
-rw-------  1 user user    723 2008-03-07 20:21 .bash_history
-rw-r--r--  1 user user    220 2008-03-04 09:58 .bash_logout
-rw-r--r--  1 user user   2298 2008-03-04 09:58 .bashrc
drwxr-xr-x  5 user user   4096 2008-03-08 13:12 .cache
drwxr-xr-x  9 user user   4096 2008-03-08 13:12 .config
drwx------  2 user user   4096 2008-03-05 21:48 .cups
drwx------  2 user user   4096 2008-03-07 02:31 .dbus-keyrings
drwxr-xr-x  2 user user   4096 2008-03-06 21:00 Desktop
-rw-r--r--  1 user user     28 2008-03-07 16:39 .dmrc
drwxr-xr-x  2 user user   4096 2008-03-04 09:53 Documents
-rw-------  1 user user     16 2008-03-04 09:53 .esd_auth
drwxr-xr-x  8 user user   4096 2008-03-08 13:29 .evolution
lrwxrwxrwx  1 user user     26 2008-03-04 09:58 Examples -> /usr/share/example-content
drwxr-xr-x  2 user user   4096 2008-03-05 20:54 .fontconfig
drwx------  6 user user   4096 2008-03-08 15:17 .gconf
drwx------  2 user user   4096 2008-03-08 15:28 .gconfd
drwx------  3 user user   4096 2008-03-07 02:14 .gftp
drwxr-xr-x 22 user user   4096 2008-03-05 20:54 .gimp-2.4
-rw-r-----  1 user user      0 2008-03-08 15:17 .gksu.lock
drwxr-xr-x  3 user user   4096 2008-03-04 09:53 .gnome
drwx------ 15 user user   4096 2008-03-08 13:29 .gnome2
drwx------  2 user user   4096 2008-03-05 20:42 .gnome2_private
drwxr-xr-x  2 user user   4096 2008-03-07 02:32 .gpilotd
-rw-r--r--  1 user user      5 2008-03-07 02:32 .gpilotd.pid
drwxr-xr-x  2 user user   4096 2008-03-04 10:25 .gstreamer-0.10
-rw-r--r--  1 user user    104 2008-03-08 15:17 .gtk-bookmarks
-rw-r--r--  1 user user     86 2008-03-04 09:53 .gtkrc-1.2-gnome2
-rw-------  1 user user    795 2008-03-08 15:17 .ICEauthority
drwxr-xr-x  2 user user   4096 2008-03-05 22:47 .icons
drwxr-xr-x  3 user user   4096 2008-03-05 20:47 .java
-rw-r--r--  1 user user  11912 2008-03-04 10:23 .lircrc
drwxr-xr-x  3 user user   4096 2008-03-04 09:53 .local
drwx------  3 user user   4096 2008-03-05 20:32 .macromedia
drwx------  3 user user   4096 2008-03-04 09:53 .metacity
drwx------  3 user user   4096 2008-03-05 19:57 .mozilla
drwxr-xr-x  3 user user   4096 2008-03-07 19:10 Music
drwxr-xr-x  4 user user   4096 2008-03-05 20:11 .mythtv
drwxr-xr-x  3 user user   4096 2008-03-08 13:29 .nautilus
drwx------  3 user user   4096 2008-03-07 02:34 .openoffice.org2
drwx------  9 user user   4096 2008-03-08 15:24 .opera
drwxr-xr-x  3 user user   4096 2008-03-07 16:45 Pictures
-rw-r--r--  1 user user    566 2008-03-04 09:58 .profile
drwxr-xr-x  2 user user   4096 2008-03-04 09:53 Public
drwx------  4 user user   4096 2008-03-08 02:15 .purple
drwxr-xr-x  2 user user   4096 2008-03-04 10:26 .qt
-rw-r--r--  1 user user 240514 2008-03-08 13:29 .recently-used.xbel
-rw-r--r--  1 user user      0 2008-03-04 09:54 .sudo_as_admin_successful
drwxr-xr-x  2 user user   4096 2008-03-04 09:53 Templates
drwxr-xr-x  2 user user   4096 2008-03-05 22:47 .themes
drwx------  5 user user   4096 2008-03-07 14:12 .thumbnails
drwxr-xr-x  2 user user   4096 2008-03-07 00:36 transfers
drwx------  7 user user   4096 2008-03-07 16:01 .Trash
drwx------  2 user user   4096 2008-03-06 21:27 .tsclient
drwxr-xr-x  3 user user   4096 2008-03-07 15:55 .ubuntu-tweak
drwxr-xr-x  2 user user   4096 2008-03-05 22:15 .update-manager-core
drwx------  2 user user   4096 2008-03-04 09:53 .update-notifier
drwxr-xr-x  2 user user   4096 2008-03-07 17:29 Videos
drwxr-xr-x  3 user user   4096 2008-03-06 00:41 .vlc
drwxr-xr-x  2 user user   4096 2008-03-07 02:09 .wapi
-rw-------  1 user user    117 2008-03-07 16:39 .Xauthority
-rw-r--r--  1 user user   5504 2008-03-08 15:18 .xsession-errors
user@ubuntu:~$

---

### Post by taurus on 2008-03-08
As long as the new password works, does it really matter if it shows 7 or 8 characters in whatever the preference?  And besides, password is stored, encrypted, in /etc/shadow.

I don't see anything wrong with your $HOME except you allow everybody to write to your $HOME.  So, what is the error message that you get when you log in now?

---

### Post by deakmann on 2008-03-08
Ok, I take it that it`s usual that the password always shows as 8 characters?

The message I get at login is:-

user $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions.User $HOME directory must be owned by user and not writeable by other users.


I also have to remember to change the session to GNOME otherwise it boots into Mythbuntu.

Is the problem because I setup the FTP server to access my HOME directory? 

Cheers

---

### Post by taurus on 2008-03-08
Change the permission of your $HOME from world writable to read-only.

```
chmod 755 /home/user
```
And no, setting up ftp server has nothing to do with that message.  Somehow, you changed the permissions of your $HOME from 755 to 777.  I have vsftpd running on my machine in the office and I can download/upload whatever I want from home and don't have any problem with it.

---

### Post by deakmann on 2008-03-08
This did the trick, thank you for the help

---

