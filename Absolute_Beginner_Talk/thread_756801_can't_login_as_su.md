---
title: "can't login as su?"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by Sanoski on 2008-04-16
Well, I finally got that ISO file burned. I just used a different program and it burned fine. Now everything seems to be alright. There's just this one thing. I can't login as super user. When I type 'su' it asks for my password, but the keyboard doesn't type anything. 

I was trying to install Thunderbird to work with Gmail. But when I tried to go into the terminal and login as root it does this. Any ideas? Keep in mind this is my first time running Linux. It's probably something simple.

---

### Post by cybil on 2008-04-16
use sudo before your commands, root is disabled

---

### Post by Znort_Ubern00b on 2008-04-16
when you use su or sudo command in terminal it asks for password it will not show on screen what you type. if you are in admin group you type your password and press enter it should then do what needs to be done

NEVER login as root or default to use root this is a failsafe in linux

---

### Post by Joeb454 on 2008-04-16
the keyboard does type stuff, it just won't show, it's a security feature :) It's always been the case as far as I know.

If you want to log in  as root from a terminal, then use ```
sudo -i
``` but be careful what you do while logged in as root!

If you just want to install Thunderbird, run ```
sudo aptitude install thunderbird
``` from a terminal :)

---

### Post by hyper_ch on 2008-04-16
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Calash on 2008-04-16
Root is disabled by default in Ubuntu.  The preferred security method is SUDO.  To use it you would type  sudo command , where command is the application you wish to run.  It will prompt you for your current password, then execute the program with root privileges.

Here is a link with more info

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

When entering your password in the terminal, it never shows what you type.  Just type the password and hit enter and you will be fine.

Edit: I am slow today :)

---

### Post by gunksta on 2008-04-16
Welcome to Linux! 

You can't actually log in as su because su is a command, not a user. Ubuntu uses su to enable you to run individual commands or scripts as the root user. I would recommend that you read this.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

As I new user, I commend your willingness to drop down to the command line and get your hands dirty with the CLI. If you want to learn how to use a command, try typing in the command "man" or "info". Thus, if I wanted to learn more about the command su, I would type:

man su

OR

info su

While you are learning, you can soften the learning curve by using some of the excellent graphical utilities provided by Ubuntu. Go to Applications --> Add/Remove Software OR use Synaptic to install thunderbird. It will ask you for YOUR password and then it will let you install stuff.

---

### Post by Sanoski on 2008-04-16
I love you guys! Awesome, it's up and running flawlessly. I am so happy right now. There's no way I'll be able to sleep tonight. You guys are the best. I know, I should really do my own research on simple stuff like this. Reading the documentation would of probably told me this wouldn't it? I just knew it was something simple. I was just too excited about finally getting my system up and running. Thanks again!

---

### Post by hyper_ch on 2008-04-16
[http://www.psychocats.net](http://www.psychocats.net)

[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

[https://wiki.ubuntu.com](https://wiki.ubuntu.com)

[http://www.ubuntuforums.org](http://www.ubuntuforums.org)

Those for plus google should solve most problems.

Enjoy

---

