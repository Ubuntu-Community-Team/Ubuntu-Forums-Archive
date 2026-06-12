---
title: "Remote Access from XP to Ubuntu"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Proximo1 on 2007-09-19
How do I remote into my Ubuntu System from a different system running Windows XP Pro SP2?

I would like to remotely access my Linux box with the same keyboard, mouse and LCD I am using for my XP box.

Thanks.

---

### Post by kavon89 on 2007-09-20
For just a command line, google for **putty**. Enter your login info for the ubuntu user account when you open it and connect to the local IP of the ubuntu computer. I think you need to install or enable or install SSH on the ubuntu computer though.

For a view of what is on the ubuntu computer, use **vncviewer**

You can search the three of those on google and also the title of your post in the forum and find some more complete answers.

---

### Post by Proximo1 on 2007-09-20
Thank you for the response.  I will try using VNC Viewer.  I hope there is little lag between the connection.  My Linux box is right behind me.  I just want to use one keyboard, mouse and LCD to access both my systems.

Thanks again.

---

### Post by bodhi.zazen on 2007-09-20
See these links :

[uwiki]VNC[/uwiki]
[uwiki]VNCOverSSH[/uwiki]

You can also get a splitter. With a splitter you would connect one mouse/keyboard/monitor to both boxes and switch between them.

---

### Post by funrider on 2007-09-20
try using cygwin which is free, load it to your windoze

then, export the port from ur ubuntu box to windoze:
export DISPLAY=yourwindozeip:0.0

back to your windoze box, u should be able to run X application by putty

---

### Post by stalker145 on 2007-09-20
KVM Switch?

That's what I do if I have two computers side-by-side.

---

### Post by Proximo1 on 2007-09-21
> **stalker145 said:**
> KVM Switch?

That's what I do if I have two computers side-by-side.

A good point.  I do have a KVM, but they only come in VGA.  I have a DVI cord going from my Workstation to my LCD screen.  If I use KVM, I must downgrade my connection from DVI to VGA.

Do you know of any KVM's for DVI?

---

