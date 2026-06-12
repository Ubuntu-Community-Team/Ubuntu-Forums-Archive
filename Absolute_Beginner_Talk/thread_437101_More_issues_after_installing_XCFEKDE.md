---
title: "More issues after installing XCFE/KDE"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Robert98374 on 2007-05-08
OK well heres ths issue now,
when i go back to Gnome instead of using XCFE or KDE it doesnt show that i have a internet connection. I also noticed that i dont have any type of minimize/maximize/close buttons when i open any type of program. I also noticed that when i am in Gnome and i press the show desktop button its says that i dont have a windows manager. Sorry if i didnt include any more information besides what i know.

---

### Post by klayn on 2007-05-08
In Gnome, try:

```
metacity
```

Does it give you the errors after this?

---

### Post by H.E. Pennypacker on 2007-05-08
Are you running Beryl/Compiz?

---

### Post by Robert98374 on 2007-05-08
I was/ running what ever came with Ubuntu

---

### Post by Robert98374 on 2007-05-08
> **klayn said:**
> In Gnome, try:

```
metacity
```

Does it give you the errors after this?

Do you mean in a terminal?

---

### Post by H.E. Pennypacker on 2007-05-08
> **Robert98374 said:**
> Do you mean in a terminal?

You don't have to run a terminal necessarily.  Many times, a forum member will give you terminal instructions when you could actually be using a graphical method.  In this case, try pressing ALT-F2 (a "run" window should pop up), and type metacity; no quotation marks or anything, just metacity.

Does this problem persist even when you restart?  

Have you tried pressing CTRL-SPACE-BACKSPACE?  Pressing these buttons at once is similar to Windows' CTRL-ALT-DELETE, but it is not the same.  Doing this will close everything (force it to close), and take you back to the log-on screen.

---

### Post by Robert98374 on 2007-05-08
1. For some reason all of my short cuts including alt+f2 arent working.

2. Yes i have restarted multiple times and it still persists

3. After i post this ill try the restart of the desktop enviroment.

---

### Post by Robert98374 on 2007-05-08
1. For some reason all of my short cuts including alt+f2 arent working.

2. Yes i have restarted multiple times and it still persists

3. After i post this ill try the restart of the desktop enviroment.

restart of the desktop enviroment does work with ctrl+alt+backspace

---

### Post by H.E. Pennypacker on 2007-05-08
I re-read your original post, and I notice you said the window manager is missing.  The name of Ubuntu's window manager is Metacity.  I don't see how you could have lost it, but usually Beryl is the problem.  

Don't worry about what Beryl is, but have you done anything with "Desktop Effects?"  It is under System > Preferences > Desktop Effects.  Did you do anything with Desktop Effects at any time?  If you did, this could explain the problem.  If you did enable desktop effects, try disabling them.  

If you did not, I am not sure what to say.  Try re-installing Metacity.  Do a Synaptic search for "metacity."  Locate "metacity" (there is nothing else in the name, just metacity).  Right click, and mark for re-installation.

I was going to suggest you try metacity --replace when the ALT-F2 window pops up, but your shortcuts don't work.

---

### Post by Robert98374 on 2007-05-08
Ok ill try to reinstall  metacity, i tried to enable some of the Desktop effects but it didnt do anyting so i just disabled it

---

### Post by H.E. Pennypacker on 2007-05-08
> **Robert98374 said:**
> Ok ill try to reinstall  metacity, i tried to enable some of the Desktop effects but it didnt do anyting so i just disabled it

For now, stay away from Desktop Effects.  Once you have everything up and running, use Beryl, if you must.  Go to Beryl-project.com for more information on Beryl.

---

### Post by Robert98374 on 2007-05-08
Will do but i want to get this one working before moving anywhere else :-)
 ok tried to reinstall metacity

after it was all done and over with there was a pop up error stating

An error  occurred
the following details are provided
E:Postfix: subprocess post-installation script returned error exit status 75

I opened up the terminal  just to see if there was an obvious error message and i saw  the message keep popping up many times and it was 

Hostname:Unknown Host

i hope that helps i also had to copy some other instructiuons that i saw that were in the terminal

[:465: Computer :unexpected operator Postfix configuration was not changed. If you need to make changes, edit/etc/postfix/main.cf (and others) as needed. To view postfix configuration values. see post config

I couldnt copy/paste it from the terminal since when i right clicked nothing came up and i tried the manual CTRL+C and CTRL+V

---

### Post by H.E. Pennypacker on 2007-05-08
You and I could work together to solve these cryptic problems, but you may be wasting your time.  I could try to help you figure out the answers to all these errors, but you would probably be better off with a re-installation, if you do not mind.

If you have done nothing with your computer so far, try re-installing.  If you have important content on your /home partition, make sure you DO NOT reformat when re-installing.  For a general installation procedure (identical to a re-installation, EXCEPT FOR the formatting part - NEVER format a partition that has important content), see this guide:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

PS:  Re-installing Ubuntu takes about twenty minutes, and finding solutions to problems could last hours, if not days.

---

### Post by Robert98374 on 2007-05-08
The only issue with reinstalling i lost my CD and i don't have a CD burner on this computer. I do have a friend thats going to be sending me a copy but, I would like to try to work out this problem. i have confidence in out abilities to figure this out.

---

### Post by Robert98374 on 2007-05-08
I remeber that when i was installing KDE it asked me about Email clients, i remember that  it asking about the server information that i used for email, i said that i use an internet site and it put the host name in the field. whats the command to uninstall KDE and XCFE?

---

### Post by H.E. Pennypacker on 2007-05-08
The errors that you posted earlier relate to Postfix, and it's not something you need.  Ignore those Postfix errors, and do me a favor by completely uninstalling Postfix.  Uninstall Postfix using Synaptic.

As for the host name errors, let them be.  It's not important, because they can't possibly have anything to do with Metacity.  Let's get back to Metacity.  After looking up Metacity using Synaptic, you presumably right-clicked on metacity, and selected the re-install option.  I then assume you clicked on "Apply."  After the re-installation process, I am assuming Metacity was correctly installed.  I am also assuming you restarted your computer.

Still having a problem?  If so, let's completely uninstall Metacity using Synaptic.  Once the uninstallation process is done, close out of Synaptic, start up Synaptic again, and install Metacity.  Do a Metacity search, and install it from the beginning.  

When done installing Metacity, you should have the following installed:

1.  Metacity.
2.  Metacity-common.
3.  libmetacity0.

If either one of those is not installed, install them.  Then restart.  Let me know if you are having any problems thereafter.

---

### Post by Robert98374 on 2007-05-08
Ok ill try that

---

### Post by Robert98374 on 2007-05-08
All 3 were installed i am going to try to uninstall KDE and XCFE to see if that might fix it for now

---

### Post by H.E. Pennypacker on 2007-05-08
> **Robert98374 said:**
> All 3 were installed i am going to try to uninstall KDE and XCFE to see if that might fix it for now

You were still supposed to have completely uninstalled Metacity, closed Synaptic, opened Synaptic again, and installed Metacity again.  This would see if anything went wrong.

Try that before you uninstall KDE and XFCE.

By the way, are you having any problems with KDE and XFCE?

---

### Post by Robert98374 on 2007-05-08
Thats when these problems started, after i installed them. i did that exactly, i even restarted the machine after i uninstalled metacity and reinstalled.

---

### Post by Robert98374 on 2007-05-08
OK uninstalled KDE and Completely uninstalling Metacity again, going to restart the computer *crosses fingers*

---

### Post by Robert98374 on 2007-05-08
OK well after i restarted i can only get into hte terminal through the login in screen. how do i start gnome?

---

### Post by Robert98374 on 2007-05-08
OK well i did the sudo aptitude install ubuntu-desktop
But still has the same issues, i am wondering how to completely uninstall all of my gnome files... i am going to try to make another profile to see if that works

---

### Post by H.E. Pennypacker on 2007-05-08
> **Robert98374 said:**
> OK well i did the sudo aptitude install ubuntu-desktop

So where are we now?  Is everything okay now?

---

### Post by Robert98374 on 2007-05-08
Under root it all works fine, i know that i am not supposed to luse root but this was the ultimate test

---

### Post by Robert98374 on 2007-05-08
i opened a new profile and it all works fine, now i am going to try to figure out what went wrong with my old profile. Thanks for the help :-)

---

### Post by H.E. Pennypacker on 2007-05-08
I am wondering if the .metacity (hidden folder) in your home folder was, somehow, damaged.  If you uninstall Metacity, delete the .metacity folder, and re-install Metacity, it may work.  See if that works.  If this does work, we can conclude that the .metacity folder was the problem.

PS:  Press CTRL-H in your home folder to view hidden folders.

---

### Post by Robert98374 on 2007-05-08
Alright i can try that too,
yep i just go under the view and check the little box there :-)

---

### Post by H.E. Pennypacker on 2007-05-08
> **Robert98374 said:**
> Alright i can try that too,
yep i just go under the view and check the little box there :-)

What box?  I am sorry, but I totally missed that sentence.

Did it work?

---

### Post by Robert98374 on 2007-05-09
No it didnt work. i ultimatly just decieded to delete the profile since there was a problem with it, the little box under view

---

### Post by klayn on 2007-05-09
sorry, please disregard

---

