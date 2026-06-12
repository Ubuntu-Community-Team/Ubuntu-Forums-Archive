---
title: "X Server issues"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by kevindubrow on 2007-05-30
Hi,
     I was trying to enable my Wacom tablet by following the page on this link: [http://ubuntuforums.org/showthread.php?t=25151&highlight=wacom+tablet](http://ubuntuforums.org/showthread.php?t=25151&highlight=wacom+tablet)

After I restarted X by ctrl+alt+backspace, neither my keyboard or mouse would work. I restarted my computer and I was informed that X was not working and would not start up.

I know that I backed up the file that I was guided to edit from that link (I was also following a guide on the Ubuntu website which told me to back up first) so I believe that I can restore it and get Ubuntu running again, right? Could someone instruct me how to restore this file through the text interface?

If it is not possible to restore this file, is there a way to reinstall Ubuntu without losing any programs or files (something like a quick install of Windows XP)? Thanks for the help!

---

### Post by taurus on 2007-05-30
Well, if you did make a backup before you edited xorg.conf, you can just copy it back like

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
_Assuming_ the backup copy is called xorg.conf.backup.

Otherwise, you can reconfigure X again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by kevindubrow on 2007-05-30
In the event where it isn't named like that and I have to reconfigure. Will I need to know anything else other than the code to reconfigure? I am using a computer at an office away from the one at home with issues, I want to know how to repair the computer before I leave. Thanks.

---

### Post by taurus on 2007-05-30
If you are not sure about a question, just use the default.  Should be good enough.

---

