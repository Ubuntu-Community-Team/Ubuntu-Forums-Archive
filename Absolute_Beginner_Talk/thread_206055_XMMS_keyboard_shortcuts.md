---
title: "XMMS keyboard shortcuts?"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by Flavian on 2006-06-29
Hi there!
I have a question.
Since in Windows I always controlled my Winamp with global hotkeys, so that I didn't have to get the focus on Winamp, just hit a button on the keyboard and it did pause / play whatever I wanted, I am searching for the same thing for XMMS as well!
I did some research on the XMMS site under plugins and here through the search function, but could not find anything that helped me.

I am sure there is someone out there that can show me the plugin I am searching for and give me a small howto install the plugin.

Thanks in advance!
Flo

---

### Post by ajgreeny on 2006-06-29
Have a look at *xmms-itouch* if you have a logitech keyboard or perhaps *xmms-xf8audio*.  I don't know anything more about either of them but they could just be what you want.  Alternatively you could use the *xmms-status-plugin*, which puts a small icon on the task bar from which you can control xmms without the main window showing, not quite what you wanted but perhaps better than nothing.

---

### Post by Flavian on 2006-06-29
Thanks for your answer, xmms-xf86audio works perfectly.
The bad thing is that XMMS has to be FOCUSED to use the hotkeys :(

I'd love to have plugin that I can use as a globalhotkey plugin, no matter what I do, I would love to pause and play.
Does anybody know a solution??

Flo

---

### Post by Flavian on 2006-06-30
Found an easy to do solution.
Installed the plugin, as mentioned above and then just assigned keys in
"System" "Pref" "Keyboard Shortcuts" under sound.

I have no idea if the plugin and the keyboard shortcuts work together, all I know is that it did not work with just the keyboard shortcuts setting...
So everyone who wants global hotkeys for XMMS, this is the way to do it ;)

Flo

---

### Post by krebul on 2008-01-21
I have not had such luck.  I've tried xmms-xf8audio but my multimedia shortcuts do nothing at all, even when I have XMMS focused.  I've also tried xmms-itouch but the plugin causes xmms to crash as soon as I click the enable radio button.

I've tried numerous other methods such as xbindkeys but no luck.  In the Gnome Keyboard Shortcuts tool, The only entry for the xf8audio is Pause.  The other actions just show the raw key code for the multimedia keys, but when I press the keys, no resulting action.

I even tried hand editing  ~/.gconf/apps/gnome_settings_daemon/keybindings/%gconf.xml.  I forced the global keybindings to use the xf8audio addon and rebooted.  I saw the right bindings in the gnome Keyboard Shortcuts tool, but when I hit the keys, xmms did not respond, with or without focus.

Sucks to be me?  :(

---

