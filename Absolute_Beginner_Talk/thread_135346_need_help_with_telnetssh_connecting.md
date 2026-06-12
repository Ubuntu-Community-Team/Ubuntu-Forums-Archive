---
title: "need help with telnet/ssh connecting"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by GMachine_24 on 2006-02-23
Hi, and thanks for taking the time to read my post.

I am writing this from a PC running Ubuntu Breezy. I also have a computer running Fedora FC4, which functions as a music and file server (a backup machine).  I also have several Windows PCs networked together with the Linux machines.

What I'd like to do is be able to turn the FC4 server into a 'headless' machine (removing the monitor, keyboard and mouse) when I am done configuring and testing it. I have heard people talking about "telnetting into" another machine (in this case my FC4) in order to do maintenance or what have you - and I think you can set up an SSH connection, as well. Top security is not my primary concern as I am the only person who has access to these computers - I live alone - and my router/firewalls seem capable of preventing any intruder(s) - at least so far.

Anyway, I am looking for advice or a 'how to' to set up this Ubuntu computer so I can connect to the FC4 (which runs Samba and Slimserver), have administrative privileges, etc. I have read some on this but I get sort of lost with the telnet stuff and the SSH stuff is just impossible for me to understand - at least so far.

I hope I have explained this well enough. Thanks in advance for you time and help.

GMachine

---

### Post by Iowan on 2006-02-23
I don't remember if I had to install the SSH-client on my workstation  or if it came installed.  I remember that I had to install the SSH-server on my Ubuntu server before I could connect to it... Once I had the pieces in place, it was painfully simple.  Until I got DNS configured, I had to use IP address.  Because my client user was different from the server user, I had to: **ssh -l username 192.168.1.XXX**.  Seems like it also worked to **ssh [email]username@192.168.1.XXX[/email]**.  After that, it was just as if I were logged in at the console.

Forgot to mention... I presume there's a painless way to install SSH (server at least) on FC4, but having never used it...

Also... I found an article on passwordless SSH [http://www.cvrti.utah.edu/~dustman/no-more-pw-ssh/no-more-pw-ssh.html]("http://www.cvrti.utah.edu/~dustman/no-more-pw-ssh/no-more-pw-ssh.html")

---

### Post by GMachine_24 on 2006-02-23
Hi: Thanks for your post. I tried to log in using the information you gave but was rejected. Here is the log:

username@192.168.0.102's password:
Permission denied, please try again.

I know the username and password are correct.

GM

---

### Post by GMachine_24 on 2006-02-23
[QUOTE=GMachine_24]Hi: Thanks for your post. I tried to log in using the information you gave but was rejected. Here is the log:

username@192.168.0.102's password:
Permission denied, please try again.

I know the username and password are correct.

GM[/QUOTE]

OK, never mind. I figured out what I was doing wrong. I am logged in at a command prompt. Thanks for your help!!

---

