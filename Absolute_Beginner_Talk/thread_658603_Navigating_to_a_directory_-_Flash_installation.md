---
title: "Navigating to a directory - Flash installation"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by TracyO on 2008-01-04
I know this has got to be simple, but I just can't figure it out.  I'm trying to install Adobe Flash.  I downloaded the file, it's in my tmp directory, but I do not know how to "navigate" to it.  This is the latest command I've tried.  What am I missing?

tracy@tracy-laptop:~$ cd/home/tracy/tmp/install_flash_player_9_linux/flashplayer-installer
bash: cd/home/tracy/tmp/install_flash_player_9_linux/flashplayer-installer: No such file or directory

Thanks,
Tracy

---

### Post by taurus on 2008-01-04
Missing a space.

```
cd /home/tracy/tmp
-or-
cd ~/tmp
ls -la
```

Have you unpacked it?

---

### Post by stump138 on 2008-01-04
there is a space in the word flash, you also need to add a space after cd, Please make sure that if you have any capitol letters, they are capitalized in your console commands :)

```
cd /home/tracy/tmp/install_flash_player_9_linux/flashplayer-installer
```

also make sure the directories are valid so take it slow:)

```
cd /home/tracy/tmp
```

```
cd /install_flash_player_9_linux
```

so on and so forth so you can isolate the error:)

---

### Post by RomeReactor on 2008-01-04
Hi. You an do it like this:
```
cd /home/tracy/tmp/install_flash_player_9_linux
```
then:
```
sudo ./flashplayer-installer
```

Or download [this package]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466") and double click on it to install Flash.

You can install Flash from the repositories, but at the moment the package has a bug, which this version has corrected.

---

### Post by TracyO on 2008-01-04
I thought I unpacked it, but maybe that's part of the problem.  in my tmp directory, it's still there as install_flash_player_9_linux.tar.gz.  I've clicked extract, but nothing changes.  

By the way, thank you for the "cd /" tip.  That's key.

---

### Post by TracyO on 2008-01-04
Wait, I was mistaken.  I do still have the downloaded file, but there is also a folder of the same name, minus tar.gz in the tmp folder.  

This is the latest.
tracy@tracy-laptop:/tmp$ /install_flash_player_9_linux
bash: /install_flash_player_9_linux: No such file or directory
tracy@tracy-laptop:/tmp$ 
 
Is *is* there.  Am I mistyping somewhere?

---

### Post by RomeReactor on 2008-01-04
Use **cd** to go inside the directory:
```
cd install_flash_player_9_linux
```
and to install it:
```
sudo ./flashplayer-installer
```

---

### Post by mick222 on 2008-01-04
I'm a newbie but ussually if i need a file i navigate to in gnome then drag it to the terminal . Is that ok .

---

### Post by TracyO on 2008-01-04
tracy@tracy-laptop:~$ cd /home/tracy/tmp
bash: cd: /home/tracy/tmp: No such file or directory

---

### Post by taurus on 2008-01-04
Are you sure you've saved it to your ~/tmp directory?

What's the output of this command from a terminal?

```
ls -la ~
```

---

### Post by TracyO on 2008-01-04
tracy@tracy-laptop:~$ ls -la
total 868
drwxr-xr-x 41 tracy tracy   4096 2008-01-04 20:02 .
drwxr-xr-x  3 root  root    4096 2007-11-11 18:31 ..
-rw-------  1 tracy tracy   1950 2008-01-04 20:13 .bash_history
-rw-r--r--  1 tracy tracy    220 2007-11-11 18:31 .bash_logout
-rw-r--r--  1 tracy tracy   2298 2007-11-11 18:31 .bashrc
drwxr-xr-x  3 tracy tracy   4096 2007-11-11 23:33 .cache
drwxr-xr-x  5 tracy tracy   4096 2007-11-23 13:36 .config
drwx------  2 tracy tracy   4096 2008-01-02 20:08 .dbus-keyrings
drwxr-xr-x  5 tracy tracy   4096 2008-01-04 19:04 Desktop
-rw-------  1 tracy tracy     28 2008-01-04 19:03 .dmrc
drwxr-xr-x  3 tracy tracy   4096 2007-12-21 00:29 Documents
-rw-------  1 tracy tracy     16 2007-11-11 23:34 .esd_auth
drwxr-xr-x  8 tracy tracy   4096 2008-01-04 07:25 .evolution
lrwxrwxrwx  1 tracy tracy     26 2007-11-11 18:31 Examples -> /usr/share/example-content
drwxr-xr-x  2 tracy tracy   4096 2007-11-25 18:28 .fontconfig
drwx------  4 tracy tracy   4096 2008-01-04 19:03 .gconf
drwx------  2 tracy tracy   4096 2008-01-04 20:17 .gconfd
drwxr-xr-x 22 tracy tracy   4096 2007-12-10 22:29 .gimp-2.4
-rw-r-----  1 tracy tracy      0 2008-01-03 08:17 .gksu.lock
-rw-r--r--  1 tracy tracy    399 2007-12-23 21:12 .gnomad2rc
drwxr-xr-x  3 tracy tracy   4096 2007-11-11 23:34 .gnome
drwx------ 19 tracy tracy   4096 2008-01-04 07:25 .gnome2
drwx------  2 tracy tracy   4096 2007-11-11 23:33 .gnome2_private
drwxr-xr-x  4 tracy tracy   4096 2007-11-23 22:39 gpodder-downloads
drwxr-xr-x  2 tracy tracy   4096 2007-11-23 21:59 .gstreamer-0.10
-rw-r--r--  1 tracy tracy    108 2008-01-04 19:03 .gtk-bookmarks
-rw-r--r--  1 tracy tracy     87 2007-11-11 23:33 .gtkrc-1.2-gnome2
-rw-------  1 tracy tracy   1539 2008-01-04 19:03 .ICEauthority
drwxr-xr-x  2 tracy tracy   4096 2007-11-11 23:35 .icons
drwxr-xr-x  3 tracy tracy   4096 2007-11-29 22:15 .java
drwxr-xr-x  3 tracy tracy   4096 2007-11-11 23:33 .local
drwx------  3 tracy tracy   4096 2007-11-23 21:39 .macromedia
drwx------  3 tracy tracy   4096 2007-11-11 23:33 .metacity
drwx------  3 tracy tracy   4096 2007-11-11 23:41 .mozilla
drwxr-xr-x 26 tracy tracy  12288 2008-01-02 19:00 Music
drwxr-xr-x  3 tracy tracy   4096 2008-01-04 07:25 .nautilus
-rw-r--r--  1 tracy tracy 352256 2007-12-31 19:55 nautilus-debug-log.txt
drwx------  3 tracy tracy   4096 2007-12-31 19:54 .openoffice.org2
drwxr-xr-x  9 tracy tracy   4096 2007-12-30 20:46 Pictures
drwxr-x---  8 tracy tracy   4096 2007-12-02 14:54 Podcasts
-rw-r--r--  1 tracy tracy    566 2007-11-11 18:31 .profile
drwxr-xr-x  2 tracy tracy   4096 2007-11-11 23:33 Public
drwx------  5 tracy tracy   4096 2007-12-28 12:43 .purple
-rw-------  1 tracy tracy  25384 2007-12-31 19:54 .recently-used
-rw-r--r--  1 tracy tracy 254838 2008-01-04 20:02 .recently-used.xbel
drwxr-xr-x  2 tracy tracy   4096 2007-12-16 15:21 .serpentine
-rw-r--r--  1 tracy tracy      0 2007-11-12 00:20 .sudo_as_admin_successful
drwxr-xr-x  2 tracy tracy   4096 2007-11-11 23:33 Templates
drwxr-xr-x  3 tracy tracy   4096 2007-12-04 15:25 .themes
drwx------  5 tracy tracy   4096 2007-11-20 06:11 .thumbnails
drwxr-xr-x  5 tracy tracy   4096 2007-12-04 15:57 .tomboy
-rw-r--r--  1 tracy tracy  10125 2007-12-04 16:15 .tomboy.log
drwx------  6 tracy tracy   4096 2008-01-04 20:15 .Trash
drwxr-xr-x  2 tracy tracy   4096 2007-11-23 20:44 .update-manager-core
drwx------  2 tracy tracy   4096 2007-11-11 23:33 .update-notifier
drwxr-xr-x  2 tracy tracy   4096 2007-11-11 23:33 Videos
drwxr-xr-x  3 tracy tracy   4096 2007-11-23 20:27 .vlc
drwxr-xr-x  2 tracy tracy   4096 2007-12-10 18:26 .wapi
-rw-------  1 tracy tracy    123 2008-01-04 19:03 .Xauthority
-rw-r--r--  1 tracy tracy   5031 2008-01-04 19:34 .xsession-errors

---

### Post by taurus on 2008-01-04
You don't have a tmp directory in your $HOME.  So, you probably have saved it to Desktop then.

```
cd ~/Desktop
ls -la
```

---

### Post by Thunar on 2008-01-04
I think the problem may be that the "tmp" directory is not in your "home" directory. Try this:

Step 1:

Open Terminal, it should look like this:

tracy@tracy-laptop:~$

Step 2:

Change the directory in terminal with this command:

```
cd /tmp/install_flash_player_9_linux/
```

it should look like this:

tracy@tracy-laptop:/tmp/install_flash_player_9_linux/$

Step 3:

Install Flash Player with this command:

```
sudo ./flashplayer-installer
```

good luck! :)

---

### Post by TracyO on 2008-01-04
I don't know what's different about my directory system, but my /tmp directory is not in home.  When I'm in terminal, I get results from typing in /tmp with no home directory or user.  The flash directory is in my tmp folder, and ideally it should be cd /tmp/install_flash_player_9_linux, as that is the exact name of the directory.

When I tried mick's suggestion, I got:
tracy@tracy-laptop:~$ '/tmp/install_flash_player_9_linux' 
bash: /tmp/install_flash_player_9_linux: is a directory

However, from typing in the command, this is the response:
tracy@tracy-laptop:~$ cd /tmp/install_flash_player_9_linux/flashplayer-install
bash: cd: /tmp/install_flash_player_9_linux/flashplayer-install: No such file or directory
(per Adobe's instructions, as follows:
   1.  Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
   4. In terminal, navigate to this directory and type **./flashplayer-installer** to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.)

---

### Post by mick222 on 2008-01-04
try copying and pasting thuners commands in terminal.
cd /tmp/install_flash_player_9_linux/

---

### Post by mick222 on 2008-01-04
then 
sudo ./flashplayer-installer

---

### Post by TracyO on 2008-01-04
That was it Thunar.  All this time, I've been missing the final backslash.  Unfortunately, now I'm stuck in the installation process.  Terminal is looking for a valid installation path for mozilla.  The given example "/usr/lib/mozilla" (with or without a space in front) does not work.  I've browsed my directories, and I've searched the computer for "mozilla" with no results.  Any ideas?

This is much more of a hand-holding event than I thought it would be.  Thanks for the patience.

---

### Post by Thunar on 2008-01-04
oh ya, I forgot about that part, haha.

Firefox is in this directory:

/usr/lib/firefox/

:)

---

### Post by TracyO on 2008-01-04
Now that I have established tmp/install_flash_player.... as my directory, how do I get rid of that?

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla):  /usr/lib/mozilla

WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): usr/lib/firefox

WARNING: /tmp/install_flash_player_9_linux/usr/lib/firefox is not a directory.


Also, from manually checking my folders, there is no firefox folder nor file in my lib folder.

---

### Post by RomeReactor on 2008-01-04
You missed the first backslash the second time around:
```
/usr/lib/firefox
```

EDIT: Are you using Kubuntu?

---

### Post by TracyO on 2008-01-04
Still nothing. [PHP]Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/mozilla

WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla):[/PHP]
 
And by the way, I now understand that it timed out or something and went back to the terminal command it was on.  I can get back into the installation with no problem.

I'm using Ubuntu 7.10.

---

### Post by bwtranch on 2008-01-04
Yeah,it's like bash, ah trash:) No just kidding. I don't know how many times I've wanted to trash the bash.

Best way to go if you get lost is / that is root then ls then cd to the next directory then ls then cd to that directory, etc.

desktop and Desktop are two different things, so say for example:

jim@jim-desktop:~$ cd /
jim@jim-desktop:/$ ls
bin                                  dev         lib         mnt   srv  vmlinuz
boot                                 etc         lib32       opt   sys
cdrom                                home        lib64       proc  tmp
cupswrapperdcp1000_1.0.2-1_i386.deb  initrd      lost+found  root  usr
cupswrapperDCP1000-1.0.2-1.i386.rpm  initrd.img  media       sbin  var
jim@jim-desktop:/$ cd home
jim@jim-desktop:/home$ ls
jim
jim@jim-desktop:/home$ cd jim
jim@jim-desktop:~$ ls
Desktop    Examples  My GCompris  Public     Videos
Documents  Music     Pictures     Templates
jim@jim-desktop:~$ cd Desktop
jim@jim-desktop:~/Desktop$ ls
cupswrapperDCP1000-1.0.2-1.i386.deb  dcp1000lpr-1.1.2-1.i386.deb
jim@jim-desktop:~/Desktop$ 

:)

---

### Post by TracyO on 2008-01-04
I realized my mistake.  I went back and used /usr/lib/firefox instead of mozilla.  I should really have waited to do this until it was not the end of the week.  I apologize for my own errors.  Thank you to all for your help and your patience.  I really do appreciate it.

---

### Post by Thunar on 2008-01-04
> **TracyO said:**
> Now that I have established tmp/install_flash_player.... as my directory, how do I get rid of that?

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla):  /usr/lib/mozilla

WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): usr/lib/firefox

WARNING: /tmp/install_flash_player_9_linux/usr/lib/firefox is not a directory.


Also, from manually checking my folders, there is no firefox folder nor file in my lib folder.

You shouldn't have to change the directory during the installation, and the directory Firefox is in should be:

/usr/lib/firefox/

not

/tmp/install_flash_player_9_linux/usr/lib/firefox

And it's not in the 

/lib/

folder, but the 

/usr/lib/

folder. We hope.

Good Luck! :)

---

### Post by Thunar on 2008-01-04
Oh, so it was actually in "usr/lib/mozilla" ?

haha, well I'm glad it all worked out ok.

:)

---

### Post by loverman210 on 2008-06-03
I am having the same problem too and I am stacking exactly here:

<<Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/mozilla

WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla):  >>

what should I do and more specifically what should I type to set the correct installation path? - nothing seems to wrk so far....

---

### Post by Thunar on 2008-06-03
> **loverman210 said:**
> I am having the same problem too and I am stacking exactly here:

<<Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/mozilla

WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla):  >>

what should I do and more specifically what should I type to set the correct installation path? - nothing seems to wrk so far....

Perhaps you can give us a little more info? What version of Ubuntu are you using? What browser are you installing flash into? can you provide a copy of what's in your terminal box? (just copy it all and paste it in your reply) what have you tried that was already covered in this thread? The more info the better! :D

---

