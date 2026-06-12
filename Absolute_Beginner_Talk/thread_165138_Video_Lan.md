---
title: "Video Lan"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by reuschle on 2006-04-24
Hey folks,

I'm new here, so be not that hard with stupid questions for the first time. I'm running the new beta release of the Dapper Drake and I tried to run a bunch of avi files with the Kaffeine Player but at standard it seems not to have the appropriate codecs. I thought about to install the VLC Player but don't know exactly how to install the appropriate version since I'm new in the linux scene.

I'm glad about any help,
thanks a lot,
Chris

---

### Post by Nikusan on 2006-04-24
[QUOTE=reuschle]Hey folks,

I'm new here, so be not that hard with stupid questions for the first time. I'm running the new beta release of the Dapper Drake and I tried to run a bunch of avi files with the Kaffeine Player but at standard it seems not to have the appropriate codecs. I thought about to install the VLC Player but don't know exactly how to install the appropriate version since I'm new in the linux scene.

I'm glad about any help,
thanks a lot,
Chris[/QUOTE]

To install VLC, in a terminal type
```
sudo apt-get install vlc
```

when prompted for a password enter your user account's password.

To get the codecs for other players read [this guide]("https://wiki.ubuntu.com/RestrictedFormats").

---

### Post by Nikusan on 2006-04-24
Whoops! vlc is in universe and you probably don't have that enabled yet. Please read [AddingRepositories]("https://wiki.ubuntu.com/AddingRepositoriesHowto") for instructions on adding universe.

---

### Post by reuschle on 2006-04-24
Hey thanks, worked well. I had already activated the repositories. Take care,
Chris

---

