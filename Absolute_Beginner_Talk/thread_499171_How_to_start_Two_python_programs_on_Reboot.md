---
title: "How to start Two python programs on Reboot"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by Namzy on 2007-07-12
Hi, I'm relatively new to linux (running Ubuntu 7.04). For a summer job I'm making a data transfer program using Python. It has two different python programs that must run simultaneously (one sends data via SFTP continuously and the other feeds data to it). This works fine when I start it using the terminal, I just use two different terminals and the two python programs run fine. 
My problem is that I need this to be an automated program, and so it must start itself automatically if the PC dies due to power failure. I've tried using crontab to schedule them to start on reboot with the lines:
@reboot /bin/su - root -c /file/path/program1.py 2>/dev/null
@reboot /bin/su - root -c /file/path/program2.py 2>/dev/null
This runs "program1.py" as needed, but it seems to ignore "program2.py" altogether. 
I've also tried to add them both to startup using system =>preferences => sessions => additional startup programs =>  python /file/path/program.py   (Note this method is undesirable because it requires login, reducing automation)
This also only ran the first program. 
Any suggestions as how I can get both running simultaneously??
Thanks!

---

### Post by Al3xK3aton on 2007-07-12
I'm thinking a dual core processor might help. Dual core processors run things simultaneously, while single core processors only give the appearance of running things simultaneously.

---

### Post by Namzy on 2007-07-12
I doubt it, as single-cores have run multiple processes for years now (as well as the two programs work fine when opened via terminal)

---

### Post by Viskovitz on 2007-07-12
Maybe you can create a little script "launcher.sh" that executes both programs, first #1 and then #2? I don't know how the @reboot line works, but maybe it only lets you execute only one command. If so, add @reboot /whatever/launcher.sh to the crontab.

---

### Post by Namzy on 2007-07-12
OK that sounds helpful, however I have no clue how to make a script. Suggestions?

---

### Post by Namzy on 2007-07-13
OK now we've had overnight to think about it :P  Anyone got any other advice? (or instructions on how to make scripts?) Thanks!

---

### Post by hyper_ch on 2007-07-13
you could ad them to the according runlevels...

---

### Post by zanglang on 2007-07-13
Can't remember if this works, but how about adding a '&' behind the cron jobs so they run in the background, simultaneously?

So, it would be:
> @reboot /bin/su - root -c /file/path/program1.py 2>/dev/null &
@reboot /bin/su - root -c /file/path/program2.py 2>/dev/null &

---

### Post by Namzy on 2007-07-13
Thanks for the suggestions guys, I've found the problem (my inexperiance with linux). I'm used to running windows where I can run my own programs, and thus I did not think to look if my programs  had permission to be executed - only one did. Now that I've given them both permission to be executed my origional cron commands do the job just fine.

---

