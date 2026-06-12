---
title: "[MBP] Quick Questions! Please Help"
date: 2008-05-20
forum: Apple Hardware Users
---

### Post by boarder4021 on 2008-05-20
Hi, thank you for reading my desperate cry for help! I'm just beginning with Ubuntu and there's many things I enjoy, and many things I can't enjoy just yet. Here's what I need help with-

I cannot edit x11/xorg.conf It says I don't have permission. What can I do to fix that? Also, I **_need_** to be able to disable the touchpad while typing, I'm struggling to post this. 

Secondly, I have downloaded ndiswrapper but I'm having trouble installing it. I followed the madwifi instructions on the wiki but I would like to know how to uninstall that and use ndiswrapper instead. 

Thank you for taking the time to read and answer my questions. It goes much appreciated.

---

### Post by skip mcshwang on 2008-05-20
To edit xorg.conf:

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by dustynus on 2008-05-20
about the disable touchpad while typing
try

"syndaemon -t -d"

works great for me :)

---

### Post by boarder4021 on 2008-05-20
Is there a way to disable the trackpad while a mouse is plugged in (via USB)? 

Also, I still need help with the wireless card...

---

### Post by boarder4021 on 2008-05-20
I could really use some help with the trackpad mouse ordeal. I'll try to fix the wireless card as much as I can,but anyone with knowledge of how to turn off the trackpad while a usb mouse is plugged - please help me out!

---

### Post by boarder4021 on 2008-05-20
> **dustynus said:**
> about the disable touchpad while typing
try

"syndaemon -t -d"

works great for me :)

Now where do I type that? And when I'm in a word processor and typing, how do I use the trackpad? Can someone elaborate? 

Also, I'm still looking for help to turn the trackpad off when I have a mouse plugged in.

---

### Post by cyberdork33 on 2008-05-20
> **boarder4021 said:**
> Now where do I type that? And when I'm in a word processor and typing, how do I use the trackpad? Can someone elaborate? 

Also, I'm still looking for help to turn the trackpad off when I have a mouse plugged in.
type it in the terminal. it senses your typing an turns off the pad. after a delay it is enabled again. you can add that command to your session and it will start automatically on boot.

I answered your second question in the other thread that you asked in. You should avoid asking the same thing in more than one place.
[http://ubuntuforums.org/showthread.php?t=800615](http://ubuntuforums.org/showthread.php?t=800615)

---

### Post by boarder4021 on 2008-05-20
Thank you very much cd33. I also am the one that IM'd you earlier today, but resounded to the forums instead. I'm sorry if I bothered you at all.

Well let's see I just typed it and I'm still having my trackpad move about while I type. I didn't get anything to come after I typed it, just the next line in the terminal. It still moves around as I type, so I don't know if it fixed anything. 

Again I apologize for posting in more than one thread, and didn't see that you had responded until later today. 

**New problem that could use some tips - I am trying to install ndiswrapper and when I do make uninstall and make install, it reports back to me that it doesn't have necessary permissions. How can I fix this? 

Also, I would like to map keybindings to certain functions such as being able to hide all windows and show the desktop and vice versa (like the button). Is this possible?

Thank you for any response.

---

### Post by cyberdork33 on 2008-05-20
You should not need to 'make' anything for ndiswrapper. Follow the direction here:
[https://wiki.ubuntu.com/MacBookPro/Penryn#head-e5409d2a7a72b4cec1c51303bb2247a83a5659dc](https://wiki.ubuntu.com/MacBookPro/Penryn#head-e5409d2a7a72b4cec1c51303bb2247a83a5659dc)

Depending on what MBP you have, you may need a different windows driver, so it would be best to determine what version machine you have.

```
sudo dmidecode| grep Product
```

I can't really help more with the other issues, someone with a Macbook (Pro) will have to chime in.

---

