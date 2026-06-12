---
title: "windows network problem..."
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by qyte on 2007-03-05
I have connected my ubuntu pc on the same network with a windows PC. Although i can browse a folder like smb://win/music i cannot seem to find a way to play those mp3 files. Is there something i am missing? I Installed XMMS and it plays a file after i copy-paste it on the ubuntu pc but i cannot seem to be able to play the file from within the network. WHY?? :(

---

### Post by punx45 on 2007-03-05
not perfectly sure, but maybe (unless you already have) the network drive needs to be mounted to a local directory?

im not 100% sure on the syntax but it would be similar to mounting a drive.

so it would be something like: mount smb:<host>/win/music /media/windows_music
where /media/windows_music is a directory you created locally.

you can read 'man mount' or maybe the samba docs at [http://samba.org](http://samba.org), or perhaps the ubuntu docs at [https://help.ubuntu.com/](https://help.ubuntu.com/) (note the tabs at the top of the page for the different releases)
there are probably other threads at this forum that you can search for, and finally, if all other information options are exhausted, someone else will probably come along and add to this thread :) 

this would not copy over all the files (so you dont have to worry about taking up all that space) but it does give XMMS a local directory to search in, which is likely to be the problem.

---

### Post by Gerard Barberi on 2007-03-05
Did you install the codecs for them?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

EDIT:  Scratch that I just saw the copy and paste part.

---

### Post by qyte on 2007-03-05
i tried the mount command you gave but it says mount: only root can do that :@

---

### Post by Gerard Barberi on 2007-03-05
Add sudo in front of the command

---

### Post by qyte on 2007-03-05
well i ran
sudo mount smb://NAME/music /media/music
and it says (after the password) can't get address for smb :(

---

### Post by qyte on 2007-03-05
problem solved ;)
here are the steps...
sudo apt-get install samba smbfs
sudo mount -t smbfs //Server/share /mount-pt

:)

---

### Post by punx45 on 2007-03-06
saweet.

---

