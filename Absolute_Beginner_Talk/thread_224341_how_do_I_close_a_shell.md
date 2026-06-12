---
title: "how do I close a shell?"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by 8nout on 2006-07-27
Cripes, this is embarassing, how dumb a newbie can I be?

Tried to install Limewire, found many tutorials, open this and open that, at one point they wanted me to type in the "command line"...hah! I can't even find the command line, so I do the google/linux search, tells me to open a shell (ctrl F1?)...I do..log in...can't figure anything out, including how to close the freakin shell! I am at the log-in:
 I am sick of XP crashing and losing all my little treasures and thought this OS would be a way to go but this is way over my head. I'll just buy an external HD and back everything up.

Thanks to all for the installation help.... can someone just tell me how to uninstall it? I have a dual boot with XP.

---

### Post by rocketman768 on 2006-07-27
I don't think you want the F1 console. You want the nice console, so go to the equivalent of the "start menu" and find it in there (has a nice icon of a console screen).

---

### Post by Tango_Down on 2006-07-27
Don't give up yet kiddo, if lime-wire does not work well for linux, there are other options like bit-torent, which honestly works better than traditional file-sharing anyway. Look up Apt-get on google to see all the packages that can be found. If you opend the shell in the GUI, there should be a little X in the corner, otherwise you can either restart your computer with <Reboot>, or you can use <shutdown -h -t secs now>.

---

### Post by bluevoodoo1 on 2006-07-27
Here's a link about terminal locations:
[http://psychocats.net/ubuntu/terminal.html](http://psychocats.net/ubuntu/terminal.html)

To get out of console mode (Ctrl+alt+F1) press Ctrl+alt+F7


Unless you really have your heart set on Limewire, I would suggest using Frostwire. It's very easy to get with Automatix.

---

### Post by Tango_Down on 2006-07-27
[http://ubuntuforums.org/showthread.php?t=33183](http://ubuntuforums.org/showthread.php?t=33183)

That is the sticky for all the nice linux versions of your favorite windows programs. :D And think about it, do you really want to go back to blue screens and <IRQL_NOT_EQUAL_OR_LESS_THAN>? ;)

---

### Post by 8nout on 2006-07-27
I have found a "terminal"? This looks like it may be what I was looking for, Thanks.

What command should I have used to close that F1 shell? (I finally just hit the reset...)

---

### Post by bluevoodoo1 on 2006-07-27
> **8nout said:**
> What command should I have used to close that F1 shell? (I finally just hit the reset...)
here...
> **bluevoodoo1 said:**
> To get out of console mode (Ctrl+alt+F1) press Ctrl+alt+F7

---

### Post by 8nout on 2006-07-27
Thanks to all.... so far the best thing I've found in Linux is the great(and fast) support on this forum!

I will struggle on a little longer.....Thanks again....

---

### Post by catlett on 2006-07-27
The way to exit was already given by bluevodoo

When someone in a tutorial says "open a shell", "get a command line" or "open a terminal", to an Ubuntu user it means going to Applications<Accessories<Terminal.
The terminal is where you will enter a command. The terminal by default opens into a bash shell. For just about everything you will use Ubuntu for, you will use a bash shell. So don't worry about different shells, Just open the terminal.
To confuse you a little more, if the instructions say "open a root terminal", there isn't a root terminal in Ubuntu. All commands are entered into the terminal and if you need "root" priveleges you use the term sudo before the command. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
You should always search Synaptic Package manager first for an application, it is the easiest way to install. Here is a guide on instalation in Ubuntu [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
This is just an Ubuntu thread with linbks to guides on terminal commands [http://ubuntuforums.org/showthread.php?t=45651](http://ubuntuforums.org/showthread.php?t=45651)
If you want an easy "automated" way to install basic computer features i.e. dvd playback, mp3 capabilities, bittorent clients, flash etc, you may want to use Automatix [http://ubuntuforums.org/showthread.php?t=223087](http://ubuntuforums.org/showthread.php?t=223087)
If you want to enable most of the automatix features by yourself from the command line, follow the dapper guide [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)

---

### Post by jimmygoon on 2006-07-27
Its worth mentioning that there are ways to make it seem as if you are in a root terminal. I believe that there is actually a menu entry for opening a root terminal although you may have to enable it in alacarte.

also these commands will get you a root terminal when you are already in a regular terminal

sudo bash
sudo gnome-terminal
sudo -s

There is others I'm sure, like if you use "Konsole" you could do "sudo konsole" I'd imagine (I'm a gnome kinda guy so I can't check)

---

