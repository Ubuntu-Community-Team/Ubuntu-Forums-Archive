---
title: "Startup Log"
date: 2005-07-17
forum: Absolute Beginner Talk
---

### Post by Sephiriz on 2005-07-17
When Ubuntu boots up, all those messages that scroll boy regarding the succesful (or failure) process of loading something are often difficult to read because it goes by so quickly.  At times I see a flash of red indicating that something failed, but I'm not sure what it is, so I'm wondering if there is some log that contains all the boot messages?

---

### Post by dave9191 on 2005-07-17
You can hit scroll lock to stop the messages scrolling :)

As for the log, Im not sure if they are all logged. Try looking through /var/log/ for something. 

Dave

---

### Post by Nequeo on 2005-07-17
[QUOTE=Sephiriz]When Ubuntu boots up, all those messages that scroll boy regarding the succesful (or failure) process of loading something are often difficult to read because it goes by so quickly.  At times I see a flash of red indicating that something failed, but I'm not sure what it is, so I'm wondering if there is some log that contains all the boot messages?[/QUOTE]
 I dont know where they are logged either... But you can try 
```

$ dmesg | more

```
immediately after you boot. Or:
```

dmesg > bootlog.txt

```
if you want to save the boot messages into a text file.

As an added bonus, this will also display boot items that appear after GDM (the login screen) starts. 

One thing to be aware off... You'll probably only see your boot log if you run that command immediately after booting. It only keeps the most recent kernal messages, and after a while the boot messages will become over-written by things like USB devices being plugged and unplugged, wireless networks coming and going out of range, and other misc. things like that.

---

### Post by Sephiriz on 2005-07-18
Thanks to both of you for taking the time to help.  Both your approaches, though not the most practical at times (or so I would imagine), work nonetheless.  These will work very well, I'm still curious if there is a log for this stuff though.  It would seem logical to do so, but I guess some things just don't exist or are so unused as to pass into the realm of nonexistence.

---

### Post by dave9191 on 2005-07-18
well i just found a bootlogd which supposidly logs all boot messages to /var/log/boot, but I dont have that file. So either its saving it somewhere else, or not working. 

Dave

---

### Post by Nequeo on 2005-07-18
[QUOTE=dave9191]well i just found a bootlogd which supposidly logs all boot messages to /var/log/boot, but I dont have that file. So either its saving it somewhere else, or not working. 

Dave[/QUOTE]

Heya,

I did not know about that program, but after you mentioned it I did a little poking around and discovered this:

Open a terminal type -

```

$ sudo gedit /etc/default/bootlogd

```

A text editor will open and you will see the following. 

```

# Run bootlogd at startup ?
BOOTLOGD_ENABLE=No

```

Simply change 'No' to 'Yes' - and hey presto! Next time you restart the /var/log/boot file will be created with a log of your boot messages. Only root has permission to read that file, so you'll have to open it with 'sudo gedit', or something similar. 

NOTE: On my machine, I get a message on my screen during boot saying that the boot log has failed. But it was lying, the boot log worked just fine. 

ALSO NOTE: The boot log will be full of lines like this '^[[A^[[74G[ ok ]'. All that 'garbage' is just the color code used to display the text as white or red during boot. It seems to get captured along with all the rest of the text. 

I've only just started using Linux myself... But the steps I had to go through to discover you could do this seem to suggest Sephiriz hit the nail on the head. The functionality was there, but turned off by default and hidden away to the point where it may as well not have been there at all.

---

### Post by dave9191 on 2005-07-18
good job :) 

Dave

---

### Post by Sephiriz on 2005-07-18
Yes, many thanks!  This is something that more people should know about I think.  Many thanks Nequeo, this log is the solution.  Very helpful too.

If you don't mind, I think I'll post up a quick HOWTO for this, I'll give you the credit for the find   :-P

Alright, the [HOWTO](http://ubuntuforums.org/showthread.php?p=260391) is now posted.

Once again, thanks Nequeo.

---

