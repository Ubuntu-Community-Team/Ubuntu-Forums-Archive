---
title: "Problem with &quot;Authentication Required&quot; window"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by Tamil on 2006-11-03
1. When login to my account "Authentication Required" window pops up. There is nothing suspicious in "Startup Programs".

2. When I try to connect to another system "Authentication Required" window comes 2 times. When I fill Username, Password and click Connect the first window goes away and second window never responds and I have to use Force Quit to close it.

---

### Post by Tamil on 2006-11-03
When I move bookmarks in Nautilus, "Authentication Required" window pops up. :confused:

---

### Post by Tamil on 2006-11-03
](*,)

---

### Post by Tamil on 2006-11-06
](*,)

---

### Post by Tamil on 2006-11-08
](*,) :(

---

### Post by steve.horsley on 2006-11-08
In the absence of another answer, here is a desperate suggestion.

**Suggestion 1:**

Log out
Ctrl-Alt-F2 to a console screen, log in and rename the following hidden directories (put an X in front or something):
.gconf, .gconfd, .gnome, .gnome2, .gnome2_private, .gconf
[B]mv .gconf .Xgconf
mv .gconfd .Xgconfd
...[/B]

Ctrl-Alt-F7 back to the GUI, log in and see if the problem has gone. If so, delete all the renamed directories and accept that your gnome settings have gone.

That's done it for me a few times, but I have also had to do the following once or twice when I couldn't figure out where the bad setting was held:

**Suggestion 2:**

Basically, give yourself a new home directory. If the problem goes away, it's something configured in your original home directory and you can just do some renaming and copy your data (but not config files).

First, make a new home directory:
**sudo mkdir /home/tamil2**
and give it to yourself (I assume your username is tamil):
**sudo chown tamil:tamil /home/tamil2**
then make this new directory your home directory by editing your entry in /etc/passwd:
**sudo gedit /etc/passwd**

Now log out and back in again. If the problem is still there, I give up and you might as well undo those changes. If the problem goes away, it must be something in your configuration files in your home folder. In that case, I suggest you do the following:

Edit /etc/passwd and restore the proper home directory name.

Boot into recovery mode and swap the names of the two home folders:
[B]mv /home/tamil /home/tamil/tamil-old
mv /home/tamil2 /home/tamil[/B]

Reboot and log in. Copy all your needed data from /home/tamil-old to /home/tamil. This includes some hidden files like .mozilla that contain application settings. Try not to copy whatever messes you up though.

---

### Post by andypaxo on 2006-12-08
Don't know if this is still a problem, but just in case you run across it again...

I had this problem for a while, every time I wanted to change settings in any program, I had to cancel 3 or 4 "Authentication Required" windows wanting me to enter the username and password for another computer.

This computer was bookmarked in Nautilus. I removed the bookmark and the problem went away!

---

