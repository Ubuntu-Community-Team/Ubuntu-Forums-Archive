---
title: "adding power button to panel"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by thelegionnaire on 2007-07-16
so can i add a shut down and stand by button to my panel? maybe just an icon that would send the code to do so, i could do that if i knew what the code was to do these tasks, any help appreciated, thanks

---

### Post by thelegionnaire on 2007-07-17
bump 


basically just looking for the console commands for shut down and suspend

---

### Post by Al3xK3aton on 2007-07-17
Doesn't your computer already have a shutdown command? Maybe you should get a media keyboard.

---

### Post by thelegionnaire on 2007-07-17
thats not my problem, i'd just like to know the terminal commands

---

### Post by Earthwormzim on 2007-07-17
If you are running Feisty, it's quite simple.  Right-click on the panel.  Select the option "Add To Panel".  In the  grouping labeled "Desktop & Windows" select the icon that says, "Quit...". 

Once you got this on your panel, when you press it, a list of options will appear, including such options as shutdown, restart, log-off, etc.

---

### Post by CautionaryX on 2007-07-17
To shutdown:

```
sudo shutdown 0
```

To restart:
```
sudo shutdown -r 0
```

The 0 represents the numver of minutes until the system shutdown begins. You can change that to whatever you want.

---

### Post by s[_]spect on 2007-07-17
Shutdown at least is as follows

Usage: shutdown [OPTION]... TIME [MESSAGE]
Bring the system down.

Options:
  -r                          reboot after shutdown
  -h                          halt or power off after shutdown
  -H                          halt after shutdown (implies -h)
  -P                          power off after shutdown (implies -h)
  -c                          cancel a running shutdown
  -k                          only send warnings, don't shutdown
  -q, --quiet                 reduce output to errors only
  -v, --verbose               increase output to include informational messages
      --help                  display this help and exit
      --version               output version information and exit

TIME may have different formats, the most common is simply the word 'now' which
will bring the system down immediately.  Other valid formats are +m, where m is
the number of minutes to wait until shutting down and hh:mm which specifies the
time on the 24hr clock.

---

### Post by thelegionnaire on 2007-07-17
thanks all

---

