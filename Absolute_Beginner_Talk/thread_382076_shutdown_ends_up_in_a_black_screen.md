---
title: "shutdown ends up in a black screen"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by soul814 on 2007-03-11
Whenever I shut down my computer, I'm always stuck in a black screen. There is a blinking cursor and I can type random stuff and it doesn't do a thing. I have to hold my power down button in order to shut my computer. When I boot my computer always has to run through a fsck check. What is that screen I am in?

---

### Post by mk04 on 2007-03-11
> What is that screen I am in?

I believe that is what they call a CLI (Command Line Interface). Try typing "exit" or "shutdown -a" then press enter.

---

### Post by soul814 on 2007-03-11
I don't know. I thought it was xserver crashing after I was doing some research.

My screen looks like this
> _

That underscore is a blinking cursor.

---

### Post by mk04 on 2007-03-12
Does it boot up okay?

---

### Post by astrolabio on 2007-03-12
What exacly is your pc? A notebook? Does it have a Ati video card? 

Post your complete configuration here.

---

### Post by lwylie on 2007-03-12
I have a similar problem every so often, but it happens only 1 out 50 shutdowns or so.  What I do to properly shutdown is to:

- switch to a virtual term (<ctrl> <alt> <F1>)
- log in with a sudo enabled account
- type sudo shutdown -h now

It will take about a minute or so and then eventually shutdown.  Hopefully that helps.

~Luke

---

### Post by zbrox on 2007-03-12
I have the same problem on the Edgy I've installed on my girlfriends computer. However it happens on every halt attemp. The message that it hangs on is that of stopping the DBus daemon. Same symptoms - black screen, cursor blinking. The keyboard however is not respongding, so I can't enter the login data on another tty to diagnose the problem fully.

Anyone has any idea? I'll try searching the bug database about this.

---

### Post by zbrox on 2007-03-15
I found out what the problem was. In my case, the machine connected to the Internet using rp-pppoe 's command "pppoe-connect". So to automate things for my girlfriend I man a script that set up the correct routing and launched the pppoe. However I have accidentally added this script to all runlevels. So when trying to halt or reboot the script was being executed again and the computer couldn't stop the ppoe connection and couldn't continue with the teardown.
I removed the script from runlevels 0 (halt) and 6 (reboot) and now everything is OK! :)

---

