---
title: "Setting up krdc"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by ahounsome on 2008-03-31
Hi all,

I'm sure that the machine I'm trying to connect to needs setting up to accept a remote connection - I just don't know how to do this. I'm trying to krdc from my Kubuntu laptop to my new Kubuntu workstation via wireless. I can ping it ok. Thanks in advance, Andy.

---

### Post by Tteddo on 2008-03-31
On the remote machine you have to create an invitation in Remote Desktop Sharing. Then you can use the Terminal Server Client on your laptop and put the IP Address or your desktop with a :0 after it like so 192.168.0.101:0 and select protocol type VNC and it should hook up after you put the invitation's password in.
If you need it permanently available, there are better ways though.

---

### Post by ahounsome on 2008-03-31
Hi, yes I have seen the invitation procedure but I wanted to get something permanent going. Any ideas?

---

### Post by Tteddo on 2008-03-31
I use mine for remote access to my network so I did the following:
I have vnc installed, then you have to run it once from the user you are going to use for it (I used vishnu) so it sets up /home/vishnu/.vnc/xstartup, i.e. in a terminal window as that user just type
> vncserver.
 In that file I changed the line that opens the fwm window manager to:
gnome-session &
So it will use gnome. KDE is:
startkde &
Then I made a file in /etc called vnc.sh and made it executable, then put the following lines in it:
> #!/bin/sh
su -l vishnu -c 'vncserver :18 -depth 24 -geometry 1024x768' &
and then I put the following line in /etc/rc.d:
> /etc/vnc.sh &&

exit 0

So that if vnc.sh fails it doesn't hang the system. This opens VNC on port 5818 and 5918 on the host machine, and it will always be waiting.

There might be easier ways to do this now, but I first figured this out in 2004 on Fedora Core 4 and it's been working ever since on 3 different machines.

Let me know if you have any questions!

---

### Post by Tteddo on 2008-04-01
There is also a way to do it by adding a few lines to your /etc/X11/xorg.conf, but I could never get that to work, it just comes up as a bunch of lines.

---

