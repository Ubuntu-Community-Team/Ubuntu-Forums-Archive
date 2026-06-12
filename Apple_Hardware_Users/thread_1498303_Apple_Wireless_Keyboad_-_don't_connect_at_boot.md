---
title: "Apple Wireless Keyboad - don't connect at boot"
date: 2010-05-31
forum: Apple Hardware Users
---

### Post by btg on 2010-05-31
Hello everybody,

This is my first post at this forum, but I have used Ubuntu for some years now. I have used Linux as my only OS since 2003, and Ubuntu has dominated my last three years.

Anyway, I have this MacBook running Ubuntu, and I have fallen in love with Apples way of making keyboards. So when time came to get a new one for the desktop it became an Apple wireless compact keyboard.

I can get it connected and it works great, until I reboot. After each reboot I can't use the keyboard anymore. I look in the BT applet and it says everything is tip-top. I have to disconnect the keyboard and reconnect again to make it start working. Why is this? I would like to be able to have a password on my box, but this cant be done without a working keyboard.  

Sorry for the ugly english, not my first language.

---

### Post by sha.goyjo on 2010-06-01
I know this is a terrible thing to say, but I find the default gnome bluetooth manager to be terribly glitch. I use Blueman. It's in the repo's. See if it helps at all.

---

### Post by btg on 2010-06-01
Yeah, I probably should have said so from the start, I tried that one, it came straight from the Blueman wiki. The same problem exists in Blueman as in the Gnome standard applet. :(

But thank you for replying.

---

### Post by sha.goyjo on 2010-06-01
When I encounter problems like this, I usually use a script to deal with the problem. I know it's not **HOW ITS DONE** but sometimes you just have to say **** it and use bash.

If you have reverted back to the gnome bluetooth manager I can see if I can find some relevant reloading commands, and then maybe we can code in a shell script to rc.local.

---

### Post by btg on 2010-06-02
I am all about shell scripts.
I used to run Slackware on several machines at home, and back then that was equal to writing allot of shell scripts :-D

I have sort of been looking for commands that help me to reconnect on boot, but I have not found anything that I feel right about. I don't know how the gnome applet will feel about me using some other BT tool to reconnect, or is there a good interface for that built in to the gnome applet itself? I will keep looking. And I will thank you for your reply(s).

---

### Post by sha.goyjo on 2010-06-02
Well, I can say this much for sure. Everything in linux that uses bluetooth interfaces through the bluez framework. You can do things to bluez in the command line, but they are complicated and frankly I don't yet understand them well enough to tell you what to do. The bluez people are mostly developers (IE they don't believe in having documentation on their website), but I think this may be helpful to you. [http://web.inter.nl.net/users/hanscees/bluezhowto.html]("http://web.inter.nl.net/users/hanscees/bluezhowto.html")

That should give you some more information on using the command line options of bluez-utils

---

