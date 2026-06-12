---
title: "Problem setting up 915resolution"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Cam on 2007-03-25
Hi, I'm having a problem setting up 915resolution to display 1280x800 on my laptop. Basically I can run it and "patch" it properly, but when it comes to adding the line to that file [I don't know much about linux yet] to get it to run at start up, I am a little confused. The official documentation had instructions for SUSE 9.2, so I went looking for a guide to setting it up in kubuntu. The one I found said to put the line in a file called /etc/init.d/bootmisc.sh and to place it above the line ‘:exit 0&#8242;. Problem is, that line doesn't exist in this file, and I'm paranoid about breaking something if I do this without help.

Can someone direct me in correctly setting up 915resolution on Kubuntu 6.10?

---

### Post by ramzai on 2007-03-25
Actually, for me it was just
sudo apt-get install 915resolution
restart X server (Ctrl+Alt+Backspace)

and everything ok, no need to edit anything manually...

---

