---
title: "How do I change application fonts in Dapper?"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by skywatcher on 2007-04-02
Hi

I use Dapper on both my laptop and desktop computers, and on both I find that the font size on applications such as Cartes du Ciel, Lazarus, SciLab etc. are big and ugly. I've tried to change this in System > Preferences > Font, but this only affects desktop fonts etc., not the application font. I also added gnome-settings-daemon to System > Preferences > Sessions > Startup Programs, but this doesn't help. The screen resolutions on both machines are set to maximum.

Can anyone tell me how I can get smaller fonts in these applications?

Many thanks!

---

### Post by justin whitaker on 2007-04-02
> **skywatcher said:**
> Hi

I use Dapper on both my laptop and desktop computers, and on both I find that the font size on applications such as Cartes du Ciel, Lazarus, SciLab etc. are big and ugly. I've tried to change this in System > Preferences > Font, but this only affects desktop fonts etc., not the application font. I also added gnome-settings-daemon to System > Preferences > Sessions > Startup Programs, but this doesn't help. The screen resolutions on both machines are set to maximum.

Can anyone tell me how I can get smaller fonts in these applications?

Many thanks!

Interesting question, one which I never really thought about. Most apps have internal font folders and settings...I think you can hack at the configuration files to change that. 

I found this online for java fonts:

[http://www.evolutionnext.com/blog/2006/06/28/1151511032040.html](http://www.evolutionnext.com/blog/2006/06/28/1151511032040.html)

There are about 30 pages on fonts here:

[http://ubuntuforums.org/tags/index.php/font/](http://ubuntuforums.org/tags/index.php/font/)

Could be that somewhere in there is the answer.

---

### Post by skywatcher on 2007-04-02
Thanks, JW

I'll check it out. Judging by the fact that programs such as InkScape and KDevelop have normal-sized fonts in their menu bars etc., I think you're right: it is clear that some hacking will be necessary for those programs that have funny fonts.

Cheers

---

### Post by kerry_s on 2007-04-02
If there gtk-2.0 apps you can use a gtkrc-2.0 to set a font for all gtk2 apps.

open a terminal and type
sudo gedit .gtkrc-2.0
put this

gtk-font-name="verdana 12"

Of course change the font to what you use. :)
(might need to restart X)

---

