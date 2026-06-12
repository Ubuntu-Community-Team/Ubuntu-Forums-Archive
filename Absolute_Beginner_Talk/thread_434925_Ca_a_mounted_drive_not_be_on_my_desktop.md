---
title: "Ca a mounted drive not be on my desktop?"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-05-06
Like hidden or something?

Basically, I want my music partition mounted on boot so I can use it all the time, but I don't want it on the Desktop.  Thanks!

---

### Post by aysiu on 2007-05-06
If you're using Ubuntu, press Alt-F2, type ```
gconf-editor
``` Then go to Apps > Nautilus > Desktop > Volumes_Visible

If you're using Kubuntu or Xubuntu, let us know, and we'll give you the other instructions.

---

### Post by gohanssjn on 2007-05-06
Awesome.

Hmmm, will this only hide certain volumes or all of them?

---

### Post by aysiu on 2007-05-06
All of them.

If you want only *that* drive not to appear, mount it outside of the /media and /mnt directories.

You could mount it to /home/music, for example.

---

### Post by gohanssjn on 2007-05-06
Would you be able to tell me how to do that?  I have tried to edit fstab, unsucessfully.

---

### Post by aysiu on 2007-05-06
Can you post the output of these commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
``` Just copy and paste them into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then copy and paste the output back here.

---

### Post by raeb on 2007-05-06
[http://ubuntuforums.org/showthread.php?t=421266](http://ubuntuforums.org/showthread.php?t=421266)

A guy here made a small little python app just for that purpose.  Works perfect in fiesty, if you're on edgy get your python packages up to date.

---

### Post by apple_and _linux on 2007-10-27
> **aysiu said:**
> If you're using Ubuntu, press Alt-F2, type ```
gconf-editor
``` Then go to Apps > Nautilus > Desktop > Volumes_Visible

If you're using Kubuntu or Xubuntu, let us know, and we'll give you the other instructions.

That's so cool!  I love it when things are this easy... Just when I was missing Mac's plist editing capabilities, I'm introduced to gconf-editor.  Yay, Linux!

---

### Post by Scott-271 on 2007-11-10
I'm running Xubuntu 7.10, and having the same problem; if you could give me the *other* instructions, it'd be much appreciated.

I'd like to be able to actually take all three on my desktop and combine them into one desktop folder- "mountpoints".

Thanks, 
Scott

---

### Post by mcduck on 2007-11-10
> **aysiu said:**
> All of them.

If you want only *that* drive not to appear, mount it outside of the /media and /mnt directories.

You could mount it to /home/music, for example.
Actually drives mounted into /mnt do not appear on desktop. That's where I mount all my drives I don't want to see on Desktop..

---

