---
title: "Uh oh! I broke the GUI!"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Dysan on 2007-05-09
I'm posting from the live CD, lol...

I tried to get my Desktop Effects to work, so I tried to get my ATi card working by reading [this](http://ubuntuforums.org/showthread.php?t=414194) and then followed [this](http://ubuntuforums.org/showthread.php?t=418489) thread.
Ctrl+Alt+Backspace aaaaaaaaand I'm like... at the real basic dos menu, or whatever, and I don't know what to do.
Please help!

---

### Post by jfinkels on 2007-05-09
> **Dysan said:**
> I'm posting from the live CD, lol...

I tried to get my Desktop Effects to work, so I tried to get my ATi card working by reading [this](http://ubuntuforums.org/showthread.php?t=414194) and then followed [this](http://ubuntuforums.org/showthread.php?t=418489) thread.
Ctrl+Alt+Backspace aaaaaaaaand I'm like... at the real basic dos menu, or whatever, and I don't know what to do.
Please help!

After you log in, type the following:
```

sudo dpkg-reconfigure xserver-xorg

```
Then type your password and press enter.

---

### Post by MrPyro321 on 2007-05-09
This might help:

If you want to turn off desktop effects from the command line, I am assuming you cannot see anything on your desktop, you may have a white or black screen.
First, restart by pressing CTRL- left ALT-Backspace
You will see a login screen.
before logging in, click the button for options at the lower right
then click change session
You may have gotten this far already, but perhaps another reader is having the same problem, so,
Select failsafe terminal
now login
at the prompt type:
gconf-editor
this will open up the registry
now select Desktop->Gnome->Applications->window_manager
the current and default key values will probably say /usr/bin/compiz
select the key value by clicking once on the key value
you can completely erase both the default and current values and when ubuntu restarts it will automatically fill in these vaules with /usr/bin/metacity
You can alternatively enter in /usr/bin/metacity for [b]both[b] the current and default values.
Now restart (Ctrl_left Alt-Backspace) and at the login screen change your session back to xclient and login.

everything's back to normal (if you left the key values blank, it will take a second for everything to appear normal)
hope this helps

[Source]("http://ubuntuforums.org/showthread.php?t=417015")

---

### Post by corstar on 2007-05-09
Ha, I love the title of your post. Gold

---

### Post by Dysan on 2007-05-09
> **jfinkels said:**
> After you log in, type the following:
```

sudo dpkg-reconfigure xserver-xorg

```
Then type your password and press enter.

Just came back from trying that.
It seems to work... but I then have to go through a really long set up, and I'm not sure how to do it without breaking something.

---

### Post by afljafa on 2007-05-09
> **MrPyro321 said:**
> This might help:

If you want to turn off desktop effects from the command line, I am assuming you cannot see anything on your desktop, you may have a white or black screen.
First, restart by pressing CTRL- left ALT-Backspace
You will see a login screen.
before logging in, click the button for options at the lower right
then click change session
You may have gotten this far already, but perhaps another reader is having the same problem, so,
Select failsafe terminal
now login
at the prompt type:
gconf-editor
this will open up the registry
now select Desktop->Gnome->Applications->window_manager
the current and default key values will probably say /usr/bin/compiz
select the key value by clicking once on the key value
you can completely erase both the default and current values and when ubuntu restarts it will automatically fill in these vaules with /usr/bin/metacity
You can alternatively enter in /usr/bin/metacity for [b]both[b] the current and default values.
Now restart (Ctrl_left Alt-Backspace) and at the login screen change your session back to xclient and login.

everything's back to normal (if you left the key values blank, it will take a second for everything to appear normal)
hope this helps

[Source]("http://ubuntuforums.org/showthread.php?t=417015")

Wow - Iv`e been having problems with a completely messed up gnome session all day. That was the very fix I needed.

Cheers.

---

### Post by Dysan on 2007-05-09
> **MrPyro321 said:**
> This might help:

If you want to turn off desktop effects from the command line, I am assuming you cannot see anything on your desktop, you may have a white or black screen.
First, restart by pressing CTRL- left ALT-Backspace
You will see a login screen.
before logging in, click the button for options at the lower right
then click change session
You may have gotten this far already, but perhaps another reader is having the same problem, so,
Select failsafe terminal
now login
at the prompt type:
gconf-editor
this will open up the registry
now select Desktop->Gnome->Applications->window_manager
the current and default key values will probably say /usr/bin/compiz
select the key value by clicking once on the key value
you can completely erase both the default and current values and when ubuntu restarts it will automatically fill in these vaules with /usr/bin/metacity
You can alternatively enter in /usr/bin/metacity for [b]both[b] the current and default values.
Now restart (Ctrl_left Alt-Backspace) and at the login screen change your session back to xclient and login.

everything's back to normal (if you left the key values blank, it will take a second for everything to appear normal)
hope this helps

[Source]("http://ubuntuforums.org/showthread.php?t=417015")

Oh, wtf? I can't even log in! It says that I need to make sure that my username and password are capitalized properly! WTF?!

---

### Post by Dysan on 2007-05-09
I tried my user name, dysan, and then desktop-dysan, but it still says that it's not correct. Any ideas before I just go and reinstall? ><

---

### Post by ectospasm on 2007-05-10
Mine wasn't as severe a problem, as failsafe GNOME worked, and if I logged into regular GNOME the windows would show, just metacity wouldn't start and many windows (most notably gnome-terminal) were completely unresponsive.  As my gconf-editor window manager settings were already set to /usr/bin/metacity, resetting them didn't work.  

What did work was turning on desktop effects in System/Preferences/Desktop Effects.  That set the default window manager to /usr/bin/compiz.  Weird, but I'm satisfied for now.

---

### Post by stewvmusic on 2007-05-15
> **MrPyro321 said:**
> This might help:

If you want to turn off desktop effects from the command line, I am assuming you cannot see anything on your desktop, you may have a white or black screen.
First, restart by pressing CTRL- left ALT-Backspace
You will see a login screen.
before logging in, click the button for options at the lower right
then click change session
You may have gotten this far already, but perhaps another reader is having the same problem, so,
Select failsafe terminal
now login
at the prompt type:
gconf-editor
this will open up the registry
now select Desktop->Gnome->Applications->window_manager
the current and default key values will probably say /usr/bin/compiz
select the key value by clicking once on the key value
you can completely erase both the default and current values and when ubuntu restarts it will automatically fill in these vaules with /usr/bin/metacity
You can alternatively enter in /usr/bin/metacity for [b]both[b] the current and default values.
Now restart (Ctrl_left Alt-Backspace) and at the login screen change your session back to xclient and login.

everything's back to normal (if you left the key values blank, it will take a second for everything to appear normal)
hope this helps

[Source]("http://ubuntuforums.org/showthread.php?t=417015")

Using the above method would not work for me without an extra tweak.  Even when I would use the above changes several times Compiz would still take over after a couple of seconds and again I would have a white screen every time I would log in.  Here is what I had to do:

I had to add the extension ".old" to compiz in order for it not to take over the desktop.  To do this insert these commands at the terminal prompt after changing back to the default values in gconf-editor and exiting:

*user*@*host*:~$ cd /usr/bin
*user*@*host*:/usr/bin$ sudo mv compiz compiz.old
Password: *your sudo password if requested*

Then logout using <Ctrl-left><Alt><Backspace> and at the login screen go Options->Select Sessions...->Gnome -> hit Change Sessions button and login as normal.  Your desktop should be back to normal without Desktop Effects.

Don't forget to rename compiz again if you install the restricted driver and want to run Compiz or Beryl.

---

