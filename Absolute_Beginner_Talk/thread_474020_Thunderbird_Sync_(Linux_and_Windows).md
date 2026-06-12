---
title: "Thunderbird Sync (Linux and Windows)"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by cong06 on 2007-06-14
I'm trying to sync my Linux and Windows Emails with Thunderbird. After finding out about the ["-profile"](http://kb.mozillazine.org/Running_from_a_USB_drive_%28Thunderbird%29#-profile_.22path.22_command_line_argument)  command in windows I set it up so I have a *.bat file:
```

cd "C:\Program Files\Mozilla Thunderbird\" 
thunderbird.exe -profile "f:\Profiles\tbProfile"

```
and a *.sh file:
```

mozilla-thunderbird -P /media/stuff/Profiles/tbProfiles

```
(since my /media/stuff folder is shared so both computers can access the external at the same time)

The Windows bat file works fine, but whenever I run the *.sh file, it comes up with a menu giving me options for Profiles that are stored on the local harddrive, not the external (/media/stuff)
This folder: tbProfiles, is the same folder copied from: ~/.mozilla-thunderbird/<random>.default 

I've tried other things to, like:
```

mozilla-thunderbird -P /media/stuff/Profiles/profile.ini
```

where profile.ini is the profile.ini file that I copied from the ~/.mozilla-thunderbird/ directory, and moidified to point to tbProfiles...

Has anyone done this before? (I [posted this in the mozillaZine forum](http://forums.mozillazine.org/viewtopic.php?t=555350), but apparently not enough people there use Linux?)

---

### Post by vikram on 2007-06-14
have you tried editing the profile.ini to point it to the same dir as the windows folder ? alternatively you can create a regular profile in linux and then replace that dir with a link to the windows folder ?

this is assuming you have a dual boot system of course.


for example you created anew profile in linux ~/.mozilla-thunderbird/<random>.default
delete this and create a sym link

```

cd ~/.mozilla-thunderbird
rm -rf <random>.default
ln -s /media/stuff/Profiles/tbProfiles <random>.default

```

the next time you start TB it will try to load ~/.mozilla-thunderbird/<random>.default but will acutally load your windoze profile.

hope this works. 

cheers !

---

### Post by cong06 on 2007-06-14
> **vikram said:**
> have you tried editing the profile.ini to point it to the same dir as the windows folder ? alternatively you can create a regular profile in linux and then replace that dir with a link to the windows folder ?

this is assuming you have a dual boot system of course.

Sorry. I should have specified. I have an external plugged into a laptop (Ubuntu Feisty) and a Windows Desktop accessing the external through Samba. So it's two different computers, entirely.

I'll post my *.ini file anyway though, just so you guys can see it:
```

[Profile0]
Name=isaac
IsRelative=1
Path=tbProfile

```
This was, of course, when I used:
```

mozilla-thunderbird -P /media/stuff/Profiles/profile.ini

```
as my *.sh file.

---

### Post by vikram on 2007-06-14
why dont you create a 'regular' TB profile in linux as you normally do and share that via samba ? you can then use your windoze bat file to point to the mapped location ? that way you dont need a shell script in linux.

another option is modify the ini file in your home director to point to 
```

[Profile0]
Name=isaac
IsRelative=1
Path=/media/stuff/Profiles/tbProfiles/<random>.default

```
again no shell script is required.

also have you tried the "-profile" option in linux . is it windoze only ?

---

### Post by Inxsible on 2007-06-14
I am not sure if you are already following the procedure listed in this thread. If not, try this route

[ThunderBird Sync]("http://ubuntuforums.org/showthread.php?t=203524")

---

### Post by cong06 on 2007-06-15
I think i fixed it.

No, I had actually not found that post. I think that's what I ended up using the most:
1) bring up profile manager
2)delete all profiles
3)direct a new profile to my directory

That's much neater then *.bat, or *.sh files. thanks :)

---

