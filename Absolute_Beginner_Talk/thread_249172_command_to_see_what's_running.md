---
title: "command to see what's running"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by benner on 2006-09-02
what is the command to list what processes are running?

---

### Post by snapcase16 on 2006-09-02
You can either enter top into the terminal or open up your system monitor.

---

### Post by davmac on 2006-09-02
You can also open up a terminal and type "ps -e"

---

### Post by benner on 2006-09-02
i tried to install software (windows mobile phone suite) under wine and it froze in the middle of installation.  i wanted to see what the process was being called so I could kill it.  thanks, 'top' worked.  now i can't kill the process.  tips?

---

### Post by davmac on 2006-09-02
How are you trying to kill the task? Are you doing a killall <taskname>? Does sudo killall <taskname> work? Can you describe what is happening and what results you're getting in more detail?

Thanks,

Dave Mac

---

### Post by szf on 2006-09-02
Yeah, like what davemac said:

[FONT="Fixedsys"]
$ ps -e | grep beag
 5423 ?        00:00:02 beagled
 5474 ?        00:00:01 beagled-helper
$
$ ps -ef | grep beag
sean      5423     1  0 07:47 ?        00:00:03 beagled --debug /usr/lib/beagle/BeagleDaemon.exe --bg
sean      5474  5423  0 07:47 ?        00:00:01 beagled-helper --debug /usr/lib/beagle/IndexHelper.exe
sean      6014  5519  0 07:56 pts/0    00:00:00 grep beagle
[/FONT]

---

