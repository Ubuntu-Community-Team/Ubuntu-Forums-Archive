---
title: "Whoa! Somethings wrong here after recursive chown and chmod!"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-07-09
okay, i just did the following commands: ```
sudo chown -R erik:erik /home/erik
``` and  ```
sudo chmod -R 644 /home/erik
```and then my desktop background disappeared, i can't seem to open anything (programs and folders), this is the error message i get when trying to open something: ```
Could not launch application. Details:Failed to change to directory '/home/erik' (Permission Denied)
``` what can I do?  EDIT: the error message when trying to open folders on my desktop is: ```
Couldn't display &quot;/home/erik/Desktop/music&quot;. The attempt to login failed.
```

---

### Post by aysiu on 2006-07-09
Believe it or not, even though you're supposed to own everything in your home directory, not all of the files in your home directory are supposed to have 644 permissions.

These are the files and folders in my home directory and their permissions...

600 ```
.bash_history
.dmrc
.esd_auth
.gtk-bookmarks
.ICEauthority
.kderc
.lesshst
.mcoprc
.recently-used
.viminfo
.Xauthority
.xcompmgrrc
``` 640 ```
.gksu.lock
``` 644 ```
.bash_logout
.bash_profile
.bashrc
.cowbell
.DCOPserver_ubuntu__0
.fonts.cache-1
.fonts.conf
.gtk_qt_engine_rc
.gtkrc-1.2-gnome2
.gtkrc-2.0
.installed.txt
.sudo_as_admin_successful
.tagtoolrc
.xscreensaver
.xsession-errors

``` 700 ```
.AbiSuite
.aptitude
.cache
.gaim
.gconf
.gconfd
.gnome_private
.gnome2
.gnome2_private
.gnucash
.gnupg
.googleearth
.grsync
.kde
.kde-test
.libgda
.loki
.macromedia
.metacity
.openoffice.org2
.thumbnails
.Trash
.update-notifier

``` 710 ```
.easytag
.inkscape
``` 751 ```
.adobe
.baghira
.cddb
.config
.dvdcss
.evolution
.firefox
.fullcircle
.gimp-2.2
.gnome
.gqview
.gstreamer-0.10
.icons
.local
.mcop
.mplayer
.nautilus
.opera
.qt
.scribus
.speedcrunch
.themes
.vmware
.wapi
.wine
.xine
Desktop
```

---

### Post by user1397 on 2006-07-09
> **aysiu said:**
> Believe it or not, even though you're supposed to own everything in your home directory, not all of the files in your home directory are supposed to have 644 permissions.then what should i do?

---

### Post by user1397 on 2006-07-09
(btw, I have edited my first post) also, I cannot seem to open a terminal, so I am really screwed!

---

### Post by woedend on 2006-07-09
try changing it to 755 instead of 644
a lot of the files are 644 but some are 755, well at least see where that gets you?

---

### Post by aysiu on 2006-07-09
> **erik1397 said:**
> (btw, I have edited my first post) also, I cannot seem to open a terminal, so I am really screwed!
You're not really screwed. This is what recovery mode is for. Recovery mode boots you into a root terminal.

By the way, I edited my post to include the permissions on the files in my home directory. That may help you.

---

### Post by user1397 on 2006-07-09
okay, i pressed CTRL+ALT+F1 and I got to a console.  I was able to log in.  Then I tried ```
sudo chmod 600 
.bash_history
```but I got this error: ```
chmod: cannot access '.bash_history':No such file or directory
```

---

### Post by aysiu on 2006-07-09
Well, when you do ```
ls -al
``` do you see *.bash_history* in there?

---

### Post by user1397 on 2006-07-09
> **aysiu said:**
> Well, when you do ```
ls -al
``` do you see *.bash_history* in there?the thing is, i cant cd to /home/erik, i get the permission denied error.  so therefore, i cannot ls-al in /home/erik.  sny other suggestions?

---

### Post by aysiu on 2006-07-09
Are you in recovery mode?

Also, do you have a live CD handy?

---

### Post by user1397 on 2006-07-09
> **aysiu said:**
> Are you in recovery mode?

Also, do you have a live CD handy?yes i think i am, since to get to this CLI I had to press CTRL+ALT+F1.  and yes i do have a live cd handy.  thank you so much for keeping up with me aysiu.

---

### Post by aysiu on 2006-07-09
No, Coontrol-Alt-F1 is not recovery mode. It's just another virtual console.

You have to reboot your computer and select **recovery mode** from the Grub menu in order to boot into recovery mode.

It may be easier for you to do this from a live CD, though. Boot your live CD, mount your Ubuntu partition, and we'll work from there.

Do you know how to mount partitions?

---

### Post by user1397 on 2006-07-09
> **aysiu said:**
> No, Coontrol-Alt-F1 is not recovery mode. It's just another virtual console.

You have to reboot your computer and select **recovery mode** from the Grub menu in order to boot into recovery mode.

It may be easier for you to do this from a live CD, though. Boot your live CD, mount your Ubuntu partition, and we'll work from there.

Do you know how to mount partitions?okay im booting into the live cd.  do I need to go to recovery mode on live cd? (or is that even possible?) 

and i have kinda forgotten how to mount partitions, so I'll show you my fdisk report and then maybe you can tell me how to mount my hdd.

---

### Post by user1397 on 2006-07-09
okay i remember, my setup is pretty simple.  it goes like this:
/dev/hda1 (/)
/dev/hda2 (/home)
/dev/hda3 (swap)

---

### Post by aysiu on 2006-07-09
The live CD and recovery mode are two separate things.

Boot into the regular live CD session. Then: ```
sudo mkdir /recovery
sudo mount -t ext3 /dev/hda2 /recovery
gksudo nautilus
``` Then navigate to /recovery and change permissions on the appropriate files. Good luck.

---

### Post by user1397 on 2006-07-09
okay, i tried what you said aysiu. (there where some folders that were not in your list, possibly b/c you didnt have those programs, so I made them 700 or 744)

So I rebooted, got to the login screen, was able to login correctly, but just after that part, I get this error message:
```
Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.
(tickbox) View details (~/.xsession-errors file)
```i ticked the box, and below it revealed this:
```

/etc/gdm/PreSession/Defaut: Registering your session with wtmp and utmp.
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h " " -l ":0" "erik"
/etc/gdm/Xsession: Beginning session setup...
/etc/X11/Xsession.d/40guidance-displayconfig_restore: line 11: /usr/bin/displayconfig_restore: No such file or directory

(gnome-session:6037): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Permisson denied
Could not create per-user gnome configuration directory '/home/erik/.gnome2/'': Permissoion denied
``` 
EDIT: I forgot to mention, when I was in /recovery/erik on the live cd, I saw the following folders: .gnome, .gnome_private, .gnome2_private, but I didn't see .gnome2 (it looks like from the error message that it might have something to do with .gnome2)

---

### Post by aysiu on 2006-07-09
Are you sure you *chmod*ed your ~/.ICEauthority to 600?

---

### Post by user1397 on 2006-07-09
> **aysiu said:**
> Are you sure you *chmod*ed your ~/.ICEauthority to 600?
no, I chmoded it 644, just like in my first post.  I chmoded /home/erik recursively with 644, so .ICEauthority must have gotten 644 permissions.  btw, you should look at my edit on my last post.

---

### Post by user1397 on 2006-07-09
okay, im continuing this tomorrow aysiu, cause i gotta get some sleep (US eastern time here, 4:00!)  sothank you so much for staying awakewith me, and I hope I'll resolve this issue tomorrow morning.

---

### Post by aysiu on 2006-07-09
To be perfectly honest, it may be easier to just create a new user and then copy over some key configuration files from your old user.

---

### Post by gruepig on 2006-07-09
> **erik1397 said:**
>  ```
sudo chmod -R 644 /home/erik
```

Eek!

Okay, so what you've just done here is make your home directory and everything under it readable and writeable by you and readable by all on your system.

(There are a few things which won't work if they are world-readable, e.g., ssh keys, but overall most things will continue to work or will give indicative error messages.)

But nothing is executable by yourself or anyone else!   To run an application, it must be executable.  Additionally -- and this is the relevant part -- *linux/unix directories must have the executable bit set*.  This is what enables you to open files in the directory, have it be your current working directory, etc.

The fix, then, is to make all of your directories -- but not files -- executable again.  Fortunately, there's an easy way to do this with chmod.  From the chmod(1) manpage:  "execute only if the file is a  directory  or  already  has execute  permission  for some user (X)".  

The following should fix most/all of your problems:

```
chmod -R ugo+X /home/erik
```.

---

### Post by user1397 on 2006-07-09
> **gruepig said:**
> Eek!

Okay, so what you've just done here is make your home directory and everything under it readable and writeable by you and readable by all on your system.

(There are a few things which won't work if they are world-readable, e.g., ssh keys, but overall most things will continue to work or will give indicative error messages.)

But nothing is executable by yourself or anyone else!   To run an application, it must be executable.  Additionally -- and this is the relevant part -- *linux/unix directories must have the executable bit set*.  This is what enables you to open files in the directory, have it be your current working directory, etc.

The fix, then, is to make all of your directories -- but not files -- executable again.  Fortunately, there's an easy way to do this with chmod.  From the chmod(1) manpage:  "execute only if the file is a  directory  or  already  has execute  permission  for some user (X)".  

The following should fix most/all of your problems:

```
chmod -R ugo+X /home/erik
```.thanks! i was able to run that command using the failsafe terminal.  i then was able to go into my regular session and everything works fine!

BTW, what did that command exactly do?  And what permissions should my /home/erik and /home/erik/Desktop be (for security reasons)?

---

### Post by MrHorus on 2006-07-09
> **gruepig said:**
> Eek!
Additionally -- and this is the relevant part -- *linux/unix directories must have the executable bit set*.  This is what enables you to open files in the directory, have it be your current working directory, etc.

Not entirely sure you are right about that one.

Asa far as I am aware you can happily read from a directory that you do not have execute permissions from since you only require read permissions...

---

### Post by user1397 on 2006-07-09
> **MrHorus said:**
> Not entirely sure you are right about that one.

Asa far as I am aware you can happily read from a directory that you do not have execute permissions from since you only require read permissions...well whatever he said worked like a charm, so I would say that I agree with him.  (we could be wrong however)

---

