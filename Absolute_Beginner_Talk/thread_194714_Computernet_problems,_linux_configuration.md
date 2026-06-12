---
title: "Computer/net problems, linux configuration"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by Handle123 on 2006-06-11
Hi. I've got a couple questions that aren't really related but I thought I'd post them in one place to save space.

1. Getting internet access on Ubuntu 6.06. I have an ADSL connection, and whenever I want to log onto the net, I need to connect to my router (192.168.1.1) and select connect. I can do this fine from my Windows machine. However, if I log into Ubuntu, go to swiftfox and then type 192.168.1.1, it doesn't connect to the router. It says not found. 

But, if I use my laptop to activate the internet connection, then start Ubuntu, the internet works fine (I'm typing this post on Ubuntu)

2. This is not a linux problem, but a problem with my computer. Sometimes, when starting up, the computer will just hang, before the OS finishes loading. It happens in Windows XP and Ubuntu. And it always happens at the same time (in Ubuntu, it hangs when the its doing "Loading Hardware Drivers".) But it only happens 1 in 4 times or so.  Can anyone explain to me what is happening at that stage so I can try and figure out which piece of hardware is causing it?

3. Just a small configuration issue. At the bottom of the screen is the list of windows currently open. They vary in size. I'd like to make it so that the size of the "buttons" are the same. Currently, if theres 1 window open the bar takes up the whole taskbar, and when a second opens up it halfs in size, etc. I dunno if i am wording this right.

Thanks for reading this post.

---

### Post by Zelut on 2006-06-11
You can always read the system logs & see if it is reporting an error with a piece of hardware at boot time.  You can find the logs by going to "System > Admin > System Log" or reading the log from the command line "<your-editor> /var/log/syslog"

That might give you some ideas about any troublesome hardware.  It could be a start..

---

### Post by Handle123 on 2006-06-12
I looked at the log but I can't really see any errors or such. Does the log start logging as soon as the computer starts booting Ubuntu?

---

### Post by Handle123 on 2006-06-12
1 more question. I have moved the menu bar from the top to the bottom. When I want to click the close (x) button on the top right of a window, usually I just flick my mouse to the top right of the screen and click. However, that doesn't work since the Ubuntu thinks I'm trying to resize the window. Instead, I have to move my mouse a couple pixels down and to the left to close the window. Its a small issue, but its been irritating me for a while.

---

### Post by Nikusan on 2006-06-12
[QUOTE=Handle123]
3. Just a small configuration issue. At the bottom of the screen is the list of windows currently open. They vary in size. I'd like to make it so that the size of the "buttons" are the same. Currently, if theres 1 window open the bar takes up the whole taskbar, and when a second opens up it halfs in size, etc. I dunno if i am wording this right.
[/QUOTE]

Right click on the bar to the left of where the windows are listed. Go to preferences, then the size tab. Try setting both min and max size to the same number.

---

### Post by Nikusan on 2006-06-12
[QUOTE=Handle123]1 more question. I have moved the menu bar from the top to the bottom. When I want to click the close (x) button on the top right of a window, usually I just flick my mouse to the top right of the screen and click. However, that doesn't work since the Ubuntu thinks I'm trying to resize the window. Instead, I have to move my mouse a couple pixels down and to the left to close the window. Its a small issue, but its been irritating me for a while.[/QUOTE]

You could try experimenting with different themes to find one that puts the close button in the very corner. I'm not sure if you'll have any luck though.

System > Preferences > Theme

---

### Post by Handle123 on 2006-06-12
Thanks for the response.

Unfortunately that number seems to limit the total size of all open window tabs, rather than individual ones :(

And none of the themes seem to move the close right to the end.

---

### Post by Handle123 on 2006-06-14
No ideas on the otehr questions? :(

---

