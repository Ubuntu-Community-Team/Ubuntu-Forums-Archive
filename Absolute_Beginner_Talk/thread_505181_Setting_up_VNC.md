---
title: "Setting up VNC"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by Tixer on 2007-07-20
I run a small server in my basement, and it's been running Ubuntu for the past 6 months. I've had an error, which I haven't bothered to fix, where I could only set the resolution to 800x640 if it was headless, but I could set it up to 1280x1024 if I had a monitor hooked up. I should have left it alone, but I was an idiot, and tried to fix it last night.

Naturally, it exploded.

I used remote-desktop to do VNC before, and it no longer works. I can't change the options for it, since I only have SSH and from what I've seen, you need visual access to change those. I've tried other programs, but either;

A) I get a blank screen in VNC
B) I get error message after error message

I just want to be able to view the desktop of the logged in user. The only problem now, is that I have no idea, if I'm even logged on. It was set to auto log in, and everything was fine, but now, I don't know if it's still logging in , or running GDM. Additionally, I've probably installed 30 different VNC servers, so I'd be scared to look at the amount of sessions running.

Where do I start for fixing this? I've tried like >9000 tutorials, but to no avail. Additionally, bonus points if you can fix the resolution issue. Note: I only have SSH access, and physical access. However, I am not willing to lug a monitor downstairs.

EDIT:

Using the command "users", I discovered that my account, which was set to log in on boot, is no longer logged on. This would explain partially why VNC isn't working, since I'd have to be logged in for it to work. How do I:

Log myself in
Make sure that x.org / gdm is working, and that, in the event I had a monitor plugged in, that I'd be seeing what is normal
Get VNC working (the above).

---

### Post by Tixer on 2007-07-20
bump.

---

### Post by Tixer on 2007-07-20
Anyone?

---

### Post by Rocket2DMn on 2007-07-20
Yes.
the vnc config file is typically stored in $HOME/.vnc/  and I believe is called XSTARTUP.  Here you can choose to enable a GUI interface over a terminal window, and you can declare the window size.  Perhaps this file got messed up somehow.
There are also universal settings in /etc/vnc.conf
Maybe post these files and we can have a look.

---

