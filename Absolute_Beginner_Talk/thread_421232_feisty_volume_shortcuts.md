---
title: "feisty volume shortcuts?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by cdiem on 2007-04-24
Hi, I've recently installed feisty (after using edgy for a while). I went through the forum, but could not find anything regarding this.
This may sound like a stupid question, but I'll ask it anyway - 
in Edgy I had configured via the System->shortcuts my sound to increase with Ctrl+up and decrease with Ctrl+down, and got used to it. However, when I try configuring shortcuts with feisty, it doesn't work (the sound of mic goes up or down instead, and not of PCM.) 

How could I configure the sound shortcuts? 

P.S. I could not find any commands for sound running gconf-editor and searching for metacity shortcuts.

---

### Post by aktiwers on 2007-04-24
Did you go into System => Preferences => Keyboard Shortcuts
And change it there?

If you did and it didnt work, maybe this guide will work..
[http://ubuntuforums.org/showthread.php?t=79717](http://ubuntuforums.org/showthread.php?t=79717)

Good Luck..

---

### Post by cdiem on 2007-04-25
Thanks, I have tried this one, but I actually could't make it work. Anyway, this doesn't look like a major problem - whenI listen to music I just won't use global hotkeys (I aslo could'n adjust any hotkeys for exaile in gconf-editor, something that was very easy to be done in Edgy).
But, thank you very much for your answer, and for bothering to find this info. Maybe with some update in a month or two this will be fixed by itself.

---

### Post by amosharper on 2007-06-16
I appreciate that this thread has been buried, but for the record (as this is the first UbuntuForums post that comes up in a relevant Google search) here is the very simple solution:

- Go to System >> Preferences >> Sound
- Under 'Default Mixer Tracks', select the device and tracks you wish to control with the keyboard shortcuts defined in System >> Preferences >> Keyboard Shortcuts

Magic! No need for xbindkey or anything of that sort.

Cheers,

- Amos

---

