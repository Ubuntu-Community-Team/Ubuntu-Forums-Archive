---
title: "File on desktop wont delete AT ALL."
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by ArrowApollo on 2006-12-11
It just looked as if my documents folder had been dragged to the desktop my accident but when i tried to trash it nothing happened. I looked at the permissions and they were fine. I emptied the folder and still no luck. Now when I go to its properties it gives me crazy stuff like permissions cannot be determined and unkown type, size, MIME type ,etc...

What can I do?

---

### Post by scrooge_74 on 2006-12-11
> **ArrowApollo said:**
> It just looked as if my documents folder had been dragged to the desktop my accident but when i tried to trash it nothing happened. I looked at the permissions and they were fine. I emptied the folder and still no luck. Now when I go to its properties it gives me crazy stuff like permissions cannot be determined and unkown type, size, MIME type ,etc...

What can I do?

open terminal type sudo nautilus /home/yourusername

whit that you will be in the file manager with root permissions and can get rid of the offender

---

### Post by bodhi.zazen on 2006-12-11
> **ArrowApollo said:**
> It just looked as if my documents folder had been dragged to the desktop my accident but when i tried to trash it nothing happened. I looked at the permissions and they were fine. I emptied the folder and still no luck. Now when I go to its properties it gives me crazy stuff like permissions cannot be determined and unkown type, size, MIME type ,etc...

What can I do?

To remove a directory:

cd ~/Desktop
rm -r name_of_directory

---

### Post by ArrowApollo on 2006-12-11
I tried both and the first one, its not there, and the second one says it doesn't exist!

---

### Post by bodhi.zazen on 2006-12-11
> **ArrowApollo said:**
> I tried both and the first one, its not there, and the second one says it doesn't exist!

Restart gnome

If the file is still on the desktop print the output of:

```
ls -la ~/Desktop
```

---

### Post by scrooge_74 on 2006-12-11
ran out of ideas on this one, maybe login out and login back in will clear it?

---

### Post by ArrowApollo on 2006-12-11
besides restarting the comp, whats the terminal code for restarting gnome? I'm very new.

---

### Post by bluevoodoo1 on 2006-12-11
[http://ubuntuforums.org/showthread.php?t=173014&highlight=desktop+delete+file](http://ubuntuforums.org/showthread.php?t=173014&highlight=desktop+delete+file)

Try ctrl+alt+backspace, or from terminal

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm restart

---

### Post by Iowan on 2006-12-11
I had that happen (under Breezy).  I also remember responding to another thread almost a year ago - but can't find it now.  If un-typeable characters have gotten embedded in the file name, it may be useful to use copy/paste with the **rm** command to purge the files.

---

### Post by bodhi.zazen on 2006-12-11
> **ArrowApollo said:**
> besides restarting the comp, whats the terminal code for restarting gnome? I'm very new.

Click the red icon on the upper panel and log out and then back in 

or Ctrl-alt-backapsace

or in a terminal:```
sudo /etc/init.d/gdm restart
```

---

### Post by ArrowApollo on 2006-12-11
Tried those command line tips, and nothing. Restarted and that "ls -la ~/Desktop" thing gave me this...

[http://img134.imageshack.us/img134/8739/screenshotut5.png](http://img134.imageshack.us/img134/8739/screenshotut5.png)

something very odd I just noticed. in my home folder i have a documents folder and it seems to be connected to the documents one on my desktop that i  cant get rid of. Whenever I delete the items in  the desktop one the items in the home folder one go away too.

---

### Post by scrooge_74 on 2006-12-11
> **ArrowApollo said:**
> Tried those command line tips, and nothing. Restarted and that "ls -la ~/Desktop" thing gave me this...

[http://img134.imageshack.us/img134/8739/screenshotut5.png](http://img134.imageshack.us/img134/8739/screenshotut5.png)

something very odd I just noticed. in my home folder i have a documents folder and it seems to be connected to the documents one on my desktop that i  cant get rid of. Whenever I delete the items in  the desktop one the items in the home folder one go away too.

If we had been using XP I would have been screamin VIRUS!!!! run for cover save what you can LOL

You got some bug there, did you try to restart the Xserver?

---

### Post by ArrowApollo on 2006-12-11
I restarted the computer.

---

### Post by dolphinsonar on 2006-12-11
Try ALT F2 gksudo Nautilus then navigate to the file and delete it as ROOT

---

