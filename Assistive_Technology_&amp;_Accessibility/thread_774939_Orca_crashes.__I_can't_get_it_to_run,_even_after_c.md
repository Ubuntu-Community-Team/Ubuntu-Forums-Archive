---
title: "Orca crashes.  I can't get it to run, even after complete removal/reinstall."
date: 2008-04-29
forum: Assistive Technology &amp; Accessibility
---

### Post by diablo75 on 2008-04-29
Hello.  I am trying to help a friend who is blind with trying Ubuntu out for the first time.  I don't have much hands on experience about Orca, but I didn't think it would be that hard to configure.

So I went into the Assistive technoligies menu, and enabled Orca to run at startup.  It worked after logging out, and logging back in, but it locked up about a minute after the Orca configuration panel came up with the voice in the background.

I've tried to do a complete removal of it via synaptic and then reinstall it, but it still doesn't run.  When I run "orca" from terminal, here's the output I get:

```
jon@jon-laptop:~$ orca
Orca watchdog detected something bad. Cleaning up.
/usr/bin/orca: line 84:  6662 Killed                  /usr/bin/python -c "import orca.orca; orca.orca.main()" "$ARGS"
jon@jon-laptop:~$ 

```

This computer is a fresh install of 8.04 LTS, by the way.

What should I do to fix this?

---

### Post by RCC2k7 on 2008-05-01
I doesn't crash for me, but it locks up upon startup for almost a minute before being usable.

---

### Post by diablo75 on 2008-05-01
Does anybody know how to fix this?  It seems pretty baffling that Orca, the default screen reader for 8.04 LTS, doesn't work even after a complete removal and re-install...

---

### Post by stormdragon2976 on 2008-06-15
Hi,
I haven't had the particular problem you have but I think I may know how to fix it.  When I use Orca for the first time, I have to do alt-f2 and type orca.  I need it to be working in order to access the preferences menu to set it to start when I log in.  So, I wonder if when you set it to start automatically before actually using it if it bypassed the set up for it.  It shouldn't have I don't think, but stranger things have happened.  So, you could try:
alt-f2
orca -t
This will cause Orca to start with the text version of setup.  It should ask you to pick a language, keyboard layout, etc.  If that works, then you could set it to start at log in if you want.
there are a couple of things I have noticed in 8.04 that I don't think were there in 7.10.  The first is any webpage that plays audio or video will freeze your computer if you have flash installed.  If you are using Gnash it will work fine until you click on a link to move to a new page, then it freezes up the computer.  It used not to do that but I think an update didn't agree with it or something.
the other problem is Orca will sometimes go silent.  It's unpredictable when this will happen.  It just stops working for no apparent reason.  When it does, alt-f2 orca will get it going again.
HTH
Storm> **diablo75 said:**
> Does anybody know how to fix this?  It seems pretty baffling that Orca, the default screen reader for 8.04 LTS, doesn't work even after a complete removal and re-install...

---

### Post by DouglasAWh on 2008-06-25
> **stormdragon2976 said:**
> It shouldn't have I don't think, but stranger things have happened.  So, you could try:
alt-f2
orca -t
This will cause Orca to start with the text version of setup.  It should ask you to pick a language, keyboard layout, etc.  If that works, then you could set it to start at log in if you want.

I'm confused to.  Here's what's going on with mine

```

wh@laptop:~$ orca
Welcome to Orca setup.

Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/orca/gnomespeechfactory.py", line 846, in __speak
    return speaker.say(text)
  File "/var/lib/python-support/python2.5/orca/gnomespeechfactory.py", line 106, in say
    return self.gnome_speaker.say(text)
COMM_FAILURE

Restarting speech...

Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/orca/orca.py", line 996, in _showPreferencesConsole
    module.showPreferencesUI(_commandLineSettings)
  File "/var/lib/python-support/python2.5/orca/orca_console_prefs.py", line 437, in showPreferencesUI
    (not setupSpeech(prefsDict)):
  File "/var/lib/python-support/python2.5/orca/orca_console_prefs.py", line 237, in setupSpeech
    speechServerChoice) # server
  File "/var/lib/python-support/python2.5/orca/orca_console_prefs.py", line 106, in sayAndPrint
    speechServer.speak(text, voice)
  File "/var/lib/python-support/python2.5/orca/gnomespeechfactory.py", line 873, in speak
    self.__speak(text, acss, interrupt)
  File "/var/lib/python-support/python2.5/orca/gnomespeechfactory.py", line 853, in __speak
    self.reset()
  File "/var/lib/python-support/python2.5/orca/gnomespeechfactory.py", line 1068, in reset
    self.shutdown()
  File "/var/lib/python-support/python2.5/orca/gnomespeechfactory.py", line 1043, in shutdown
    speaker.stop()
  File "/var/lib/python-support/python2.5/orca/gnomespeechfactory.py", line 109, in stop
    self.gnome_speaker.stop()
COMM_FAILURE

```

Thankfully, I don't NEED this functionality...I can only imagine trying to get something like this to work if you were blind...

---

### Post by stormdragon2976 on 2008-06-25
Hi,
If you have the time, maybe run
code:
ubuntu-bug -p gnome-orca
and file a bug with that.  Would help the Orca developers correct the errors.  I just reported 2 bugs earlier this week and I think I may have found another one.
Thanks

---

### Post by DouglasAWh on 2008-06-25
> **stormdragon2976 said:**
> Hi,
If you have the time, maybe run
code:
ubuntu-bug -p gnome-orca
and file a bug with that.  Would help the Orca developers correct the errors.  I just reported 2 bugs earlier this week and I think I may have found another one.
Thanks

Should it tell me when it's done, or just move on to the next line?

---

### Post by stormdragon2976 on 2008-06-25
Hi,
It should open Firefox to the launchpad page for reporting bugs in Ubuntu with some info already filled in, like package name.  It will also attach a .txt file that should help them debug it.

---

### Post by DouglasAWh on 2008-06-25
> **stormdragon2976 said:**
> Hi,
It should open Firefox to the launchpad page for reporting bugs in Ubuntu with some info already filled in, like package name.  It will also attach a .txt file that should help them debug it.

oh, didn't do that.  Just brought up this box saying it was gathering information and went away...unless I accidentally closed the window or tab

---

### Post by strange_cathect on 2008-06-29
I can confirm this problem. Orca "browns out" when I open it. My only choice is to try to close it. Then I'm told that it is "not responding."

---

### Post by cheesphht on 2008-10-23
Same here - brown out. Tried running various ideas up there but all it ever says in the terminal is "Welcome to Orca setup" and that's all. 

Has anyone ever found out about this problemo?

the magnifier comes in real handy for me

---

### Post by JohnCarcinogen on 2009-03-24
I had a similar problem - by any chance do you run a firewall app?

In my case, I looked for a bug. It seemed to be one, but couldn't fix it. 
So I turned to process of elimination - kill small apps until I found one that may or may not conflict with Orca and....WAAALAAA! I found out that Firestarter (my firewall tool) was causing Orca to hang.

Try killing one small app at a time - a clock app (I run one), a weather app, etc. And keep trying Orca after stopping those apps one at a time.
Hopefully, you'll find it. 
That's how I found my solution, anyway.

After I exited/killed firestarter, Orca went back to normal. 

Since I don't use Orca, this really isn't a problem - but I'd like to see if I can find a firewall app that doesn't conflict with Orca.

Hope this helps!

---

