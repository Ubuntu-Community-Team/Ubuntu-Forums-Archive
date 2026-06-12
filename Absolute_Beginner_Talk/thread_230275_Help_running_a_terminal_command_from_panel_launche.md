---
title: "Help running a terminal command from panel launcher"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by subpar on 2006-08-05
Ok so I was bumpin around on google last night looking for an alarm, and I found one that I really liked. So I ran```
sleep 8h 30m && xmms /home/subpar/Doc\!/Music/wakeup.m3u
```inside of the terminal, and it worked fine.

The problem is, I tried to create an application launcher to run this from the panel so I wouldn't have to type that it every time I went to bed at night, and could instead just click on an icon, and have it set the command for me. When I press the icon, it'll open the terminal put in the command, and then close the terminal right afterword, which will also terminate the sleep program. 

Is there any way I can prevent the terminal from closing, or at least send the sleep process to the background? I have already tried adding "screen -d" to the beginning of the code in the application launcher.

Thanks for any help!

---

### Post by fourchannel on 2006-08-05
Hm. I get the same results here.

What I did instead was make a script to hold those commands, and then tell the applet to launch the script ```
nano -w /home/<username>/bin/alarm.sh
``` and you could put this in the script ```
#/bin/bash
sleep 8h 30m && xmms /home/subpar/Doc\!/Music/wakeup.m3u
``` ```
chmod 750 /home/<username>/bin/alarm.sh
``` and then use this command in the applet ```
gnome-terminal -e "/home/<username>/bin/alarm.sh"
```

---

### Post by subpar on 2006-08-05
Aha! That works just like I wanted it to. Thank you so much.

---

