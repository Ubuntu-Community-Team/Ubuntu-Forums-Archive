---
title: "Misc. Noobie Questions...feel free to post a Question"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by mbrang00 on 2006-07-22
Im going to start this thread with intent to consolidate alot of the misc non important/non-technical question. As mentioned anyone can feel free to ask here so long as it is not too involved of a question.

Ill start:

A Couple of Newbee Questions for today:

So I read a post that said someone was running xubuntu and another that was running kubuntu...Which one am I running? 


How do I take a screenshot? Is it the same as the "Legacy OS" and use Print Screen or is it diffent, Id experiment, but i have my wirelees working finally and dont want to take the risk of screwing somthing up...

Thats all I have for now,
Thanks in advance for your input.

---

### Post by GuitarHero on 2006-07-22
If you got your cd image off of ubuntu.com you are running ubuntu.  Another way to tell is color, brown is ubuntu, blue is kubuntu, dark blue/black is xubuntu.  They are just different desktop environments.  Basically they are all the same OS with different menus/interfaces etc.  In ubuntu there is a take screenshot button in one of the main drop down menus at the top.

---

### Post by mbrang00 on 2006-07-22
Ahhh Thanks for the input.. you are absolutly right about the screenshot. And it looks like I have the regular ol' ububtu....good enough for me
Thanks agian, Im sure ill come up with more questions 2morro, getting tired now.

---

### Post by moma on 2006-07-22
Start a terminal window program from the Applications -> Accessories -> Terminal menu.

These commands will reveal the type of system you run. Type commands in a terminal window.

$ [COLOR="Green"]cat /etc/issue[/COLOR]
Ubuntu 6.06 LTS \n \l

$ [COLOR="Green"]cat /etc/*release*[/COLOR]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06 LTS"

Use this command in scripts
$ [COLOR="Green"]lsb_release -c [/COLOR]
Codename:       dapper
--------------------------------------------

How to take a screenshot?
Use menu selection: Applications -> Accessories -> Take a Screenshot.

or just type this in a terminal window.
$ [COLOR="Green"]gnome-screenshot[/COLOR]

With 4 seconds delay.
$ [COLOR="Green"]sleep 4; gnome-screenshot[/COLOR]

KDE (Kubuntu distro) has an excellent "ksnapshot" command.

// moma
  [http://www.futuredesktop.com/ubuntu6.06.html#guides]("http://www.futuredesktop.com/ubuntu6.06.html#guides")

---

### Post by Drakkor on 2006-07-22
Ian't there a keyboard shortcut to makd a screenshot ?  Thanks ! :KS

---

### Post by argie on 2006-07-22
My Print-Screen button does that fine.

---

### Post by mbrang00 on 2006-07-22
I found the same thing...Print screen did the job...what is neat, i found that if you have a particular window selected it will take a shot of just that window, if you want an overall screenshot, just deselect that window.

---

### Post by Sef on 2006-07-22
To print a section of the screen:

1)Make sure the item you want to take a picture of is in the foreground.

2) Hold down the alt button.

3) Press print screen.

---

