---
title: "kubuntu login keeps going back to login screen"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by fnordportland on 2006-12-01
ery time i type my password/username in and hit enter it starts to go to my gui and then just  brings me back to my login screen,im running write now on a live ubuntu

---

### Post by nixternal on 2006-12-02
hrmm. It would be nice to see your /var/log/Xorg.0.log file, but since you can't login it won't be so easy. Unless you have SSH access to a server. If you have SSH access to a server, copy over that log file by typing this at the command line:

```
scp /var/log/Xorg.0.log username@server.with.ssh.access:directory/to/upload/to
```

I have seen this in the past as well. The main concern in your Xorg.0.log are lines that begin with [EE]. Don't worry so much about the Wacom ones, but I am willing to bet at the bottom, the very last line I believe, there will be an error concerning fonts. Another thing you can try is press Ctrl+Alt+F1 to get out to a terminal. Once you are there, you can try to reconfigure xserver. Do this by typing:

```
sudo dpkg-reconfigure xserver-xorg
```

---

