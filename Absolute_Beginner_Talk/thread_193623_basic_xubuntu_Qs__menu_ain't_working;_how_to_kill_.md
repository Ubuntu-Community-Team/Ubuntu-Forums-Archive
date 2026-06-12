---
title: "basic xubuntu Qs:  menu ain't working; how to kill app"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-06-10
Hello,


I installed xubuntu-desktop on a computer running ubuntu. I chose Xubuntu in the sessions option in the login screen.


1.  I was playing around with the panels and deleted the default-ly installed "Applications" menu in the upper-left hand corner of the screen (Panel 1). I right clicked on the panel-->Add New Item-->XFCE Menu. But when I click on the mouse, no menu appears.

In "Edit Menu"/ Menu File,  I tried both  "Use default desktop menu file" and "Use custom menu file" but neither work. Before I deleted the orignal menu (Applications Menu"), the menu worked. By the way, the menu file in the blank underneath "Use custom menu file" points to /home/hanzj/.config/xfce4/desktop/menu.xml

Oh, I just saw the Applicaiton Menu on my panel now. It doesn't work now either.

2. I've got an application that won't close. Specifically, it's the "Preferred Applicaitons" dialog. Is there a way to force it to quit?

---

### Post by blackjack6.21.91 on 2006-06-10
In XFCE i think the forcequit is in your Task Manager (it might be called the Program Lister, too)

No help with the first problem though.

---

### Post by Dr. Nick on 2006-06-10
to kill any program in any gui you can use this command in a termnal. Just use "killall *appname"* That will require a sudo for most administrative programs running as root. here is specific command for software properties dialog

killall gnome-default-applications-properties

---

### Post by TehLiberating on 2006-06-29
on the first problem, there is a Xubuntu Dapper bug: 

The menu editor (xfce4-menueditor) doesn’t work as expected, and might eat your menu. To restore the default menu: remove ~/.config/xfce4/desktop/menu.xml, log out from Xfce and then log in again.

---

### Post by NJC on 2007-06-26
> **blackjack6.21.91 said:**
> In XFCE i think the forcequit is in your Task Manager (it might be called the Program Lister, too)



Thanks ... this worked well. I was wondering where this was hiding.

---

### Post by alan_daniel on 2007-06-26
As another option, in the future, there's the sometimes "fun" xkill...if you type the command "xkill" in a terminal, whatever you click on next will be forced to quit. Note that this does not always kill the corresponding process, so it is not the best solution, but it can be entertaining and somewhat fulfilling to "xkill" a misbehaving app.

---

### Post by gruss on 2008-01-14
Ohhh xkill is fun, thanks!!!

---

### Post by jackmo on 2008-01-17
> **Dr. Nick said:**
> to kill any program in any gui you can use this command in a termnal. Just use "killall *appname"* That will require a sudo for most administrative programs running as root. here is specific command for software properties dialog

killall gnome-default-applications-properties

nice one, cheers.

Can you tell me how I find out what applications are called or bring up a list of currently running aplplications?

thanks

---

### Post by mart007 on 2008-02-11
I think that running the command:

top

will show you the current processes running.  I may, however, be wrong...  ;-)

---

### Post by sideburns on 2008-04-22
If you want to know all running processes and their ID, use this:

ps -aux

Then, if it's a process you own you can kill it with

kill -9 XXXX

Where XXXX is the ID of the process in question.  Use sudo if it's not your own process, of course.

BTW, thanx for the xkill tip.  I'm helping my sister learn Ubuntu, and was looking for the easy, non-tech way.  I've now added it to Accessories on her main menu, so that she doesn't even need to open a terminal, and I'm planning on doing that on my own Fedora box.

---

