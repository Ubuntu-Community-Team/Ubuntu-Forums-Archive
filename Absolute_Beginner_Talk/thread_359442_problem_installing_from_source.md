---
title: "problem installing from source"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Ceta on 2007-02-12
I tried installing from source with the instructions at this website: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) but I get the follow error after saving the tar file on my desktop and typing tar -xvzf pspvc-install-0.2.1.tar.gz in the terminal. the name of the file on my desktop is pspvc-install-0.2.1.tar.gz.



rain@the-cube:~$ tar -xvzf pspvc-install-0.2.1.tar.gz
tar: pspvc-install-0.2.1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
Edit/Delete Message

---

### Post by tbroderick on 2007-02-12
Change to Desktop or mv the file to your /home.
```
cd Desktop
tar xvzf pspvc-install-0.2.1.tar.gz
```

---

### Post by Maestro23 on 2007-02-12
And you can always tell where you are at in terminal by typing:

> pwd


---

### Post by Ceta on 2007-02-12
Here's what happened:

rain@the-cube:~/Desktop$ tar xvzf pspvc-install-0.2.1.tar.gz
pspvc-install-0.2.1/
pspvc-install-0.2.1/install.sh
pspvc-install-0.2.1/archives/
pspvc-install-0.2.1/archives/ffmpeg-051130-0.33.tar.gz
pspvc-install-0.2.1/archives/ffmpeg-mh-unix.patch
pspvc-install-0.2.1/archives/ffmpeg-lrintf.patch
pspvc-install-0.2.1/archives/x264_051028.tar.gz
pspvc-install-0.2.1/archives/pspvc-0.2.1.tar.gz
pspvc-install-0.2.1/uninstall.sh

---

### Post by tbroderick on 2007-02-12
Change to the newly created folder pspvc-install-0.2.1 and make sure you have the following installed nasm libfaac-dev libxvidcore-dev and build-essential. Then run the installer.
```
sudo apt-get install nasm libfaac-dev libxvidcore-dev build-essential
sudo ./install.sh

```

---

### Post by Ceta on 2007-02-12
How do I change to that folder?  I open that folder, and run a terminal, and type pwd, but it says I am in my home folder. The pspvc install folder is on my desktop, not home.

---

### Post by Maestro23 on 2007-02-12
> **Ceta said:**
> How do I change to that folder?  I open that folder, and run a terminal, and type pwd, but it says I am in my home folder. The pspvc install folder is on my desktop, not home.

The directory "Desktop" should be under[COLOR="Red"] /home/username [/COLOR]

Get to /home/username

Should see Desktop

[COLOR="Red"]cd Desktop[/COLOR]

Should see the file in question.

---

