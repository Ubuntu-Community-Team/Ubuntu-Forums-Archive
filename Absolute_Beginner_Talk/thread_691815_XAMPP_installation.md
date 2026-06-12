---
title: "XAMPP installation"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by drarncruz on 2008-02-09
I am very new to ubuntu and linux. I am trying to set up a testing environment for php scripts and many of the forums recommend setting up XAMPP.  So I went to apachefriends and "downloaded" xampp-linux-1.6.5a tar.gz to the desktop.  The instructions say to open the terminal and paste this command "sudo tar xvfz xampp-linux-1.6.5a.tar.gz -C /opt".
When I do this, I get this error:
tar: xampp-linux-1.6.5a.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

I'm pretty much lost at this point.  Any advice would be greatly appreciated.

Thanks

---

### Post by kvizz on 2008-02-09
I think you should install every part of xampp/lamp server from ubuntu repos. This guide may help you: [http://www.supriyadisw.net/2006/12/lamp-installation-on-ubuntu](http://www.supriyadisw.net/2006/12/lamp-installation-on-ubuntu) . just skip the part about ubuntu installation and start from Apache.

---

### Post by badmedic on 2008-02-09
When you open the terminal it starts you off in your home directory, so it can't see the file because it isn't there... it is on your desktop.

Try moving the XAMPP file from your desktop to your home directory and then run the command again.

---

### Post by drarncruz on 2008-02-09
Thanks guys, I will try your suggestions.

---

### Post by drarncruz on 2008-02-09
Thanks BadMedic - that fixed it!
Now I have LAMP already installed as well and according to the install instructions for XAMPP on this forum, it should not affect this install.
I have LAMP working, somewhat, but now I would like to turn it off and try XAMPP.  Is there a terminal command to do this.

---

### Post by badmedic on 2008-02-09
Not sure about stopping LAMP, but the terminal command to start XAMPP is:
```

/opt/lampp/lampp start
```

---

