---
title: "nvidia-settings GUI won't open, can't use tools"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by samuraiCat on 2007-06-21
Hi, everyone. Let my preface this by saying I've spent a couple of hours searching for a solution to this issue all over the web and this forum. I don't see anything yet, so I guess I'll add to the deluge of problems. Thanks in advance.

Okay, here's the issue: I have a nvidia GeForce FX 5200. I used Envy to install drivers, then I went into xorg.conf and fixed my horizontal and vertical stuff, as well as setting it to 1024x786. The strange thing is that while I have a menu item under Settings called "nvidia settings," which I assume is the GUI, when I click it I get an error message telling me it can't open. When I go to the terminal and type "gksudo gedit nvidia-settings," nothing happens. 

Now, are there any tools in that GUI that help to adjust and tweak the performance of the FX 5200? Is there any other way to tweak the card? Obviously, I'm coming from XP, and there was a whole control panel worth of crap--is there any corresponding level of control in Linux, is this wysiwyg?

Please keep in mind that I'm a total newbie, so please tell me pretty explicitly what to do if you have suggestions. Thanks!

Edited to add: Despite all my (self-caused) problems with Ubuntu/Linux so far, I love it. That love is mainly due to the support of the community. You rock.

---

### Post by Ayuthia on 2007-06-21
You should be able to go to the terminal and type nvidia-settings.  I am not for sure if you need gksudo or not, but if you do, you do not need gedit (it is a text editor).

---

### Post by Happy_Man on 2007-06-21
The command isn't ```
gksudo gedit nvidia-settings
```, it's ```
gksudo nvidia-settings
```

FYI, Gedit is a text editor. Your previous command told the computer to open this application with a text-editor in superuser mode. Kinda weird, isn't it? :D

---

### Post by deadlikeoscar on 2007-06-21
I just typed nvidia-settings only and it popped right up. Since I used the Restricted Drivers Manager I didn't get an icon. I just downloaded one I found in Google and added a launcher to my System-->Administration panel with the command nvidia-settings. I had to move the icon into my pixmaps folder through the terminal but it was well worth it. I wish I would have known that the Nvidia panel worked in Ubuntu with the Restricted Driver. My Dad switched to Fedora 7 for that reason alone.:(

---

### Post by shavenlunatic on 2007-06-21
make sure you have gksu (or gksudo) before nvidia-settings of when you click "Apply" and then click "Save to xorg.conf", it will apply what it can but won't save anything to the xorg.conf file (meaning the settings won't be aplpied properly on a restart of X



edit: woohooo, 100 Post party!

---

### Post by samuraiCat on 2007-06-21
> **Happy_Man said:**
> The command isn't ```
gksudo gedit nvidia-settings
```, it's ```
gksudo nvidia-settings
```

FYI, Gedit is a text editor. Your previous command told the computer to open this application with a text-editor in superuser mode. Kinda weird, isn't it? :D

Sorry! I wrote those in my post from memory. I think I did use "gksudo nvidia-settings", but I'm not sure. I'll try again when I get home.

---

### Post by samuraiCat on 2007-06-21
> **deadlikeoscar said:**
> I just typed nvidia-settings only and it popped right up. Since I used the Restricted Drivers Manager I didn't get an icon. I just downloaded one I found in Google and added a launcher to my System-->Administration panel with the command nvidia-settings. I had to move the icon into my pixmaps folder through the terminal but it was well worth it. I wish I would have known that the Nvidia panel worked in Ubuntu with the Restricted Driver. My Dad switched to Fedora 7 for that reason alone.:(

Okay, I'll look for the nvidia-settings package and see if I can get it.

---

### Post by samuraiCat on 2007-06-21
> **Happy_Man said:**
> The command isn't ```
gksudo gedit nvidia-settings
```, it's ```
gksudo nvidia-settings
```

FYI, Gedit is a text editor. Your previous command told the computer to open this application with a text-editor in superuser mode. Kinda weird, isn't it? :D

Yes, that was definitely an error. So, could I do this to edit xorg.conf? > sudo gedit /etc/X11/xorg.conf 

But first, I'm assuming: > $ cp /etc/X11/xorg.conf /etc/X11/xorg.backup2

---

### Post by Happy_Man on 2007-06-21
Yes. ```
sudo gedit /etc/X11/xorg.conf
``` says open this file with Gedit in superuser mode. Wonderful. The other command says copy the contents of the first file to a second file with the specified name. It's really quite simple to get the hang of it.

---

