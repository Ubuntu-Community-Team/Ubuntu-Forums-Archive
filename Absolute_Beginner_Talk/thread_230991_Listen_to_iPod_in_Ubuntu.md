---
title: "Listen to iPod in Ubuntu"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by Gonzo_PhD on 2006-08-06
How do I listen to my ipod in Ubuntu? I see it pop up on the desktop. Is there another application I'm supposed to use to view it like in iTunes?

Thanks

---

### Post by PingunZ on 2006-08-06
By using the " search " function on this forum ;)

---

### Post by Gonzo_PhD on 2006-08-06
Sorry... :-(

---

### Post by catlett on 2006-08-06
You want to use gtkpod. Go to System<Adminisrtation<Synaptic Package Manager and search for gtkpod. Here is the synaptic description
> manage songs and playlists on an Apple iPod
gtkpod is a platform independent GUI for Apple's iPod using GTK2. It
allows you to upload songs and playlists to your iPod. It supports ID3
tag editing, multiple charsets for ID3 tags, detects duplicate songs,
allows offline modification of the database with later synchronisation,
and more.You will also need mp3 support. This will give you mp3 and ogg support
```
sudo apt-get install mpg321 vorbis-tools
```

---

