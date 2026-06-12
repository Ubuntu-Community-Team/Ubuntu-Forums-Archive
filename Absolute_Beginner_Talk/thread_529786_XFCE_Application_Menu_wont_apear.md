---
title: "XFCE Application Menu wont apear"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by jdg.gehrig on 2007-08-19
I am Running Xubuntu and today I just booted up my laptop and the application menu (top & bottom) aren't there. my desktop is still there though.

i found this post but i don't think mine was caused by my laptop dying. They said they fixed it but i have no idea how.

the other post is at : [http://ubuntuforums.org/showthread.php?t=442107](http://ubuntuforums.org/showthread.php?t=442107)

Can someone please help 

Thanks in advance


new info:
if i type xfce4-panel in terminal the panel loads it says something about asla-mixer not finding the device and as long as terminal is open the panel will stay visible

---

### Post by HermanAB on 2007-08-19
This is a known bug.  Maybe you can help figure out why this happens.

Anyhoo, what you wish to know is how to fix it:
a. delete ~/.config/xfce4
b. log out and log in again

Like this:
$ rm -Rf ~/.config/xfce4
Now press ctrl-alt-backspace and log in again.
This will reset the desktop back to the default.

Note that I'm not sure whether the above is xfce or xfce4.  First do 'ls ~/.config' and have a looksee.

How to keep your desktop changes next time this happens:
$ tar -zcvf config.tgz .config

When it screws up again, untar that:
$ tar -zxvf config.tgz

Cheers,

Herman

---

### Post by jdg.gehrig on 2007-08-19
i feel really stupid asking this because i know i found the .config directory :confused:

But... Can you tell me where it is or tell me how to get to it if it isn't consistant

nvm found it

---

