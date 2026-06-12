---
title: "terminal stopped working with sudo..."
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by deathremains on 2007-08-13
well i started to install a webcam driver specifically the eyetoy for ps2 after a couple trys i finally got it to work via XawTV and my soundcard first started to go like the sound would stop for 5-10 minutes and then start back up. well i though it was something wrong with the eyetoy webcam so i restarted my computer and un plugged it well sudo stopped working as well as the system > admin area nothing is showing there and i cant reburn the iso seeing as theirs also glitches in the built in iso burning software any help?

---

### Post by guguma on 2007-08-19
do this 

```
groups <username>
```

if you do not see 'admin' then I suppose that something kicked you out of the admin group and that is why sudo does not work. so you should edit 

```
/etc/group
```

file.

But as you cannot do sudo so you cannot do it from your user account. If you have root account enabled do it as root.

Or if you have an alternate install cd. Boot with it choose rescue and choose the option to execute a shell in /dev/<root partition> . First it will do things as if it is installing a new system but do not worry.

then 

```
startx
```

and use (first backup the file)

```
gedit /etc/group
```

and make sure you have your login name by these entries. No whitespace chars, and user names separated by a comma.

WARNING (I do not know the exact details on this file, but this is the data from my default file so it has a possibility of working)

```

adm:x:4:
dialout:x:20:
cdrom:x:24:
floppy:x:25:
audio:x:29:
dip:x:30:
video:x:44:
plugdev:x:46:
scanner:x:104:
netdev:x:112:
lpadmin:x:113:
admin:x:117:

```

Also check the parameters of these enries (1000 and 27)(Again I do not know the meaning of exact parameters but as default they are like this) DO NOT ADD YOUR LOGIN NAME BY THESE

```


<username>:x:1000:
sudo:x:27:

```

Hope that helps. You have not been replied for 5 days now that is why I am posting a "possible" solution.

---

