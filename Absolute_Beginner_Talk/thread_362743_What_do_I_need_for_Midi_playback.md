---
title: "What do I need for Midi playback ?"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Sweet Spot on 2007-02-16
Really simple question. I've got Amarok, and use Totem for movies or short Audio needs. All I want is to test some midi files which I downloaded for ringtones. What should I look for in the respositories in order to enable Midi playback ?

Doug

---

### Post by tubasoldier on 2007-02-16
timidity should work for your needs.

---

### Post by mahiyar on 2007-02-16
You can also try Xmms plugin from here [http://sourceforge.net/project/showfiles.php?group_id=124847](http://sourceforge.net/project/showfiles.php?group_id=124847). There also is a Mplayer plug in for MIDI.

---

### Post by Sweet Spot on 2007-02-17
Hmmm, Timidity failed miserably for me. First off, can't find the GUI, so I guess it doesn't use one. After finding it in usr/bin etc.., I opened a midi file (not poly) and it was totally garbled, and played back slowly. 

As for plug-ins, is there one for totem or Amarok ? I'd rather not install more programs, if I can avoid doing so. 

Doug

---

### Post by tubasoldier on 2007-02-18
Yeah, timidity does not have any graphical interface, its really just a library. If i were to listen to midi files as you want to i would use Kmid (being that i use KDE). However, I have a sound card that is able to emulate midi itself, so I dont have to worry about it. I just load a soundfont. That way I can use my favorite music notation editor to write, edit, and listen to midi. My laptop does the same thing you are describing and I gave up on midi on that thing. 

Sorry I'm not able to help you more.

---

### Post by Sweet Spot on 2007-02-19
Thanks for the honesty. Pretty ironic though. I've been pushing Ubuntu in a thread on my forum, and dared anybody to challenge me to find a task on Ubuntu which I couldn't perform !:-\":lolflag:   Technically, I guess that Kmid should work though, if I really wanted it.

---

### Post by nathanhill on 2007-02-28
To get the GTK gui use the following command syntax:

timidity -ig

Then you get a GUI...

---

### Post by Sweet Spot on 2007-03-21
Thanks Nat, that works. But when I play a .mid file in it now, it's kind of choppy and skips a bit. Anything come to mind ?

Just noticed, I'm getting this:

> (<unknown>:8456): Gtk-CRITICAL **: gtk_text_buffer_get_bounds: assertion `GTK_IS _TEXT_BUFFER (buffer)' failed

(<unknown>:8456): Gtk-CRITICAL **: gtk_text_buffer_insert: assertion `GTK_IS_TEX T_BUFFER (buffer)' failed

(<unknown>:8456): Gtk-CRITICAL **: gtk_text_buffer_insert: assertion `GTK_IS_TEX T_BUFFER (buffer)' failed

(<unknown>:8456): Gtk-CRITICAL **: gtk_text_buffer_get_bounds: assertion `GTK_IS _TEXT_BUFFER (buffer)' failed

(<unknown>:8456): Gtk-CRITICAL **: gtk_text_buffer_create_mark: assertion `GTK_I S_TEXT_BUFFER (buffer)' failed

(<unknown>:8456): Gtk-CRITICAL **: gtk_text_view_scroll_to_mark: assertion `GTK_ IS_TEXT_MARK (mark)' failed

(<unknown>:8456): Gtk-CRITICAL **: gtk_text_buffer_delete_mark: assertion `GTK_I S_TEXT_MARK (mark)' failed


---

### Post by klato on 2007-04-02
i just installed timidity and was able to open a midi file directly from firefox.  the only downside is that there is no way to actually stop the file from playing!  it just plays to complettion and you have no control over it whatsover :(

---

