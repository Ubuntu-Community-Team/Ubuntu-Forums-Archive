---
title: "x window system won't start"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-05-28
when I boot up, everything seems to go ok, but then when the GDM would load and show normally, instead, it's a black screen with the loading circle cursor.  When I boot using the recovery mode (like now) and run it as root, everything works ok (of course) but when I do a su to my user then type startx it gets an error along the lines of "created authority file at /home/ryan/.serverauth.xxxx" (the x's are numbers)
"user is unauthorized to start xserver, aborting"
so I checked the permissions on the "authority" files it's creating and they are set to "me" "none" (no read/write)
and changing them doesn't help because every time it makes a new one with a different number after the dot!

I haven't even changed anything as far as I'm concerned, what happened?

---

### Post by greybirds on 2007-05-28
These two links might be of use.

[http://www.shallowsky.com/blog/linux/autologin.html]("http://www.shallowsky.com/blog/linux/autologin.html")

[http://www.shallowsky.com/blog/linux/serverauth.html]("http://www.shallowsky.com/blog/linux/serverauth.html")

---

### Post by ryanVickers on 2007-05-28
I fixed one of the problems, but it still doesn't work.  At least it's not making the authority files anymore, but I'm still not "authorized" to run X!

---

### Post by greybirds on 2007-05-29
Might be a stupid question, but has xhost helped?

---

### Post by ryanVickers on 2007-05-29
I just assumed that was a command and ran it, and here's the output:
> access control enabled, only authorized clients can connect
interesting...

---

### Post by greybirds on 2007-05-29
Can you get to a text mode terminal (control - alt - F1) and log in with your normal user name and get a command prompt? (Press control - alt - F7 to get back to the desktop.)

Also, what does the .xsession-errors and .Xauthority files in your normal user's home directory say?

---

### Post by ryanVickers on 2007-05-29
I can't get a command propt in this mode.  I can run X as root booting from recovery mode, but not normally (from my user).

.Xauthority is not readable as text, but I've noticed interesting things in the .xsession-errors file:
some segments...
> ** (gnome-session:5432): WARNING **: Failed to establish a connection with GDM: No such file or directory

** (gnome-session:5432): WARNING **: Couldn't connect to PowerManager Process /usr/bin/gnome-power-manager exited with status 0

** (gnome-session:5432): WARNING **: Couldn't connect to PowerManager Process /usr/bin/gnome-power-manager exited with status 0

** (gnome-session:5432): WARNING **: Failed to establish a connection with GDM: No such file or directory
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!
alarm-notify.c:368 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:304 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:243 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1875 (alarm_queue_init)
alarm-queue.c:218 (queue_midnight_refresh) - Refresh at Mon May 28 18:00:00 2007
 
alarm-notify.c:274 (alarm_notify_finalize) - Finalize 
 alarm-queue.c:1946 (alarm_queue_done)
No Hal support
No musicbrainz support (musicbrainz2 missing)
No iPod support
No Audio cd support (musicbrainz2 missing)

I think that bit (of the several Mb file) is interesting...

---

### Post by ryanVickers on 2007-05-30
Ok, never mind, I fixed it.  But tanks for the suggestions, they might help others more so than whatever my problem was (still don't know :p).

---

