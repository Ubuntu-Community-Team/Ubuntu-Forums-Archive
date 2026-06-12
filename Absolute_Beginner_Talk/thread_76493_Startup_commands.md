---
title: "Startup commands?"
date: 2005-10-15
forum: Absolute Beginner Talk
---

### Post by bengtfalke on 2005-10-15
In what file do I put commands that should be executed each time a user logs in, for example the startup command for beagle search daemon. This command can not be executed by root.

regards/falke

---

### Post by drummer on 2005-10-15
'System > Properites > Session' has a tab that allows you to add programs to fun when gnome starts up (ie. each time you log in). Just click add, enter the command you need to run and set/leave the 'order' to 80, or there abouts. Sorry if the names of menus i've written aren't exactly correct, I'm not at my linux box at the moment... hope you can fine them alright.

---

### Post by SilentCacophony on 2005-10-15
> System > Properites > Session
Pretty close :) System > Preferences > Sessions, then select 'Startup Programs' tab.

Also, any additions there will be run as the user for that session, not as root.

---

### Post by PeaceMessenger on 2005-10-15
While we're at it,  How can I add a command at startup to run as root?
much obliged.

---

### Post by drummer on 2005-10-15
[QUOTE=PeaceMessenger]While we're at it,  How can I add a command at startup to run as root?
much obliged.[/QUOTE]
do you mean run as root when gnome starts or when the computer boots? the former I'm not sure about, but for the latter you can make a script and put it in /etc/init.d
something like this:```
#! /bin/sh
# /etc/init.d/run_this_as_root
[command to run as root]&
exit 0
```make it executable too with "sudo chmod +x /etc/init.d/run_this_as_root"

---

### Post by az on 2005-10-15
You can also edit your sudoers to allow certain commands to be executed as root without asking for the password (NOPASSWORD).  You can use that in your session startup if it is more approprate than playing with the runlevel initscripts.

---

### Post by drummer on 2005-10-15
[QUOTE=azz]You can also edit your sudoers to allow certain commands to be executed as root without asking for the password (NOPASSWORD).  You can use that in your session startup if it is more approprate than playing with the runlevel initscripts.[/QUOTE]
[http://ubuntuguide.org/#usesudowithoutpasswordprompt](http://ubuntuguide.org/#usesudowithoutpasswordprompt)

but it isn't secure.. with the sudoers file changed like that, you can run anything as root through the sudo command without being propted for a password. This should be fine as long as you pay attention to what you're doing when editing config files, system files, etc. and also to who uses the system, since when you're logged in, anyone can get root access without being asked a password.

---

### Post by cpscotti on 2005-10-16
Ok, but in mine it does not work!

I must execute the script:

xmodmap -e 'keysym w = w W w question question question'

to correct my keyboard, happens that when I put this line on teh Sessions Startup programs list, it is executed (I think) but not takes effect!

and as far as I know it does not need to be executed with sudo, i tried putting sudo on it, even worst: the next login was NO-GOOD!!!!

Anyone can help &#322; (<--- lol 'question mark' should be there)

Thanks

---

### Post by drummer on 2005-10-16
do you need the single quotes? and are you sure the syntax of the command is right? if it runs correctly in a terminal, it should work when you add it to the sessions, as far as i can tell. I have a few commands that run when I login and all work fine, even the first which has attributes as well (see attached pic). Perhaps you could try changing the 'order', some of my commands run with an order of 50 (can't remember why they do, or why i set them to :P).

---

### Post by davmac on 2005-10-16
Adding a script that runs, as root, at startup is not too difficult.

1. Make sure you put your script in /etc/init.d (ask if you need more help to write the script - but there are other threads covering this)

2. Make sure the script is executable by typing "sudo chmod +x /etc/init.d/myscriptname"

3. Type "sudo update-rc.d myscriptname defaults"

Another alternative is to edit /etc/init.d/bootmisc.sh and add the commands in here.

Hope this helps,

Dave Mac

---

