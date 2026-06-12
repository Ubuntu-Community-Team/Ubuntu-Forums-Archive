---
title: "Connecting to ubuntu that's not in a login/active session"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by DarkKoopa on 2006-09-23
Hi,

That title might be worded wrong, so feel free to correct the 2 week linux n00b :D 

I have a headless ubuntu LAMP with GUI box that acts as a family web server.

If I have logged onto the ubuntu box and have a active session (and locked screen ;) ), I can then log into the session via Windows using VNC Viewer (or similar).  Great.

The issue is that when by PC restarts (as it did last night due to power failure), I can't login, because the box is waiting at the login screen. Yeah, sad I know.  I have tried to search of this and there are many threads that have different options that confuse the hell out of me.  I have enabled remote login by System - Admin - Login Screen and unchecked the box about indirect hosts (or something, can't remember of the top of my head) that enables the XDMCP.

What Windows based program can I use to connect to the box to login?  I'm more than happy to then close that down and then start the VNC client.

Please help this newbie [-o<

---

### Post by crokett on 2006-09-23
Are you looking for gui or cli login?  You can use ssh to log in and start the vnc server.

---

### Post by DarkKoopa on 2006-09-23
> **crokett said:**
> Are you looking for gui or cli login?  You can use ssh to log in and start the vnc server.

How do I do this?  I tried Putty and WinSCP but got a Connection refused message.

I'm guessing that I need to open port 22 on ubuntu which means that I haven't installed a "SSH server"????? :confused: 

I dunno, I'm confused.  For now, I'm going to manually put a monitor and keyboard on it to login, can someone tell me what I need to do to get this working?   #-o 

Cheers

---

### Post by arsenic23 on 2006-09-24
All you have to do to get ssh working is install type
```
sudo apt-get ssh
```
Bam, it works.

If you just want to have your machine logged in all the time so you can use VNC, then you'll want to set your server up to autologin.  Just go to the Login Window Preferences, in the System>>Administration menu.  There should be a security tab there that will let you set up autologin so your VNC will always be available.

---

### Post by DarkKoopa on 2006-09-24
> **arsenic23 said:**
> All you have to do to get ssh working is install type
```
sudo apt-get ssh
```
Bam, it works.

If you just want to have your machine logged in all the time so you can use VNC, then you'll want to set your server up to autologin.  Just go to the Login Window Preferences, in the System>>Administration menu.  There should be a security tab there that will let you set up autologin so your VNC will always be available.

The apt-get command actually didn't work.  I had to use the package manager to install it.

So now I can log into the machine on a cli with a SSH client.

How do I start a GUI session that I can then use a windows VNC client with?

I tried 

> sudo /etc/init.d/gdm start

and nothing happened.  I couldn't log in with the VNC windows client.  I tried the sudo command in the SSH client again and it said that it was already running, so I've misread how to start  a GUI session. #-o

---

### Post by maaronB on 2006-09-24
I am not even sure what the question is so forgive me if this is irrelevent, but you can easily set GNOME to automatically log in a user with out starting at the login screen.
go to System->Administration->Login Window->Security.  Then check automatically log in box.

---

### Post by DarkKoopa on 2006-09-24
> **maaronB said:**
> I am not even sure what the question is so forgive me if this is irrelevent, but you can easily set GNOME to automatically log in a user with out starting at the login screen.
go to System->Administration->Login Window->Security.  Then check automatically log in box.

This is what I have ended up doing for now, but I'm one of those people that would like to know what I did wrong and how I can correct it, just for my limited linux knowledge. ;)

---

### Post by steve.horsley on 2006-09-24
Trying to start GDM over an SSH session won't give you a GUI. Unless you have an X-server installed on your windows client you will not be able to get GUI apps running over SSH. But it is worth keeping SSH installed as a backup or for when you don't need GUI control. Beware, the internet is full of SSH password guessing bots. They just spend all day guessing usernames and passwords. So use good passwords.

---

### Post by DarkKoopa on 2006-09-24
I found this thread

[http://ubuntuforums.org/showthread.php?t=11808](http://ubuntuforums.org/showthread.php?t=11808)

which was great for running VNC over SSH.

It still doesn't solve the original login screen issue though...

---

