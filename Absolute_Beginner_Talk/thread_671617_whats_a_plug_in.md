---
title: "whats a plug in?"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by chuck88 on 2008-01-18
totem says this: Please install the necessary plugins and restart Totem to be able to play this media. I still can't play dvds. I wish there was a "make it so number one" button to push. Any Ideas?

---

### Post by Nezing on 2008-01-18
Chuck,a plugin is simply "code" software to allow apps to work.You might visit a web site,and you see a message**;"install missing plugins"**.This is so media can "play" in your browser.

As far as playing dvd's are concerned:

open up **Terminal** and copy and paste this line of code in:
[B]
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse[/B]

You might get asked for your password,after this.Just follow the instructions,then proceed.

Press **enter **on your keyboard,and let Terminal go to work.At some stage it will ask you do you wish to continue-Y/N  Press Y on your keyboard,and let Terminal finish the install.

When this has happened,copy and paste this into Terminal:
[B]
sudo /usr/share/doc/libdvdread3/install-css.sh[/B]

Then press** enter **on your keyboard.When Terminal has finished,close it up,and try a media file,via  Totem.

---

### Post by st33med on 2008-01-18
Also, these plugins are considered illegal in the USA because of hungry patent trolls and the MPAA. Just to warn ya, K?

However, nobody has been sued over libdvdcss2 yet (a codec required to play DVDs), but I don't want to risk it. Your choice, though.

---

### Post by chuck88 on 2008-01-18
alright, meow I got sound, but still no picture

---

