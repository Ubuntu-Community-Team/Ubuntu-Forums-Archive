---
title: "Incorrect file permissions for home/.dmrc"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by Clay85 on 2006-05-19
I recently re-installed Ubuntu and on first bootup and every bootup after that I've gotten a message something like:

 [quote=ubuntu]$Home/.dmrc has incorrect file permissions and is being ignored. This prevents your session from being saved. The file should be owned by user and have 644 permissions.[/quote]

It wasn't anything I changed, because it was a fresh re-install (I even wrote zeros to disk). I tried to look for that folder, but I can't find it. Maybe I don't have it? What should I do?

---

### Post by S{yndrom}e on 2006-05-19
clay from what you are telling me, i getting that the folder/file .dmrc needs to have 644 permissions.

Well this is what i *think* you should do:

first see if .dmrc exists. Go to your home folder and press crtl+H. Lots of new files should show up. Look for .dmrc. If it is there then proceed

Open up terminal and paste this code


chmod 644 /home/*your user name*/.dmrc

if that doest work just try

chmod 644 .dmrc

Tell me if this fixes ur problems

---

### Post by Ecthelion on 2006-05-19
If you changed your username in your new installation, this could also help:
```
sudo chown *username* /home/*username/.dmrc*
```

---

### Post by Clay85 on 2006-05-19
The file is there, is owned by me, and has 644 permissions. I tried all of your suggestions and I still get this message after I type in my username and password.

:(

If it had 777 permissions would it give me this error? (not that it matters.)

---

### Post by jorn on 2006-05-19
I think so.

---

### Post by aysiu on 2006-05-19
The permissions should be 644, not 777.

---

### Post by Ecthelion on 2006-05-20
I've had those problems too, and finally the problem seemed to be that my home dir had the wrong permissions.
Have you checked the permission of /home/**username**/ ?
I think it should be 755

---

### Post by S{yndrom}e on 2006-05-20
yea /home/username should be 755. It would make since, if the username wasn't accessable then neither would .dmrc. You still havn't told us whiether u have the file .dmrc yet. So yea try chmoding the /username folder. Try using sudo chmod (mabey that will help??). 

Good Luck

---

### Post by Clay85 on 2006-05-22
Okay... I'm not sure if this is what happened (I'm pretty sure it's not, but nothing else is working). Let's pretend I put ```
 sudo chmod -R 777 home
``` into my terminal. 

.dmrc has 644 permissions, but is owned by me (just like the error message says it should be). What 'group' should these files be in? They are currently in 'enzo'. I have no idea what the problem is or really what I'm doing or I could be more helpful. I'll post my la -l and maybe someone can tell what the problem is by that. :(

[quote=Enzo's Terminal]enzo@reboot:~$ pwd
/home/enzo
enzo@reboot:~$ la -l
total 1048
-rwxrwxrwx  1 enzo enzo   4260 2006-05-22 14:48 .bash_history
-rwxrwxrwx  1 enzo enzo    414 2006-05-12 13:17 .bash_profile
-rwxrwxrwx  1 enzo enzo   2272 2006-05-19 03:44 .bashrc
-rwxrwxrwx  1 enzo enzo   2274 2006-05-19 03:43 .bashrc~
drwxrwxrwx  6 enzo enzo   4096 2006-05-16 11:55 .BitTornado
-rwxrwxrwx  1 enzo enzo     73 2006-05-19 10:51 CHOWNENZO
drwxrwxrwx  4 enzo enzo   4096 2006-05-19 02:18 .config
-rwxrwxrwx  1 enzo enzo     53 2006-05-22 14:39 .DCOPserver_reboot__0
lrwxrwxrwx  1 enzo enzo     32 2006-05-22 14:39 .DCOPserver_reboot_:0 -> /home/enzo/.DCOPserver_reboot__0
drwxrwxrwx  2 enzo enzo   4096 2006-05-22 14:49 Desktop
**-rwxrwxrwx  1 enzo enzo     26 2006-05-15 16:50 .dmrc**
-rwxrwxrwx  1 enzo enzo     26 2006-05-12 13:38 .dmrc~
drwxrwxrwx  4 enzo enzo   4096 2006-05-19 02:53 Downloads
-rwxrwxrwx  1 enzo enzo     16 2006-05-12 13:38 .esd_auth
drwxrwxrwx  3 enzo enzo   4096 2006-05-16 21:10 .evolution
-rwxrwxrwx  1 enzo enzo  26826 2006-05-16 20:29 .face
drwxrwxrwx  4 enzo enzo   4096 2006-05-17 19:33 Fonts
-rwxrwxrwx  1 root root      0 2006-05-22 13:41 .fonts.cache-1
drwxrwxrwx  3 enzo enzo   4096 2006-05-15 17:31 .fullcircle
drwxrwxrwx  4 enzo enzo   4096 2006-05-16 21:08 .gaim
drwxrwxrwx  5 enzo enzo   4096 2006-05-22 15:15 .gconf
drwxrwxrwx  2 enzo enzo   4096 2006-05-22 15:24 .gconfd
drwxrwxrwx 21 enzo enzo   4096 2006-05-22 14:38 .gimp-2.2
-rwxrwxrwx  1 enzo enzo      0 2006-05-16 20:42 .gksu.lock
drwxrwxrwx  4 enzo enzo   4096 2006-05-19 04:14 .gnome
drwxrwxrwx 15 enzo enzo   4096 2006-05-22 15:15 .gnome2
drwx------  2 enzo enzo   4096 2006-05-12 13:38 .gnome2_private
drwxrwxrwx  2 enzo enzo   4096 2006-05-19 02:55 .gnome_private
drwxrwxrwx  2 enzo enzo   4096 2006-05-16 20:23 .gpilotd
-rwxrwxrwx  1 enzo enzo      6 2006-05-16 20:23 .gpilotd.pid
drwxrwxrwx  2 enzo enzo   4096 2006-05-22 13:46 .gstreamer-0.10
drwxrwxrwx  2 enzo enzo   4096 2006-05-12 13:38 .gstreamer-0.8
-rwxrwxrwx  1 enzo enzo     86 2006-05-12 13:39 .gtkrc-1.2-gnome2
-rwxrwxrwx  1 enzo enzo    507 2006-05-22 15:15 .ICEauthority
drwxrwxrwx  2 enzo enzo   4096 2006-05-12 14:09 .icons
drwxrwxrwx  3 enzo enzo   4096 2006-05-15 17:00 .kde
drwxrwxrwx  3 enzo enzo   4096 2006-05-12 14:47 .local
drwxrwxrwx  3 enzo enzo   4096 2006-05-15 17:12 .mcop
-rwxrwxrwx  1 enzo enzo     31 2006-05-16 12:20 .mcoprc
drwxrwxrwx  3 enzo enzo   4096 2006-05-12 13:39 .metacity
drwxrwxrwx  5 enzo enzo   4096 2006-05-15 19:01 .mozilla
drwxrwxrwx  4 enzo enzo   4096 2006-05-12 15:06 .mozilla-1.5
drwxrwxrwx  5 enzo enzo   4096 2006-05-12 16:33 .mozilla_backup
drwxrwxrwx 22 enzo enzo   4096 2006-05-19 01:11 Music
drwxrwxrwx  6 enzo enzo   4096 2006-05-19 00:39 My Files
drwxrwxrwx  3 enzo enzo   4096 2006-05-12 13:39 .nautilus
drwxrwxrwx  3 enzo enzo   4096 2006-05-19 00:39 .openoffice.org2
drwxrwxrwx 25 enzo enzo   4096 2006-05-19 04:11 Pictures
drwxrwxrwx  2 enzo enzo   4096 2006-05-22 14:39 .qt
-rwxrwxrwx  1 enzo enzo  10936 2006-05-22 15:18 .recently-used
-rwxrwxrwx  1 enzo enzo      0 2006-05-22 14:48 .sudo_as_admin_successful
drwxrwxrwx  2 enzo enzo   4096 2006-05-16 20:12 .themes
drwxrwxrwx  5 enzo enzo   4096 2006-05-19 12:38 Themes
drwxrwxrwx  4 enzo enzo   4096 2006-05-12 15:31 .thumbnails
drwxrwxrwx  2 enzo enzo   8192 2006-05-22 14:49 .Trash
-rwxrwxrwx  1 enzo enzo 519536 2006-05-12 15:31 ubuntu_user_guide.pdf
drwxrwxrwx  2 enzo enzo   4096 2006-05-12 14:09 .update-notifier
-rwxrwxrwx  1 enzo enzo 258932 2006-05-17 19:18 WINXPbookmarks 5-06.html
-rwxrwxrwx  1 enzo enzo    117 2006-05-12 13:38 .Xauthority
drwxrwxrwx  2 enzo enzo   4096 2006-05-15 17:01 .xine
-rwxrwxrwx  1 enzo enzo  11140 2006-05-16 13:23 .xscreensaver
-rwxrwxrwx  1 enzo enzo    596 2006-05-22 15:15 .xsession-errors
enzo@reboot:~$
[/quote]

I had this problem before I upgraded to Dapper, but I just noticed that the files have "1600777 file permissions". Is that from changing from Breezy to Dapper, or is that what my problem is?

---

### Post by S{yndrom}e on 2006-05-22
if enzo is your user name, then yes it should be like that. Also it is not a good idea to chmod 777 your home directory. Right click on the file itself and in the permissions tabl make it so that is says Owner: (check) Read (check) Write and the rest blank. Because from what you pasted above, it seems .dmrc has 777 permisions

---

### Post by Clay85 on 2006-05-22
I changed it to:
```
-rw-r--r--  1 enzo enzo     26 2006-05-15 16:50 .dmrc

```

And I get the same error message.

Edit: I changed it through the GUI to make sure I'm not screwing up the code, too. :D

---

### Post by S{yndrom}e on 2006-05-22
try chmod 600

---

### Post by Clay85 on 2006-05-22
[QUOTE=Ecthelion]I've had those problems too, and finally the problem seemed to be that my home dir had the wrong permissions.
Have you checked the permission of /home/**username**/ ?
I think it should be 755[/QUOTE]


DUH that was it!

Sorry for being stupid. :( Thanks for your time, though. :)

---

### Post by S{yndrom}e on 2006-05-22
gahhhhhhh!

Well glad you fixed that =P

---

### Post by DSn0wMan on 2006-05-22
I had this problem several weeks ago, and was unable to resolve it untill I re-installed. The whole changing file permissions didn't really work. See this [http://www.ubuntuforums.org/showthread.php?t=168015](http://www.ubuntuforums.org/showthread.php?t=168015) thread for more info.

---

### Post by S{yndrom}e on 2006-05-22
we found out that his permissions on his username folder were out of order :P

---

