---
title: "Permissions..."
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by Izman111 on 2007-09-30
Well, i'm a ubuntu nub and my dad installed this. long story short i screwed up with some permissions (because it said when I logged in that others shouldn't be able to access my files...) I did this, but for some ungodly reason I locked my self out of my account! GNOME wont start, and in the command line i can go anywhere but my home directory!

can anyone tell me a command that will make the permissions on my home directory normal again? I don't wana wake up my dad because it's late (typing this on my windows partition), btw, I know how to get in a command line >.<

---

### Post by taurus on 2007-09-30
Boot into recovery mode from GRUB menu.  Then at the prompt, try

```
chown -R **user**:**user** /home/**user**
```
_Assuming_ **user** is your log in name.  Replace it with your actual log in name, okay.

Then, reboot and see if you can log in now.

```
shutdown -r now
```

---

### Post by Izman111 on 2007-09-30
thankyou, that was fast :)

i'll definatly try that, I can't thank you enough.

---

### Post by Izman222 on 2007-09-30
It didn't work, I still get the "Your session lasted less than 10 seconds..." thing, here is my exact error

/ect/gdm/PreSession/Default: Registering your session with wtmp and utmp

/ect/gdm/PreSession/Default: running: /usr/X11R6/bin/Sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0. Xservers" -h " " -l ":0" "isaac"

/ect/gdm/Xsession: Beginning session setup...

(gnome-session: 5169): libgnomevfs - WARNING **: Unable to create ~/.gnome2 directory: Permission denied
Could not create per-user gnome configuration directory '/home/isaac/.gnome2/': Permission denied

EDIT: for some reason my other new account (Izman111) password wasn't correct. so I made a new 1

---

### Post by Izman222 on 2007-09-30
bump? read the post above

EDIT: Wow, i've sat at my computer screen for a hour now...taurus... were is your bright answer???

---

### Post by eph1973 on 2007-09-30
when you go to recovery mode, and type ```
ls -l /home
``` does it say something like this for your user directory:

```
drwx------ <some number> <your user name> <your user name> 4096 <date> <time> <your user name>
```

If it doesn't have at least that first drwx at the first part of the listing for your home directory, you might have to change the permissions to something like:

```
chmod 0755 /home/<your user name>
```

In addition to file ownership, if you changed the permissions such that you can't write to your home directory, you would also get that error.

---

### Post by Izman222 on 2007-09-30
THANK YOU SO MUCH! I'M IN UBUNTU!!! xD looks like that was the ticket, thanks!!!

---

### Post by mohit052 on 2007-09-30
Well,
do you know the root password of the comp?

what you have done most probably is that, you have changed the permission of your home directory to
one with no write permissions....

log in as other user  and change the permission of your home directory by becoming root.
Your home directory will be /home/your_user_name..

You in for some serious sloogin by your dad if this does not work..... for all i figure

best of luck

---

