---
title: "Boot problem"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by Corvair on 2006-07-14
I had sound problems so I deleted Alsa sound device and reinstalled as per the thread below.

[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=alsa+configuration](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=alsa+configuration)

It said to reboot, so I did and now I cannot open Ubuntu OS.
I come up with a kernel, I think it is called. I put in my user name and password and come up with the prompt:

claude@ubuntuclaude:~$

What do I have to do to open my Ubuntu page?

Please...

---

### Post by Sonofmoog on 2006-07-14
Run the command
```
startx
```
or, perhaps, 
```
sudo startx
```
and enter your password when prompted.  If you see the graphical login screen, you should be good to go.  If you do not, make note of any error messages that appear and post them here.

---

### Post by Paerez on 2006-07-14
to get the login, do:
```
# sudo /etc/init.d/gdm restart
```

---

### Post by Corvair on 2006-07-14
Thanks for looking at the problem.

Sonofmoog,

With your solution I get a blank grey window and nothing else.


Paerez,

with your solution I get a message: command not accepted


I work from a startup page, white on black.

first I get a request to log in and then I get the prompt as mentionned earlier.

I have to switch to windows to communicate.

---

### Post by Paerez on 2006-07-14
I know this is a lot to ask, since you are switching between computers, but could you give me the exact error message for my command?

---

### Post by Corvair on 2006-07-14
No problem,

It says command not found

---

### Post by Paerez on 2006-07-14
wow ok. Are you using Kubuntu, Xubuntu, or Ubuntu?
if you are using K or X, change "gdm" to "kdm" or "xdm" respectively.

---

### Post by Corvair on 2006-07-14
I am using Ubuntu 6.06

---

### Post by Paerez on 2006-07-14
ok try:
```
# sudo apt-get install gdm
# sudo /etc/init.d/gdm restart
```

---

### Post by Corvair on 2006-07-14
OK,
we have some progress.

I installed gdm and now I can go as far as the regular Ubuntu login  screen. If I log in, all I get is a dark brown screen and the mouse pointer whish I can move but tha's all.

If I go to the bottom left to options and request failsafe terminal for the failsafe xterm session and then login I get a terminal consol with the regular prompt so as to be able to initiate repairs.

Now what next?

---

### Post by Paerez on 2006-07-14
ok, I guess you must have accidentally uninstalled gnome with the alsa (baby out with the bathwater :D)
```
# sudo aptitude install ubuntu-desktop
```

---

### Post by Corvair on 2006-07-14
Hello Paerez,

Thank you very much for helping me getting back on the saddle.
Like you said I must have dumped the wrong thing.

My sound problem with xmms is still there no: no sound.

If you have time to look at the following thread maybe you can help me find that solution too. 

thanks again.

[http://www.ubuntuforums.org/showthread.php?t=214339](http://www.ubuntuforums.org/showthread.php?t=214339)

---

