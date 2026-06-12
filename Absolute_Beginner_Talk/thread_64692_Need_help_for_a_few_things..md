---
title: "Need help for a few things."
date: 2005-09-11
forum: Absolute Beginner Talk
---

### Post by America's Reject on 2005-09-11
Ok, I installed it for the second time and it has not fixed the problem.  Here are my issues.

First, when Ubuntu is loading I get two things that "Failed".  They go by way to fast for me to see.  I "think" one of them is "General Console Interface Fonts" but can't be sure.  How can I find out what is wrong.  I am an absolute Linux noob.

Second, my screen resolution.  How can I get it to be 1280x1024, right now I can only go as high as, 1024x768.  I am using a DELL 17" monitor.

Thanks,
America's Reject

---

### Post by windowsatemyhomework on 2005-09-11
[QUOTE=America's Reject]Ok, I installed it for the second time and it has not fixed the problem.  Here are my issues.

First, when Ubuntu is loading I get two things that "Failed".  They go by way to fast for me to see.  I "think" one of them is "General Console Interface Fonts" but can't be sure.  How can I find out what is wrong.  I am an absolute Linux noob.

Second, my screen resolution.  How can I get it to be 1280x1024, right now I can only go as high as, 1024x768.  I am using a DELL 17" monitor.

Thanks,
America's Reject[/QUOTE]
 I was just recently in the same boat that you are. Find out from either Dell's website or your monitor user's manual what the specifications of your monitor are. Then open a terminal and type ```
sudo gedit /etc/X11/xorg.conf
```(Assuming you are using gnome/ubuntu. If you installed Kubuntu/KDE, substitute "kate" for "gedit".)

Scroll down to where you see "Section 'Monitor'". In that section, change the numbers after "HorizSync" and "VertRefresh" to reflect the values for your monitor. 

Next go down to the next section, called "Section 'Screen'". Under every "Subsection 'Display'", add "1280x1024" to the list of resolutions for each "Depth". 

Save the document, close it, and reboot. That was all it took to fix mine, best of luck!

---

### Post by America's Reject on 2005-09-11
umm how do I get into terminal and what did u use?

I get thsi error Cannot Open Display when I type that into the thing when I press ctrl + alt + f1

I have my specs I just need to figure out how to edit the file.

---

### Post by windowsatemyhomework on 2005-09-11
[QUOTE=America's Reject]umm how do I get into terminal and what did u use?

I get thsi error Cannot Open Display when I type that into the thing when I press ctrl + alt + f1[/QUOTE]
 If you're in ubuntu/gnome, in the top left click "Applications", highlight "system tools" and select "Terminal". If you're in kubuntu/KDE, click in the bottom left, highlight "system" and choose "Konsole". Then follow the previous instructions.

---

### Post by wellery on 2005-09-11
[QUOTE=America's Reject]umm how do I get into terminal and what did u use?

I get thsi error Cannot Open Display when I type that into the thing when I press ctrl + alt + f1[/QUOTE]

You get to the terminal by using the menu in the top left corner:

applications->system tools->terminal

---

### Post by America's Reject on 2005-09-11
I fucked up, now I can't load says it can't load the graphical interface or something.

How can i go about undoing the changes I made and trying again?

here is what i added to the file thing exactly as I typed

HorizSync30-95
VertRefresh50-160

then to eat of the things that had resolutions: "1280x1024"

1280x1024 is highest i can go with monitor and 60 refresh.  Where did I mess up?

---

### Post by America's Reject on 2005-09-11
[QUOTE=America's Reject]I fucked up, now I can't load says it can't load the graphical interface or something.

How can i go about undoing the changes I made and trying again?

here is what i added to the file thing exactly as I typed

HorizSync30-95
VertRefresh50-160

then to eat of the things that had resolutions: "1280x1024"

1280x1024 is highest i can go with monitor and 60 refresh.  Where did I mess up?[/QUOTE]
 ANy way I can edit files through windows? lol

[http://support.dell.com/support/edocs/monitors/e773s/En/specs.htm](http://support.dell.com/support/edocs/monitors/e773s/En/specs.htm)

anyone have AIM or MSN and can tak to me?  Or just reply to this thread

---

### Post by windowsatemyhomework on 2005-09-11
[QUOTE=America's Reject]I fucked up, now I can't load says it can't load the graphical interface or something.

How can i go about undoing the changes I made and trying again?

here is what i added to the file thing exactly as I typed

HorizSync30-95
VertRefresh50-160

then to eat of the things that had resolutions: "1280x1024"

1280x1024 is highest i can go with monitor and 60 refresh.  Where did I mess up?[/QUOTE]
 The only thing that I see that should have been different is that there should be a tab between each name and the numbers associated with them ```
HorizSync       30-95
VertRefresh     50-160
```Don't copy and paste what I just put here, because the interface on these forums won't let me put in tabs. Just go back into the file (using terminal > sudo gedit /usr/src/X11/xorg.conf), and place a tab before the numbers. Give that a shot.

I just thought of something. Did you mean that it's not letting you get back into the graphical interface of linux and you typed that last message from windows? Because if that's the case then you have to go about this differently.

If it won't let you into the graphical ubuntu at all, then you have to just use the command line interface (like a DOS prompt). log in with your usual username and password, then type "sudo nano /usr/src/X11/xorg.conf". It won't be as pretty as gedit was, but you will be able to edit the file the way that I described above (add the tabs). To save from within nano, press Ctrl+O (the letter, not number), and hit enter to save it with the same filename that it already had. Then reboot and see if it lets you into the graphical user interface (GUI).

---

### Post by America's Reject on 2005-09-11
[QUOTE=windowsatemyhomework]The only thing that I see that should have been different is that there should be a tab between each name and the numbers associated with them ```
HorizSync       30-95
VertRefresh     50-160
```Don't copy and paste what I just put here, because the interface on these forums won't let me put in tabs. Just go back into the file (using terminal > sudo gedit /usr/src/X11/xorg.conf), and place a tab before the numbers. Give that a shot.

I just thought of something. Did you mean that it's not letting you get back into the graphical interface of linux and you typed that last message from windows? Because if that's the case then you have to go about this differently.

If it won't let you into the graphical ubuntu at all, then you have to just use the command line interface (like a DOS prompt). log in with your usual username and password, then type "sudo nano /usr/src/X11/xorg.conf". It won't be as pretty as gedit was, but you will be able to edit the file the way that I described above (add the tabs). To save from within nano, press Ctrl+O (the letter, not number), and hit enter to save it with the same filename that it already had. Then reboot and see if it lets you into the graphical user interface (GUI).[/QUOTE]
 I am using my computer (in windows) and parents (in windows) to type these.

I get the blue error box of death

---

### Post by windowsatemyhomework on 2005-09-11
[QUOTE=America's Reject]ANy way I can edit files through windows? lol

[http://support.dell.com/support/edocs/monitors/e773s/En/specs.htm](http://support.dell.com/support/edocs/monitors/e773s/En/specs.htm)

anyone have AIM or MSN and can tak to me?  Or just reply to this thread[/QUOTE]
 Yeah, I'm on AIM. travisparker84.

---

