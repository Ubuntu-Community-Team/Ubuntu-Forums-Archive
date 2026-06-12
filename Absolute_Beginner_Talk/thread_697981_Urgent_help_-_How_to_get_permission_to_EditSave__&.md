---
title: "Urgent help - How to get permission to Edit/Save  &quot;xorg.conf&quot; file?"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by PiggiePaul on 2008-02-15
Right, I've just done something stupid (but not my fault !!!) that's my story anyway.......

In trying to get the extra buttons on my mouse to work, I followed some instructions and edited my xorg.conf file to allow for extra buttons.

And guess what. Upon rebooting NONE of my buttons work, so I can't click anything to alter anything (oh dam and blast)

So I've booted the system off the live CD (mouse working) and edited my "xorg.conf" back the way it should be.

So all I need to do it save it, reboot and all will be as it was.

Apart from one tiny issue.

I can't save the file "xorg.conf" as I don't have permission as I'm not logged on as me (I'm just running from the live CD Boot.

Dam and blast these permissions :(

So, I still have the file on screen now in gedit. How can I make it save?

Otherwise I'm stuck.

---

### Post by Rocket2DMn on 2008-02-15
You need to mount your hard drive first, then make sure you edit THAT xorg.conf file rather than the one being used on the LiveCD
Better yet, let's just skip the LiveCD altogether.
Boot into normal mode (where you have no mouse functionality? - this is OK right now) and do CTRL+ALT+F1 at the login screen and log into the tty (terminal).  You can then edit xorg from the command line (make a backup first!)
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backuip
sudo nano /etc/X11/xorg.conf
```
Then restart gdm
```
sudo /etc/init.d/gdm restart
```

---

### Post by TheBoat on 2008-02-15
You don't need to use the LiveCD.  Once Ubuntu has loaded, hit CTRL+ALT+F1.  This will take you to a virtual console and you can fix the xorg.conf (or replace it with a backup if you have one). FYI to get back to the Ubuntu Desktop GUI hit CTRL+ALT+F7.
EDIT: Beat me to it.

---

### Post by PiggiePaul on 2008-02-15
> **Rocket2DMn said:**
> You need to mount your hard drive first, then make sure you edit THAT xorg.conf file rather than the one being used on the LiveCD
Better yet, let's just skip the LiveCD altogether.
Boot into normal mode (where you have no mouse functionality? - this is OK right now) and do CTRL+ALT+F1 at the login screen and log into the tty (terminal).  You can then edit xorg from the command line (make a backup first!)
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backuip
sudo nano /etc/X11/xorg.conf
```
Then restart gdm
```
sudo /etc/init.d/gdm restart
```

Phew..........

Many MANY thanks for that.

Followed your explanation to the letter, and all back working fine.

Sheesh, now that was a close one.
Good job I also made a note of what I'd changed beforehand.

I guessed it could be done from the terminal at bootup, but I had no idea how to do it, which is why I went the Live CD Route as it was all I could think of to get at the file in question.

At least I know I can do that again if the same happens :)

Again, many MANY thanks.

---

