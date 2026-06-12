---
title: "Problem in console trying to config resolution"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by The Napster on 2006-12-02
Hello People,
First of let me just say this is my first hour using Linux and im abolsuletly loving it so far, just ran into a little problem trying to config my setup to run my 1024 X 1280.

After searching the forums i found a possible resolution to the problem in this thread: [http://ubuntuforums.org/showthread.php?t=309351&highlight=1280+X+1024](http://ubuntuforums.org/showthread.php?t=309351&highlight=1280+X+1024) 

Ive opened up the console and ive tried running the following command:

gksudo gedit /etc/X11/xorg.conf|
Doing so just gives me this error: (gedit:7524): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

And then just opens up a blank file with no code for me to edit.

Running the following command does not give me an error but still opens a blank XORG.CONF file.
sudo gedit /etc/X11/xorg.conf|


Complete console entry:
esys@ubuntu:~$ home
bash: home: command not found
esys@ubuntu:~$ gksudo gedit /etc/X11/xorg.conf

(gedit:7524): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

esys@ubuntu:~$ sudo gedit /etc/x11/xorg.conf
esys@ubuntu:~$



Thank you.

---

### Post by munkyeetr on 2006-12-02
from what you've posted here, i believe it's just a simple typo.

try this:
```

gksudo gedit /etc/X11/xorg.conf

```

there's a capital X in X11
and there's no pipe symbol [ | ] after the command

this should work...

---

### Post by The Napster on 2006-12-02
Hello,
Quite correctly it seemed it was just a stupid typo! Thanks alot!

Anyway now ive seem to have been able to set my resoultion to the correct one for my LCD :) 

Problem is text still looks a little small on blary in firefox, any ideas / advice on how to rectify / escalate this problem.

Thanks.

---

### Post by Scunizi on 2006-12-02
First.. Have you installed a different video driver on your system or are you currently using what came with the install?  For most nvidia cards you could install nvidia-glx from synaptic then you'll have to open the same xorg file and change the name of the current driver (vesa or nv) to nvidia.  That might make a differance.

Also while you're in Firefox you can always CTRL+ to make everything bigger.  I also didn't see which version of Ubuntu you're using but the things listed above should work in the latest version or Dapper LTS.

---

