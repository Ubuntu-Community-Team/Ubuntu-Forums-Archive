---
title: "Exaile"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by Armman on 2007-08-20
I just installed Exaile but it won't start. So I ran it through Terminal and this is what it says,

:xubuntu@xubuntu:~$ exaile
Traceback (most recent call last):
  File "/usr/share/exaile/xl/xlmisc.py", line 36, in <module>
    from xl import mozembed
  File "/usr/share/exaile/xl/mozembed.py", line 29, in <module>
    import gtkmozembed
ImportError: No module named gtkmozembed
Traceback (most recent call last):
  File "exaile.py", line 2635, in <module>
    main()
  File "exaile.py", line 2627, in main
    exaile = ExaileWindow(options, fr)
  File "exaile.py", line 148, in __init__
    self.player = player.ExailePlayer(self)
  File "/usr/share/exaile/xl/player.py", line 460, in __init__
    GSTPlayer.__init__(self)
  File "/usr/share/exaile/xl/player.py", line 254, in __init__
    self.setup_playbin()
  File "/usr/share/exaile/xl/player.py", line 573, in setup_playbin
    GSTPlayer.setup_playbin(self)
  File "/usr/share/exaile/xl/player.py", line 257, in setup_playbin
    self.playbin = gst.element_factory_make('playbin')
PluginNotFoundError: playbin

What does this mean?

---

### Post by smoker on 2007-08-20
>  ImportError: No module named gtkmozembed
>  PluginNotFoundError: playbin

looks like you are missing the above, where did you install from?

perhaps uninstall, and try reinstalling again.

---

