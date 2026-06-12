---
title: "Installing Google Earth"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by RichPicker on 2007-03-01
The .bin file is on my desktop.

When I type this in the terminal:

sudo sh GoogleEarthLinux.bin

I get ths:

sh: Can't open GoogleEarthLinux.bin

I've read the preceding posts and recommended threads, but can't get past this point.

---

### Post by Maestro23 on 2007-03-01
Try this:
 
> cd /home/username/Desktop

sudo chmod +x GoogleEarthLinux.bin

./GoogleEarthLinux.bin


---

### Post by RichPicker on 2007-03-01
I installed it, and have used it. But the it is not in Applications > Internet.

I have to open usr/local/googleearth   and double-click the application icon.

Where did I go wrong. The app works well, but there is no link to it?

---

### Post by taurus on 2007-03-01
Did you log out and back in again?

---

### Post by RichPicker on 2007-03-02
Yes. I did that.

In the instructions is this line:
"Leave /usr/local/google-earth as the installation path"

The installer wanted to put the application some place else, but I changed it to put it where the instructions say to put it. 

My uneducated guess is that this might be the problem. 

If I re-install it and allow the installer to place it where it wants, I fear I will  have it installed 2 places. I'm not sure what to do next.

---

### Post by taurus on 2007-03-02
I told the installer to place it in ~/bin/google-earth with a link to ~/bin and there is an icon in Applications -> Internet.

---

### Post by RichPicker on 2007-03-02
Okay. I understand how to tell the installer to place it there. But I don't know how to do the link. Can you explain? And if that works for me, how do I remove the previously installed version?

---

### Post by RichPicker on 2007-03-02
Maybe I could just create the link from where it resides on my system now, and not have to reinstall it?

---

### Post by taurus on 2007-03-02
When you install it, you will see a GUI screen with two windows/menus.  The first one asks you where you want to install it.  The second one gives you an option to link it to your ~/bin if you wish.  You don't have to link it by hand.

---

### Post by RichPicker on 2007-03-02
Okay. But will it be installed in two places - the old install and the new? And will I need to remove the older install, and how do I do that?

---

### Post by taurus on 2007-03-02
Where did you install it to the first time?  You probably have to remove it by hand first.

---

### Post by RichPicker on 2007-03-02
How do I remove it. I tried selecting it, but "move to trash" is not available.

---

### Post by taurus on 2007-03-02
Where did you install it to?  You can use the "sudo rm" command to remove it or you can remove it with nautilus.

```
gksudo nautilus
```

---

### Post by RichPicker on 2007-03-03
Well, beans. For two days, this is what I get:

--10:48:06--  [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
           => `GoogleEarthLinux.bin'
Resolving dl.google.com... 66.102.1.91, 66.102.1.93
Connecting to dl.google.com|66.102.1.91|:80... connected.
HTTP request sent, awaiting response... 

And never a response.

---

### Post by taurus on 2007-03-03
From a terminal, run

```
cd ~/Desktop
wget -c http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
```
And once it's done with downloading, then run

```
chmod 755 GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```

---

### Post by RichPicker on 2007-03-03
The installer would only allow me to install it here:
/home/rich/google-earth

With a link to here:
/home/rich

When I changed the location or link, the "Install" button turned gray and innactive. So, it's in my home folder, where I must double-click the application icon, and it is still not in Applications > Internet. 

It works, but I would like to learn what went wrong, and get it installed in the right place. And out of curiosity what is the significance of the "755" in the command?

---

### Post by taurus on 2007-03-03
Have you logged out and back in again (or even reboot)?

```
man chmod
```

---

### Post by RichPicker on 2007-03-03
I restarted the computer. I'll try the command you just sent.

---

### Post by RichPicker on 2007-03-03
Oh sheesh. That's not a command, it's to a manual page. Now you'll know I'm stupid.

I restarted the machine. The problem is, it would not let me install it anyplace other than what was in the installer 'boxes'

---

### Post by taurus on 2007-03-03
Where do you want to install GoogleEarth?

---

### Post by RichPicker on 2007-03-03
It doesn't matter. I'm too pooped to wrestle with it any more right now. I'd like it to be in the same place as the other applications, install the same as the other applications, and launch from Applications > Internet, like the others. And I'd like to understand what I'm doing using Linux, and how to at least use the GUI, but that doesn't look too promising right now. 

When in Romania and Bulgaria last year I needed to be near an English-speaking friend much of the time. Linux is similar. I feel too strong of a dependence on you and others. There is too much of a learning curve for me to learn Linux. I hoped that by now, after two months, I would understand more than I do, but I don't.

I want to use this computer with Linux, without relying on you or others - or have hope that that day will arrive soon - but I still need more help than I want to ask for.

Sorry for the trouble. I can use Google Earth where it is now. Or try installing it again on my own later. Enjoy your weekend. Thank you sincerely for your help.

---

