---
title: "cant run terminal :|!!!!"
date: 2005-08-17
forum: Absolute Beginner Talk
---

### Post by noob_Lance on 2005-08-17
hey, i cant run the terminal anymore... someone help. i get Permission denied whenever i try to open it... wth is going on...

~Lance


*EDIT* i cant RUN ANYTHING... even to see my harddrive !!!!!!!!!!!!!! HELP!!!!!!!!!!!!

---

### Post by heimo on 2005-08-17
Full disk?

Try to change to virtual console - you can change between first virtual console and X with ctrl+alt+F1 and ctrl+alt+F7. Logon to console, type

 ```
df -h
``` 
check free space

 ```
sudo apt-get clean
``` 
will remove some .deb install packages

---

### Post by noob_Lance on 2005-08-17
no i still have about 8 gigs of free space... i get permission denied, child process crap :|!!!!! help :(

---

### Post by heimo on 2005-08-17
[QUOTE=noob_Lance]no i still have about 8 gigs of free space... i get permission denied, child process crap :|!!!!! help :([/QUOTE]

Can you give exact error messages? Have you tried rebooting? (if not, don't try yet, it can make your system unbootable)

---

### Post by noob_Lance on 2005-08-17
Cannot launch entry

Details: Failed to execute child process "gnome-terminal" (Permission denied)

thats for the terminal... aswell as all the others, games i can run,.. anything else... im pooched

---

### Post by heimo on 2005-08-17
Can you change to virtual console and run any shell commands (df, ls, top)? With top you can check if some process is taking all CPU, but this seems to be some other kind of problem. 

Other thing you can try: hit alt+F2 and type: gnome-terminal (does it launch a terminal window? No?)

I would probably try to restart gdm with
 ```
sudo /etc/init.d/gdm restart
``` 
it's possible that this makes your system unusable. On a healthy system, this just restarts your graphical user interface.

---

### Post by noob_Lance on 2005-08-17
Cannot display location 'file://gnome-terminal'

Details: There is no default action associated with this location

---

### Post by heimo on 2005-08-17
If changing to virtual console works and you can execute shell commands, I would probably take the risk of rebooting (type sudo reboot). However, this probably doesn't solve your problem. You could try to add new user before rebooting (with adduser command).

---

### Post by noob_Lance on 2005-08-17
i tried installing Eclipse if thats any use... using this 

[https://wiki.ubuntu.com/EclipseIDE](https://wiki.ubuntu.com/EclipseIDE)

any clues there?

---

### Post by heimo on 2005-08-17
[QUOTE=noob_Lance]i tried installing Eclipse if thats any use... using this 

[https://wiki.ubuntu.com/EclipseIDE]("https://wiki.ubuntu.com/EclipseIDE")

any clues there?[/QUOTE]

And the problems began after you installed that? Which steps did you follow? Did you install it from zip or apt-get? Which steps did you take? Were there any errors or warnings?

EDIT: Are you using Hoary 5.04?

---

### Post by noob_Lance on 2005-08-17
well it wasnt a zip. tar.gz but i followed those steps. im not usin kubuntu if thats what you mean... :S

yes im on 5.04

---

### Post by heimo on 2005-08-17
And you had no problems during install? Have you logged out and in after this? I read through the instructions and can't see anything that would mess your computer. Did you try to run eclipse? Hit alt+F2 and type: *killall gnome-panel *That should reload your panels. If you haven't restarted, go ahead and try that one too (if this problem came right after the eclipse install). Hopefully this is nothing major, but it's a weird problem. Hopefully not a hardware failure.

---

### Post by nosyguy on 2007-05-02
I am facing the same problem and hence need some help. Right now I can't open any program at all, not even the terminal.

After installing tetex package, I couldn't figure out why I can't open the program tex. So I figure it has to do with the permission. I tried something like "sudo ... /usr/bin/tex" but it doesn't work. Finally I thought maybe I can try to give the user permission to execute programs in that folder. So I type something like "sudo uo-x /usr/bin" (something like this which I saw on the web, but maybe typed wrongly here).

The rest of the story is as described earlier. Could anyone help me with this situation, where I couldn't even open the terminal to remedy?

Thanks

---

### Post by Tomosaur on 2007-05-02
It sounds like both of you have somehow messed up your permissions. Reboot your machine (may require a hard reboot, ie, hold the power switch for around ten seconds, then switch your computer back on). When Grub shows, boot into the recovery mode, then once everything's booted, type:
```

ls -l /usr/bin > /home/<your own user name here>/usrbinprivs.txt

```

Then reboot back into normal mode, and paste the contents of that file up here.

---

### Post by nosyguy on 2007-05-03
Thanks. After posting, I searched for a long time but but couldn't find my posting!

Anyway, I boot into the recovery mode and type "chmod -R a+rwx /usr/bin" and then I was able to log-in again, and also run any programs. Then I figured that I should enter "chmod -R go-w /usr/bin" so that the permission of that directory would be set to its proper settings.

So all is fine now. Thanks =)

---

