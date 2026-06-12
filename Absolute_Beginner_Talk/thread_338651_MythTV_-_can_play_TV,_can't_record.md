---
title: "MythTV - can play TV, can't record"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by sfpiano on 2007-01-14
I can run mythtv and watch everything just fine, but when I go to record a show, nothing happens. Doesn't matter if I go through mythtv or mythweb. I go to the guide, select the program I want, go to 'record only this time', I hit save settings, and I get nothing. I go to upcoming recordings and it's blank. I know it's not my card because I can do cat /dev/video0 > test.mpg and view it with mplayer and it's fine.

However if I go into mythweb under 'Recording Schedules', that's where I find the recording I setup, but it doesn't run it as a recording.

---

### Post by jonny on 2007-01-14
Presumably you can view live TV through MythTV?  If so, I'd suggest a couple of possible areas for exploration:

1. Permissions.  Are you sure that the mythtv user can write to the directory where you said recordings should be saved when you ran mythtv-setup?  And you did run that program as the mythtv user, right?
2. Channel setup.  Are you totally confident that your channel / card / source setup is correct?  Perhaps MythTV knows the programme exists but doesn't think it has access to a tuner.
3. Device contention.  Mythbackend can fall over in a big heap if anything else accesses the tuner card while it's running.
4. Advanced setup error.  There are some pretty complex options hiding in mythbackend.  If you think that you might have accidentally changed something you don't understand, try backing up and deleting your database, deleting /home/mythtv and /home/*/.mythtv and then delete and reinstall all the Myth packages.

---

### Post by sfpiano on 2007-01-14
The directory is owned by www-data, but it's chmoded 777. I've been running mythtv as root, I wasn't aware it mattered who you ran it as. This time I started the backend as root and tried to start the frontend as mythtv, but it said:
mythfrontend: cannot connect to X server

Edit: in fact, I can only run mythfrontend as root, for anyone else it gives me the same problem.
Any time I try running xhost it also says "unable to open display **"
Which is :0.0

---

### Post by jonny on 2007-01-14
IIRC, running mythtv-setup as root isn't recommended.

Installing Myth creates a new user, mythtv.  You need to log in as that user (you might have to create a password first) and then run mythtv-setup as that user.  If you simply su in a terminal session, you will continue to own the X session and the mythtv user won't have permission to take it over.

Mythbackend should start on its own when you turn on your PC.  If you need to restart it, don't run it directly from the command line - use the standard method for restarting services,
```
sudo /etc/init.d/mythtv-backend restart
```
I believe that this script will start mythbackend as root, but will immediately drop privilges to match the mythtv user - that's certainly the way that most services work under Ubuntu.

---

### Post by sfpiano on 2007-01-14
I logged in as mythtv, and ran mythtv-setup, but it had all of the settings from when I ran it as root. I still have the same problem where it won't. I don't know maybe I'm doing something wrong: I go to the program guide, select the program I want to record, change it from 'Do not record this program' to 'Record only this showing', and scroll down to 'Save these changes' and hit enter. But when I go to the list of recordings nothing shows up.

---

### Post by wjston on 2007-01-15
> **sfpiano said:**
> I logged in as mythtv, and ran mythtv-setup, but it had all of the settings from when I ran it as root. I still have the same problem where it won't. I don't know maybe I'm doing something wrong: I go to the program guide, select the program I want to record, change it from 'Do not record this program' to 'Record only this showing', and scroll down to 'Save these changes' and hit enter. But when I go to the list of recordings nothing shows up.

Try logging in as Myth user, then exit back to Ubuntu desktop. Now start an Xterm and type in mythfrontend - hit enter. Now try watching live tv and then hit your record button. Press Alt/Tab on your keyboard to bring up your xterm display. This should reveal any problems MythTV is having while trying to record. Hopefully it will just be a permissions problem or directory does not exist problem. If it is a directory problem, make sure you change where recordings are to be stored in MythSetup to a directory MythTV has read/write permissions. 

Hope this helps.

---

### Post by SyvanX on 2007-01-15
Shouldn't mythbackend fail to start if the recordings directory is un-writeable?

check your mythbackend log to see if there are any errors on starting as the mythtv user.

```
tail /var/log/mythtv/mythbackend.log
```

---

### Post by scoultas on 2007-10-23
I had the same issue.  Mythbackend logs showed:

> No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.

I ran mythtv-setup, went to the 'General' page, and changed the Master Server IP Address, which was set to 127.0.0.1, to the actual IP address of the machine running mythbackend (for me, both backend and client are the same machine, but I set the real IP address rather than just the loopback localhost IP address).

I then restarted mythbackend, and 'Upcoming Recordings' displayed a full list of programs set to record again.

Hope this is useful to you in solving your problem!

---

