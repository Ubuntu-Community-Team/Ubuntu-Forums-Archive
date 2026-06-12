---
title: "No GUI"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Patrick793 on 2007-08-28
I'm making this topic for my friend. I've tried helping him on MSN, but no luck. He has installed Ubuntu 7.04 using Unetbootin. After the installation was complete, he started Ubuntu, but there was no GUI. I told him to log into the CLI, and he did. Then I told him to download the ubuntu desktop package using ```
sudo apt-get install ubuntu-desktop
```
He did that, and after the installation was complete, I told him to reboot his computer using ```
sudo reboot
``` which he did. He went back into Ubuntu, and there still was no GUI. Can anyone help? My knowlege of Ubuntu is limited, and I tried helping him with all I know. So, would you please help?

Thanks!

---

### Post by Outrunner on 2007-08-28
```
startx
```

This will start the X server

---

### Post by Patrick793 on 2007-08-28
He gets this error when he types startx.

```
X: cannot start /etc/X11/X (no such file or directory), aborting
xinit: Connection refused (errno 111) unable to connect to X server
xinit: No such process (errno 3): Server error
```

---

### Post by Patrick793 on 2007-08-28
Anyone?

---

### Post by bren on 2007-08-28
get him to type this command and post the content here....


> lshw -short

actually he will have to type a lot so he could send it to a file.....then if it is a dual boot machine he can send it to you

> lshw -short > hardwarelist.log

---

### Post by aquavitae on 2007-08-28
Try ```
sudo dpkg-reconfigure xserver-xorg
``` It should reconfigure the gui.  Then use ```
startx
``` to start it.

---

