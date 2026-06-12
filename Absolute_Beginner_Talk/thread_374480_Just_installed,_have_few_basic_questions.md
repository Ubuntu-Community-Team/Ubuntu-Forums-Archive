---
title: "Just installed, have few basic questions"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by Gru001 on 2007-03-02
Hello all :)

My first post :guitar: 

I installed Ubuntu 6.10 last night and I was really impressed with how the installation went.

I have only 1 hdd and had Windows XP on it.. Ubuntu installation partitioned (resized) the drive and installed with no problems.

BTW my comp is P4 2.4ghz, 512MB DDR333, ESC Mobo with Intel chipset.

Here come the questions:

1. When I try to restart or shut down the Ubuntu closed and I get black screen, however the computer doesn't restart / shut down. I have to use the case buttons for restarting. Do you know if there is a way to fix this?

2. When system is starting I notice many options, can't remember which right now, but there are 5 options and then Windows XP as 6th. I think there is a default generic one, and then 4 others. Which one should I acutally use and does it really matter?

3. My font is very fuzzy / bluurred, it is hard to read anything. I looked around and found that this is a BUG and that it has to do something with ~/.fonts.conf file. They are suggesting deleting this file. Anyone knows how to locate it.

I have other questions too, but they are minor issues. Any help / assistance is greatly appreciated.

Thank you for your time.

---

### Post by raja on 2007-03-02
Welcome to Ubuntu
Answer to 2:
The entries in the grub menu list the available kernels for you to boot into. The first line will be the latest kernel and you should do that. Sometimes, if you have problems after a kernel update it helps to be able to boot to an older version.

---

### Post by dstew on 2007-03-02
Shutdown problems have been solved by using the kernel option apci=force. You add this to the kernel line in the grub list menu. Here is a link to a discussion of this problem:

[http://www.linuxquestions.org/questions/showthread.php?t=496998](http://www.linuxquestions.org/questions/showthread.php?t=496998)

---

### Post by gabng on 2007-03-02
1) Not sure about this.

2) If you've just installed and updated the system, the first entry in the menu should be the default one (latest kernel), so just use that.  The other entries are the previous kernel version before you updated and the debug modes of the two kernels.

3) ~/.fonts.conf refers to the .fonts.conf file in  your home directory, where ~/ refers to your home directory.  To locate the file just open up a terminal and type
```
ls -a
```
and you will see the the file.  To remove it, type
```
rm .fonts.conf
```

---

### Post by xmastree on 2007-03-02
Just to clarify that .fonts.conf file thing. 
The dot at the beginning means that it's a hidden file. That's the same for any file or folder, if there's a dot at the start, it's hidden. So it won't show up in nautilus (the file browser) unless you select *show hidden files* from the view menu (or Ctrl-H).

---

### Post by Gru001 on 2007-03-03
Thank you for replies.

I never managed to fix reboot / shut down problem. I tried both workarounds, but they didn't help. Hopefully the next version will address this.

Font I did manage to fix, but I didn't have the config file, so I changed the the way font is displayed to Subpixel smooting.

I also managed to get the rest of the buttons to work on my Logitech MX700 by just adding few lines to some file :)

Now I have few more noob questions ;)

1. How do you create a folder / go into admin mode to do so?

2. Is there a good location for having just personal files such as media files and downloads

3. Do programs that I install with Automatix have automatic updates, or are there any settings that I need to specify / change. What about Synaptic?

That is it for now. 

My next big project will be to have a good media player installed and have all the codecs installed, and maybe even one day ATI drivers with a control panel that supports TV out :cool: 

Thanks again for you support!

---

### Post by 3rdalbum on 2007-03-03
> **Gru001 said:**
> 

1. How do you create a folder / go into admin mode to do so?



Press Alt-F2 and type: "gksudo nautilus". I suggest adding that command as a launcher on your panel. The window that opens up will allow you to make changes to files in administration mode.

> 2. Is there a good location for having just personal files such as media files and downloads

Your home folder, generally! Otherwise, if you want, you can create a folder in the / (Filesystem) directory, but you'll need to do it via the thing I told you about above.

> 3. Do programs that I install with Automatix have automatic updates, or are there any settings that I need to specify / change. What about Synaptic?

This depends. If the program recieves major bugfixes or security updates, and it's officially supported by Canonical (i.e. it's in the "main" or "restricted" repository), then you will recieve updates through Synaptic. Otherwise, you generally won't get updates automatically.

> My next big project will be to have a good media player installed

Kaffeine! You can install it through Synaptic. Don't worry, it's a KDE program, but it runs fine on Gnome.

---

### Post by hackle577 on 2007-03-03
I would also read through sections 1, 2, and 3 of the official documentation here: [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html)

Happy Ubuntu-ing!

---

### Post by Sabar on 2007-03-31
I saw Gru001 posted a line saying you got your Logitech to work, any way you could explain that a little better?

I have a Logitech Mx700 mouse also that upon startup I get a message that input devise doesn't work or something to that affect.

I have done a search on the forums this seemed to be the closest thing I could find. Tried to do a google search and I got nothing.

Thanks for any help guys 
Sabar:)

---

