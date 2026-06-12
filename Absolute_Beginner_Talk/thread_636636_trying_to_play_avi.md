---
title: "trying to play avi"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by james1030 on 2007-12-10
hey guys. i am trying to play an avi from disk on totum, but when i put the disk in the drive totum says "Unable to activate plugin Media Player Keys". i dont know what do do, any help?
thanks a bunch

---

### Post by Kingsley on 2007-12-10
You probably need to install ubuntu-restricted-extras.

---

### Post by vikramsharma on 2007-12-10
> **james1030 said:**
> hey guys. i am trying to play an avi from disk on totum, but when i put the disk in the drive totum says "Unable to activate plugin Media Player Keys". i dont know what do do, any help?
thanks a bunch

Just install totem-xine via Synaptic Package Manager or though apt-get install.  It's recommended that you enable the repositories mentioned in the Synaptic Package Manager.  You can also install VLC Media Player that plays almost all available media formats.

---

### Post by james1030 on 2007-12-11
VLC player works good. thx

---

### Post by stchman on 2007-12-11
> **james1030 said:**
> hey guys. i am trying to play an avi from disk on totum, but when i put the disk in the drive totum says "Unable to activate plugin Media Player Keys". i dont know what do do, any help?
thanks a bunch

You need the proper plugins:

```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

---

