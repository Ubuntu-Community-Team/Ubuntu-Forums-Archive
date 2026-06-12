---
title: "Applications fail to start"
date: 2008-12-04
forum: Apple Hardware Users
---

### Post by pwaldo on 2008-12-04
Hi all,

I have just installed Intrepid on my G3 iBook (768MB RAM).  The desktop appears after logging in.  When I try to run almost any application, I get nothing.  For example, I try to open a terminal or Firefox, I see some CPU activity, but no application appears.

On what may be a related note, I have strange behavior on the few applications I can open.  I can open the applet manager and the Updater tool.  The strange thing is that after being open for a while, they cease to function.  Not like an unresponsive application, but button presses are handled but they don't do anything.  For example, the Updater opens and I can check for updates.  After a repository update is finished, I have updates to install.  I click the Install button, but I get no activity.

Now that I think about it, the only apps that I can open are ones which are initiated from the Dock.  The reason I was able to get the updater to run was because I got the "You have updates" balloon.

I have tried looking at ~/.xsession-errors, but I have no way to get to it.  I can't open a GUI terminal, and the Virtual Terminals are not accessible because I had to use video=ofonly.

Any ideas would be greatly appreciated.  Thanks in advance!

---

### Post by mokkamanfred on 2009-01-10
Same error for me. I installed 8.10 on a G3 iBook@800MHz with some trouble during installation and its finalization. It hung at some point of clock setting.

You can try to start xterm by opening the file manger and change to folder /usr/bin. So did I and I got a small terminal window with no decoration.

I think that some scripts won't have been started during installation process. Is there a way to start them manually?

Thx for help!

---

### Post by rjcalifornia on 2009-01-11
How did you get 768 MB of RAM on your ibook?? I thought the limit for G3s was 576....

---

### Post by avtolle on 2009-01-11
> **mokkamanfred said:**
> Same error for me. I installed 8.10 on a G3 iBook@800MHz with some trouble during installation and its finalization. It hung at some point of clock setting.

You can try to start xterm by opening the file manger and change to folder /usr/bin. So did I and I got a small terminal window with no decoration.

I think that some scripts won't have been started during installation process. Is there a way to start them manually?

Thx for help!
Wonder if your battery is OK? Suggested by [https://help.ubuntu.com/community/UbuntuDateBug](https://help.ubuntu.com/community/UbuntuDateBug)

---

