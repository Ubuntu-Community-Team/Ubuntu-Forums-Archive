---
title: "Total newbie question"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by Lochaber on 2006-03-21
Installed Ubuntu 5.04, not without problems (multiple restarts).

Now when I boot the machine, it takes me to some weird command-like thing in the form:

myName@myMachine: $_

I just want to get to the desktop and start playing with programs? What on earth is this new obstacle?

---

### Post by WoodyMahan on 2006-03-21
[QUOTE=Lochaber]Installed Ubuntu 5.04, not without problems (multiple restarts).

Now when I boot the machine, it takes me to some weird command-like thing in the form:

myName@myMachine: $_

I just want to get to the desktop and start playing with programs? What on earth is this new obstacle?[/QUOTE]


Ubuntu 5.04 is an older version.  I would recommend downloading the 5.10 version and trying again.  I'll check around and see if there is a command line you can type in there to start your desktop environment.

---

### Post by resolutioncenter on 2006-03-21
Something obviously went wrong with your install (did you by any chance try to do a custom install? If so, don't).

What you are seeing is the command line. If you are not getting any errors, you probably simply didn't install a graphical user interface.

If you indeed did a custom install, maybe simply reinstalling and chooses the default install would be the easiest option.

However, you could also try to install the desktop from the command line.
1. Log in: Type your user name at the prompt and press enter
You'll then need to give your password (Simply type it in and press enter, you will not be able to see that you are typing)

2. After you loged in successfuly install the desktop:
Type sudo apt-get install ubuntu-desktop.
Press enter.
Type your password again and press enter.

3. After everything needed is installed, restart your computer:
sudo restart

Hope this helps.

---

### Post by ncappel1 on 2006-03-21
[QUOTE=WoodyMahan]Ubuntu 5.04 is an older version.  I would recommend downloading the 5.10 version and trying again. [/QUOTE]

Great advice. you would not belive how much better 5.10 is than 5.04. If you feel like waiting just a little bit though, the Dapper release is coming out really soon.

good luck!

---

### Post by taurus on 2006-03-21
[QUOTE=ncappel1]Great advice. you would not belive how much better 5.10 is than 5.04. If you feel like waiting just a little bit though, the Dapper release is coming out really soon.

good luck![/QUOTE]
Really soon for Dapper now means June 1st!!!

---

### Post by IYY on 2006-03-21
There could be an error with your X server, or maybe it's just not running for some reason.

Try:

**sudo gdm**

And if that doesn't work, also try:

**startx**

---

### Post by xshady87 on 2006-03-21
I had the same problem. I posted a thread on the topic and got it fixed. Here's the link: [http://www.ubuntuforums.org/showthread.php?t=146587](http://www.ubuntuforums.org/showthread.php?t=146587)

---

