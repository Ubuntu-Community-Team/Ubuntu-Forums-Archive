---
title: "/Home being ignored, Cannot Log in"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by Corneilius on 2007-09-15
I have been using Ubuntu for a few months now, and I have to say I am quite impressed.  I have so far been able to solve any problem or get anything done that I need to by reading and following directions from users of this forum.  You are all so very helpful.

Today, I encountered the first problem I have not been able to trouble shoot by myself.

I was following this guide on how to install some PSX emulation on my computer to play some of my old games.  [http://ubuntuforums.org/showthread.php?t=95835](http://ubuntuforums.org/showthread.php?t=95835)

After doing this, I was unable to open any programs.  Each time I tried it told me that I was denied access to my /home/username/ directory.

I restarted and tried to log in.  At this point I was given an error message.  Error Message was something like   "Your $HOME/dmrc file has incorrect permissions and is being ignored ...........File should be owned by user and have 644 permissions"

At this point I did some searching on my other ocmputer to find a thread that suggested safe starting in the terminal and typing "chmod 644 /home/username/"  or something to that effect.

Now when I try to log in I get an error message saying "your session only lasted less than 10 seconds......"  Details 

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/og/wtmp -u /var/run/utmp -x"/var/lib/gdm/ : 0.Xservers" -h "" -l ".0" "username"
/etc/gdm/Xsession: Begining session setup

(gnome-session: 5429): Libgnomevfs-WARNING **:  Unable to creat ~/.gnome2directory: Permision denied
Could not create per-user gnome configuration directory /home/uername/.gnome2/ : Permission denied


I am running Ubunutu  Feisty Fawn.  It is on a Compaq Laptop Presario R3000.  It has an ATI card.

Does any more information help?  I would truly appreciate it if anyone could help a newbie out!

---

### Post by Corneilius on 2007-09-15
I should also add that I am unable to run the Failsafe Gnome.  I am only able to get into the Failsafe Terminal.

---

### Post by schorsch on 2007-09-15
When you are in the failsafe teminal please type:
```
sudo chmod 755 /home/*username*
sudo chmod 644 /home/*username*/.dmrc
sudo chown *username* /home/*username*/.dmrc
```
Substitute *username* with your username.
As far as you do not have changed the permissions on your homedir recursively in the past there is no need to change it recursively again via the command
```
chmod -R ...
``` as this can cause a lot of trouble.

---

### Post by Corneilius on 2007-09-15
Thank you so very much.  You made that seem incredibly easy!!!!  It is working great now!

---

### Post by schorsch on 2007-09-15
Great to hear that! Could you please mark your thread as solved as this may help others, too?

---

### Post by Grumpywolfe on 2007-09-17
Hi all

Just wanted to thank you all for the fix it helped me out.

---

### Post by jmeyer on 2007-09-18
[SIZE="3"]Hey,

I am trying to logon to a Windows Domain and this doesn't seem to work for my situation.  I have tried chown and chmod but logging into our network I have a /home/*domain*/*username*.   I can log in but none of my network documents loads in my Ubuntu profile.  Could I get some help on this or point me in the right direction. 

Thanks[/SIZE]

---

### Post by splintercellguy on 2007-09-18
I suggest you create a new post, since your problem is entirely separate from the OP's issue, and to gain attention.

---

