---
title: "Taskbars gone"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by RippyFish on 2007-04-27
Hi 

I am a real Ubuntu noob when it comes to fixing problem like this. I updated my son's PC from 6.10 to 7.04 and after the restart both top and bottom taskbars have gone.

When the system is booting to the desktop both bars flash on and off a few times then disappear all together. I did get one error about already running a panel but I don't get that anymore.

Even logging in as root has the same problem.

I have googled the problem without any luck and have done a search of this forum but have not found any fixes for this problem.

So I hope there is a fix this as my 5 year old son can no longer play his games.

Thanks.

---

### Post by deadgobby on 2007-04-27
[http://doc.ubuntu.com/screencasts/Customising_Ubuntu_Desktop](http://doc.ubuntu.com/screencasts/Customising_Ubuntu_Desktop)

---

### Post by Rotaj on 2007-04-27
If you right-click where a panel should be, do you get a panel menu?

---

### Post by DSn0wMan on 2007-04-27
I dont know if it will help in your case, but when my panels are missing I just tell it to ```
killall gnome-panel
``` then the panels come back.

---

### Post by RippyFish on 2007-04-27
> **Rotaj said:**
> If you right-click where a panel should be, do you get a panel menu?

All I get when I right click (anywhere on the desktop) is the standard right click menu, create folder, create launcher etc.

---

### Post by RippyFish on 2007-04-27
> **DSn0wMan said:**
> I dont know if it will help in your case, but when my panels are missing I just tell it to ```
killall gnome-panel
``` then the panels come back.

How do I get into Terminal when i don't have the top taskbar?

---

### Post by deadgobby on 2007-04-27
Applications>Terminal if it is there. If not Please watch this link
[http://doc.ubuntu.com/screencasts/Customising_Ubuntu_Desktop](http://doc.ubuntu.com/screencasts/Customising_Ubuntu_Desktop)

---

### Post by kittyhawk63 on 2007-04-27
> **RippyFish said:**
> How do I get into Terminal when i don't have the top taskbar?

Don't know if this help. When you have the menu bar Alt_F1 will open the file drop down. You might try it. Can't do any harm.
kh

---

### Post by RippyFish on 2007-04-27
> **deadgobby said:**
> Applications>Terminal

But with no taskbar at the top (or bottom) I cannot do that.

---

### Post by DSn0wMan on 2007-04-27
alt+f2 will let you run a command

---

### Post by RippyFish on 2007-04-27
> **kittyhawk63 said:**
> Don't know if this help. When you have the menu bar Alt_F1 will open the file drop down. You might try it. Can't do no harm.
kh

Gave it a try but nothing happened. Thanks anyway.

---

### Post by deadgobby on 2007-04-27
Duh thanks for that DNs. Yes Alt + f2 and click on know applications.

---

### Post by Rotaj on 2007-04-27
Try Ctrl + Alt + F2 to access a terminal window

---

### Post by RippyFish on 2007-04-27
> **DSn0wMan said:**
> alt+f2 will let you run a command

alt+f2 did nothing but ctrl+alt+f2 got me into a black terminal screen. When I typed in "killall gnome-panel" I got this reply gnome-panel:no process killed (also tried sudo at the beginning of the command).

---

### Post by DSn0wMan on 2007-04-27
That means that gnome-panel is not running. You can try running gnome-panel and see what kind errors it is throwing.

---

### Post by pebo on 2007-04-27
...or Ctrl+Alt+f1 will take you to a virtual console (Ctrl+Alt+f7 will get you back)...
edit: too slow:(

---

### Post by RippyFish on 2007-04-28
> **DSn0wMan said:**
> That means that gnome-panel is not running. You can try running gnome-panel and see what kind errors it is throwing.

OK, tried typing gnome-panel in terminal and got this back, cannot open display.

---

### Post by DSn0wMan on 2007-04-28
I am guessing that there is some configuration problem with your XServer. Just make a backup of /etc/X11/xorg.conf then run sudo dpkg-reconfigure xserver-xorg

---

### Post by kittyhawk63 on 2007-04-28
Do you know the command to make a back up copy of xorg.conf?

---

### Post by DSn0wMan on 2007-04-28
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

### Post by kittyhawk63 on 2007-04-28
Ctrl+Alt+F1
Type the following. You may want to write it down.

[SIZE=4]**sudo cp -i /etc/X11/xorg.conf /etc/X11/xorg.conf.bak**[/SIZE]

If you can't get back into Linux  after you reboot...
Enter safe mode at boot up. I can't remember what it is called. You will know it when you see it. Maybe someone can type it for him.

Type the following when you see yourname@yourname:~$

[SIZE=4]**sudo cp -i /etc/X11/xorg.conf.bak /etc/X11/xorg.conf**[/SIZE]

The "X" in X11 is a capital letter.

---

### Post by jiminycricket on 2007-04-28
Are you running the ATI fglrx or nVidia 3d driver, 'nvidia'?  Have you tried substituting in 'vesa' for the driver in /etc/X11/xorg.conf?   BTW gnome-panel didn't start because it needs to target an X display, this has a bit of explanation albeit referencing XFree86 instead of xorg: [http://www.linuxjournal.com/article/3083](http://www.linuxjournal.com/article/3083)

---

### Post by RippyFish on 2007-04-28
> **kittyhawk63 said:**
> Do you know the command to make a back up copy of xorg.conf?

> **DSn0wMan said:**
> ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Thanks, I googled that one up.

I will try to reconfig the xserver shortly and let you know the out come.

---

### Post by RippyFish on 2007-04-28
All fixed, you guy's are legends.

My son says a big thank you to the internet people for fixing his computer.

---

### Post by kittyhawk63 on 2007-04-28
> **RippyFish said:**
> All fixed, you guy's are legends.

My son says a big thank you to the internet people for fixing his computer.

Tell your son we were all glad to help.
**Post us exactly what you did to get it fixed.**
kh

---

### Post by paparucino on 2007-04-28
> **RippyFish said:**
> How do I get into Terminal when i don't have the top taskbar?

Alt-F2 gives you a command line.
As said before, try to right-click on the bottom of the screen, a list of options should appera. Select "Add a panel"

---

### Post by RippyFish on 2007-04-28
> **DSn0wMan said:**
> I am guessing that there is some configuration problem with your XServer. Just make a backup of /etc/X11/xorg.conf then run sudo dpkg-reconfigure xserver-xorg

I did what was suggested in this post and it worked a charm.

---

### Post by kittyhawk63 on 2007-04-28
> **RippyFish said:**
> I did what was suggested in this post and it worked a charm.

Rippyfish,
Post that your problem was fixed. Go to your original post and choose "Edit." Then click "Go Advanced." Choose toward the top of the page that has appeared that you have the problem "resolved." Click "Save."
kh

---

### Post by Pikestaff on 2007-05-01
RippyFish, what sort of settings did you input when you reconfigured xorg?  Because I am having this exact same problem (except on Dapper) and I've tried everything in this thread as well as reconfiguring xorg and I'm still having the same problem.

---

### Post by kittyhawk63 on 2007-05-01
> **Pikestaff said:**
> RippyFish, what sort of settings did you input when you reconfigured xorg?  Because I am having this exact same problem (except on Dapper) and I've tried everything in this thread as well as reconfiguring xorg and I'm still having the same problem.

Pikestaff,
Please restate your problem. Several things have been discussed here.
kh

---

### Post by Pikestaff on 2007-05-01
I actually have figured it out :)  My problem was that I had both KDE and Gnome installed and I had customized my KDE a lot and those settings were interfering with Gnome.  I solved it by going into System Settings and Appearance and unchecking the box that said "Use my KDE style in Gtk applications".

---

### Post by ericdegen on 2007-05-30
Same issue here as well.  The Killall gnome-panel does work for me, but I'd sure like to know why and fix this from happening almost each time I boot.

---

### Post by whistlerspa on 2007-06-10
> **RippyFish said:**
> How do I get into Terminal when i don't have the top taskbar?


Thanks that fixed my problem

---

