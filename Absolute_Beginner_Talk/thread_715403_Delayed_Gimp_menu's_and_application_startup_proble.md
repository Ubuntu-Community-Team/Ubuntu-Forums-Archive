---
title: "Delayed Gimp menu's and application startup problem"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by r0mmie on 2008-03-04
Hello everyone,

I have a problem with the gnome desktop (I think). A lot of menu's started showing a delay when clicked upon. 

This is a delay of about 1,5 seconds (this seems to be exactly the same for all appearances of the problem).

Example: When I click on 'Applications' nothing happens for 1.50 seconds, then the dropdown menu appears..

Most programs show this delay when clicking on dropdown menu's.

Example: When clicking on file in firefox, 1.50 seconds delay before the menu appears.

Also all programs that seem affected by this have the same delay when they start! Right click menu's are delayed by 1.50 seconds too.

KDE apps like amarok seem to be unaffected. Shell commands also execute instantly. So it seems to be a problem with anything that has standard gimp window? Also my computer is not slow, it has a pretty new q6600 processor with 2gb of RAM.

This problem only appeared today. I really don't know what caused it or where to start looking for a solution. Some of the things I changed today:
-messing around with bluez to get my bluetooth headset to work
-installed mythtv
-installed dualview trought the nvidia-settings GUI

I have been running Ubuntu 7.10 for three days now, so I'm pretty green. Any pointers in the right direction would be greatly appreciated. Also if you need any additional information please ask!

Cheers,

Bartol

---

### Post by chewearn on 2008-03-05
See this thread:
[http://ubuntuforums.org/showthread.php?t=536045](http://ubuntuforums.org/showthread.php?t=536045)

Try to read the thread to understand the issue and how to solve.  If you still have problem after that, post back.

---

### Post by r0mmie on 2008-03-06
Thanks for the link, I found the solution on the other thread.


This script worked for me:

 #!/bin/bash
sleep 5
DISPLAY=:0.0 compiz --only-current-screen &
DISPLAY=:0.1 compiz --only-current-screen &

Although that script works for fixing the display problems and the slow menu's, I couldn't get the script to run properly at start-up. Is there any specific directory I should put it in? As the preferences > sessions gui doesn't seem to work for this file.

It's called ~/.dualstartup.sh and I put that text in the 'command' input field in the sessions settings, but I still have to run the script manually after each reboot for the fix to take effect. (I checked the spelling)

Is there any way of finding out if that command really runs at startup and fails or just doesn't run at all?

Thanks so far, and if this thread gets closed because of the subject change, I'll understand.

cheers

---

### Post by chewearn on 2008-03-06
Try to put in the full path:
/home/<user>/.dualstartup.sh
Replace <user> with your username.

You can add a temporary zenity prompt into it to verify it's running, like this:
```
#!/bin/bash
zenity --question --text "Ready?"
sleep 5
DISPLAY=:0.0 compiz --only-current-screen &
DISPLAY=:0.1 compiz --only-current-screen &
```But you will need to install zenity first:
```
sudo aptitude install zenity
```

---

### Post by r0mmie on 2008-03-06
Thanks,

Changing to the full path did the trick!

---

