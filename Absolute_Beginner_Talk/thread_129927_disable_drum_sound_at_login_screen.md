---
title: "disable drum sound at login screen"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by Vega on 2006-02-15
man that sound gets on my nerves! How can I disable it?


keepthechange.

---

### Post by David Corrales on 2006-02-15
Go to System -> Preferences -> Sound and disable (or change) the default sound for the question event.

---

### Post by PhilOSparta on 2006-02-15
When I go into this application  System->Preferences->Sound, the Sound Events tab has events and sounds listed for games.  I have removed all the games from my system.  How can I get these events and sound references removed from the tab?  There must be a file somewhere that contains them.
I have been unable to find it.

I have found that the individual game sound lists are at /etc/sound/events
If you delete individual sound list files you delete their listing from the Sound Events tab.
Example: Delete /etc/sound/events/gnibbles.soundlist  and the Nibbles game sound events are removed from the Sound Events tab.

---

### Post by soonindallas on 2006-02-15
System->Preferences->Sound

Do you not have sounds for "system events" ?

The drum sound seems to be question.wav assigned to question events.

Of course if you disable it here you won't get an audible warning for other questions.

---

### Post by mcduck on 2006-02-15
System/Preferences/Sound won't help. It only configures users personal sound settings.

Open System/Administration/Login Screen Setup, and 'Accessibility'-tab. Then unmark 'Make a sound when login window is ready'. The drum sound is gone :)

---

