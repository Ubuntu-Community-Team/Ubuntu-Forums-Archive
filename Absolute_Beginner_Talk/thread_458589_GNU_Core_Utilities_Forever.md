---
title: "GNU Core Utilities Forever?"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Toe-Maus-nOOb-Is on 2007-05-29
I have a situation that I got into. I was running D. Drake 6.06 LTS on my laptop with all systems Go. After gettting my wireless configured, I went to Ubuntu Upgrades and started searchin. I decided on an utils upgrade called Gnu Coreutils, I rebooted and came up with a nice black screen prompting me to log in. 

What I was in was GNU core Utilities 5.93 in the full terminal mode, No desktop and no graphics? It might be a server because there are tty0, tty1, tty2, thru tty6 options? The boot sequence puts me into this operating system and I can't seem to get out of it. 

Is there a possible option without having to reinstall Ubuntu 6.06?  Can I get my GUI/desktop back? Or can I work hand and hand with both systems with options to go back and forth? 

Thank you in advance for your help.

---

### Post by GrueTamer on 2007-05-29
I don't know what to do to get out of it, but if you don't mind, I have a little knowledge to share with you.

The tty things...you've always had them.  When you hit ctrl+alt+f1, you go to tty1.  With f2, tty2, f3, tty3, etc etc.  Ctrl+alt+f7 brings you back to your graphical interface.

Try typing "startx" in the terminal that you get when you log in.  It sounds like X isn't starting up, so startx should start it up.

If none of these things help, in that terminal, type

```
sudo apt-get install ubuntu-dsektop
```

to make sure that it's installed.  If it is, then startx should've taken you.  At this point, if you can't get back to your GUI, there's probably a misconfigured xinit file or something.  If that happens, I'll tell you what you can do, but this probably isn't the case (well, that's what my current level of knowledge leads me to believe, of course)

---

### Post by Toe-Maus-nOOb-Is on 2007-05-29
GrueTamer,
Want to thank you for a quick fix! I struggled with that situation for about 6 hours. GUI/Desktop LIVES! Thank You again. 


Toe-Maus-nOOb-Is

---

