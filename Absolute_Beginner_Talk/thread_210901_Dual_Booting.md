---
title: "Dual Booting"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by CounterBlow on 2006-07-07
Well I've decided to dual boot Windows, and Dapper Drake.  I'm currently running on Windows, because I can't seem to get Ubuntu to work.  I get to the screen, where it asks which OS I would like to use.  I click the top most Ubuntu one, and it starts to load (White text on a black backround, this is suppose to happen, as it did on a video tutorial I watched)  However, once the screen goes down, it eventually asks for my login, and password (Still on the white texted, and black backround screen)  I type these in, and then it goes to this:

ubuntu: ~$

Above that, it gives me administrative commands that I can enter.  I enetered the help one, but nothing happened.

If anyone knows what the problem is, or how to fix it, it would be greatly appreciated.  Thanks.

---

### Post by tonyr on 2006-07-07
Generally this means that something in your X server startup didn't
work.  Describe your hardware, in particular your graphics controller
and display.  The file /var/log/Xorg.0.log, which you can look at from
the console session that you have, usually has some info about why
the xserver didn't start.  Look for lines that start with EE.

If you are unfamiliar with the Linux commandline interface, say so,
and some helpful souls will guide you to extractring more useful
information.

---

### Post by CounterBlow on 2006-07-07
Yeah, I have no clue about Linux commands.  This is my first time using something with Linux.

And, how would I access this console session?  Would that be within the BIOS on startup?

---

### Post by CounterBlow on 2006-07-07
bump?

---

### Post by crystal on 2006-07-07
You are already at the command line. To view the file tonyr mentioned, you can enter:
nano /var/log/Xorg.0.log

---

### Post by CounterBlow on 2006-07-07
So after I log in at that screen I mentioned in my first post, just enter: nano /var/log/Xorg.0.log ?  I'll try that now...

---

### Post by tonyr on 2006-07-07
Yes, that's right.  As you have discovered, hopefully by now,
nano is (should be) a relatively easy to use visual editor.

What is your computer? Laptop? Desktop? Make and Model?

(Sorry, I had to pay attention to family for a little while.)

---

### Post by CounterBlow on 2006-07-07
No problem.  I use a Desktop PC.  It's a custom built model. (OEM)

I'm going to try the nano now, and see what happens.  If I can't follow this editor, I'll report back here. ;)

---

### Post by crystal on 2006-07-07
> I'm going to try the nano now, and see what happens. If I can't follow this editor, I'll report back here.
To exit, press CTRL + X. The caret (^) refers to the control key.

---

### Post by CounterBlow on 2006-07-07
When I entered it, it said, "nano /var/log/Xorg.0.log: No such file found"

And to make it clear, I entered my login information, and then I entered "nano /var/log/Xorg.0.log" at the "ubuntu: ~$" part.

---

### Post by Max Luebbe on 2006-07-07
Just in case it wasn't clear in earlier posts:
(You said you were unfamiliar with command line tools)

'nano' is a text editing program

to change directories use 'cd' followed by the path you want to get to, or 'cd ..' to go back a level


to see all the entries in a directory use 'ls'

Could you goto the log directory
```
cd /var/log
```

And let us know if there are any Xorg related files there?
```
ls X*
``` (the star here is a wildcard, it tells ls to match anything that starts with X)

Also, how did you install ubuntu?

---

### Post by crystal on 2006-07-07
Okay... this is rather out of my league to diagnose, but what do you get when you try:
locate Xorg
and
locate X11

---

### Post by CounterBlow on 2006-07-07
> **Max Luebbe said:**
> Just in case it wasn't clear in earlier posts:
(You said you were unfamiliar with command line tools)

'nano' is a text editing program

to change directories use 'cd' followed by the path you want to get to, or 'cd ..' to go back a level


to see all the entries in a directory use 'ls'

Could you goto the log directory
```
cd /var/log
```

And let us know if there are any Xorg related files there?
```
ls X*
``` (the star here is a wildcard, it tells ls to match anything that starts with X)

Also, how did you install ubuntu?
Alright, I'll try that now.

And, my computer was running on NTFS, so I had to reformat it.  Before I did so, I downloaded Dapper Drake, and burnt it onto a disk.  Then a friend helped me install it via AIM, with a tutorial.

Crystal, I'll try that too.

And just to be perfectly clear:  Should I be entering this at: **ubuntu: ~$** ?

---

### Post by tonyr on 2006-07-07
> **CounterBlow said:**
> When I entered it, it said, "nano /var/log/Xorg.0.log: No such file found"

This means either that the xserver never even attempted to start
or that it couldn't find the **nano** program, or that **nano**
couldn't open the file for some reason.

How did you install?  Did you use the LiveCD, the AlternateCD or the
ServerCD?  I'm asking because the ServerCD does an installation
without the graphical desktop (ie, it puts you in the white-on-black
console you're in now).

Knowing the specfics of the graphics controller and the display
would help some here.

---

### Post by CounterBlow on 2006-07-07
It said "No such file or directory", when I entered those...
> How did you install? Did you use the LiveCD, the AlternateCD or the
ServerCD? I'm asking because the ServerCD does an installation
without the graphical desktop (ie, it puts you in the white-on-black
console you're in now).
I'm pretty sure it was the Desktop CD, but I downloaded it from a faster mirror.  The friend sent me a link to it, but I reformatted, so I don't have the link anymore...

---

### Post by Max Luebbe on 2006-07-07
No such file or directory when you entered which commands?

---

### Post by CounterBlow on 2006-07-07
cd /var/log

And I should be entering these at, "**ubuntu: ~$**" ?

---

### Post by tonyr on 2006-07-07
Unfortunately, this is sounding worse and worse.

At the console prompt, do
```

mount
ls /

```

and reproduce the results here, if you can.

---

### Post by Max Luebbe on 2006-07-07
yes, thats where you want to enter them.

For future reference, the $ and what comes before it is called 'the prompt'

---

### Post by CounterBlow on 2006-07-07
Alright.

I typed mount, then ls / and I got the following:

in light blue:  cdrom  initrd.img  vmlinuz

in purple:  etc  initrd  media  lib  opt  root  srv  tmp  var  dev  home  lost+found  mnt  proc  sbin  sys  usr

---

### Post by tonyr on 2006-07-07
Did **mount** produce any result?

Do
```

ls -l /var

```
You should see a list that looks something like this:
```

drwxr-xr-x  2 root root  4096 2006-07-07 06:38 backups
drwxr-xr-x 11 root root  4096 2006-04-09 20:55 cache
drwxr-xr-x  3 root root  4096 2006-05-13 14:17 games
drwxr-xr-x 47 root root  4096 2006-07-01 20:22 lib
drwxrwsr-x  2 root staff 4096 2006-03-27 02:38 local
drwxrwxrwt  3 root root    60 2006-07-07 11:48 lock
drwxr-xr-x  8 root root  4096 2006-07-07 11:48 log
drwxrwsr-x  2 root mail  4096 2006-04-09 14:48 mail
drwxr-xr-x  2 root root  4096 2006-04-09 14:48 opt
drwxr-xr-x 10 root root   420 2006-07-07 11:49 run
drwxr-xr-x  6 root root  4096 2006-04-09 15:03 spool
drwxrwxrwt  3 root root  4096 2006-07-07 09:44 tmp

```

If none of these are there, that's bad.  If some are there, which ones?

---

### Post by CounterBlow on 2006-07-07
Yeah I got that.  However I could only read the end of it ("ackups"/"ache"/"ames", etc.)

When i type in mount, I get the following:

dev/hdd3 on/type ext3 (rw, errors=remount-ro)
procon/proc type proc
sys on/sys type tmpfs (rw)
varlock on/var/lock type tmpfs (rw)
procbususb on/proc/bus/usb type usbfs (rw)
dev on/dev/pts type devpts (rw, grid=5, mode 620)
devshm on/dev/shm type tmpfs (rw)
dev/hdd1 on/media/hdd1 type ntfs (rw, nls=ute8, umask=007, grid=4C)

---

### Post by CounterBlow on 2006-07-07
Alright.  So could someone link me to a **good** installation download?

Also, I thank everyone for the help.

---

### Post by tonyr on 2006-07-07
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

Choose your country, then get the one that says **PC (Intel x86) desktop CD**.
I assume you have an x86 based platform.

EDIT: Not all sites have a nice web page, some have a directory listing.  The
file name there is **ubuntu-6.06-desktop-i386.iso**.

---

### Post by CounterBlow on 2006-07-07
The estimated time on that is 6 hours. =\

Have any other, faster, ones?

[EDIT] I got one that's roughly a half an hour.  This should do. :)

---

### Post by tonyr on 2006-07-07
Probably too late now, but you should get the md5sums file and verify
your download.  The linux utility is **md5sum**.  There is an
equivalent one for Windows, but I don't remember what it is right now.

---

### Post by CounterBlow on 2006-07-07
> **tonyr said:**
> Probably too late now, but you should get the md5sums file and verify
your download.  The linux utility is **md5sum**.  There is an
equivalent one for Windows, but I don't remember what it is right now.
I downloaded one from the link you gave me.  I just clicked a different United States.

But now I go to boot the disk, and it goes to the Ubuntu screen.  I click "Start, or install Ubuntu from disk".  it loads (Green lettering in the top left corner of the screen) and then after a few minutes says: I/O error, "Reboot".  I reboot, but the same thing keeps happening.

---

### Post by tonyr on 2006-07-07
Sorry this is being so much trouble.  The problem you are seeing
usually means a bad download or a bad burn.  The bad download you 
can check in Windows by running ***md5summer*** which you
can get [here]("http://www.md5summer.org/download.html").
In linux you can use the utility ***md5sum***.
At the site where you downloaded the iso image, if you scroll down
some you will see a list of file links, one of which is MD5SUMS.TXT.
It contains checksums for each .iso file.  The result fo running
one of the md5sum programs should match the corresponding checksim
in the MD5SUMS file.  If they don't, the download file is bad.

When you burn the CD, it is recommended that you burn at 4x speed,
and not higher than 8x.

EDIT:  There is a tutorial/guide for this process at
[http://psychocats.net/ubuntu/iso.html]("http://psychocats.net/ubuntu/iso.html")

---

### Post by CounterBlow on 2006-07-07
Okay, I'll do that.

But just to make sure, when I start the disk, and have the BIOS run from the disk as a first boot priority, should I delete the already made partitions (From the previous disk)?  Or is there anything else I should change?  Or delete everything else and start from scratch?

[EDIT] For Dapper Drake, according to the tutorial, which line should I copy? [http://mirror.cs.umn.edu/ubuntu-releases/6.06/MD5SUMS](http://mirror.cs.umn.edu/ubuntu-releases/6.06/MD5SUMS)

[EDIT2] Nevermind, I performed the tutorial, and it said the disk I had just used was fine...

---

### Post by confused57 on 2006-07-07
If you have the ubuntu-desktop installed, which should have been with the Desktop Live CD...boot into Ubuntu, at the command prompt($), type:

```
sudo /etc/init.d/gdm start
```
or
Ctrl+Alt+F7

Don't know if this will help, your system should be booting to the graphical gdm login screen if the desktop installed properly.

If none of this works, and you have a fast internet connection, you could try (re)installing the ubuntu-desktop:
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

You've gotten some good advice from other posters, but thought I'd offer my 2 cents worth.  Good luck.

---

### Post by CounterBlow on 2006-07-07
> **confused57 said:**
> If you have the ubuntu-desktop installed, which should have been with the Desktop Live CD...boot into Ubuntu, at the command prompt($), type:

```
sudo /etc/init.d/gdm start
```
or
Ctrl+Alt+F7

Don't know if this will help, your system should be booting to the graphical gdm login screen if the desktop installed properly.

If none of this works, and you have a fast internet connection, you could try (re)installing the ubuntu-desktop:
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

You've gotten some good advice from other posters, but thought I'd offer my 2 cents worth.  Good luck.
Thank you, I will try that.

BTW, tony, would you happen to have AIM by any chance?

---

### Post by tonyr on 2006-07-07
AIM - That's AOL Internet Messenger, right?  No, I don't, but I can come
up with something.  Stay tuned...

---

### Post by CounterBlow on 2006-07-07
> **tonyr said:**
> AIM - That's AOL Internet Messenger, right?  No, I don't, but I can come
up with something.  Stay tuned...
It's AOL ***Instant*** Messenger. :-P

But yeah, that's what I meant.

---

### Post by CounterBlow on 2006-07-07
bump

---

### Post by Wr8EYilK8Y on 2006-07-07
I know what happened now. You installed the server. When typing "startx" you get a "command not found", don't you? I'll IM you the command to enter over Gaim, okay? Glad you came to join the Linux community, CB. Nice to see you here.

---

