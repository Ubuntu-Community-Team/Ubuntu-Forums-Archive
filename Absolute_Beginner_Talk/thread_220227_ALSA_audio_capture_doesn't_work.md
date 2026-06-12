---
title: "ALSA audio capture doesn't work"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-07-21
in System/Preferences/multimedia Systems Selector, when I press the "Test" key under Default Audio Plugin (while ALSA is the Plugin which is selected), I get an error message

 " Advanced Linux Sound Architecture: Could not open resource for reading."

What's wrong?

---

### Post by halfvolle melk on 2006-07-21
Maybe the mic is of. You can check that by entering 'alsamixer' in a terminal.

---

### Post by hanzj on 2006-07-21
i ran alsamixer, but wasn't sure what to look for. please refer to screenshot.

---

### Post by halfvolle melk on 2006-07-21
Hmm, that looks fine. With the up and down arrows you can switch the "Mic sele" between Mic1 and Mic2, but I don't think that will help in this case.
I don't know, sorry.

---

### Post by hanzj on 2006-07-21
I even tried restarting the sound server.



:~$ /etc/init.d/alsa-utils restart
 * Shutting down ALSA...  * warning: 'alsactl store' failed with error message 'alsactl: save_state:1190: Cannot open /var/lib/alsa/asound.state for writing'...                  [[COLOR="Red"]fail[/COLOR]]
 * Setting up ALSA...                                                    [ ok ]

There was a "fail", so I ran it with sudo.

sudo /etc/init.d/alsa-utils restart
Password:
 * Shutting down ALSA...                                                 [ ok ]
 * Setting up ALSA...                                                    [ ok ]



Yet when I go back to Testing the audio plugin in System/Preferences/Multimedia, I still have the same error.

---

