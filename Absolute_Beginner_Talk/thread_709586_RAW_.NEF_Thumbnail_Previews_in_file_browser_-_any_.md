---
title: "RAW .NEF Thumbnail Previews in file browser - any plugins?"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by PiggiePaul on 2008-02-27
I have a Nikon Digital SLR and take all my photo's in RAW format generally.

They end up with a "Photo.NEF" filename.

Now, I can open .NEF files for viewing and editing with various programs, but is there a plug-in or something that lets you see small thumbnails of RAW .NEF files when just browsing folders, like you get when you browse through .JPG and .GIF files?

Thanks.

---

### Post by Roanoke on 2008-03-04
I'd also like to know.

---

### Post by PiggiePaul on 2008-03-04
> **Roanoke said:**
> I'd also like to know.

Ahhh, shame. I thought you might have posted the answer :(

Perhaps someone knows.

There are a few progs that can read these files, so there must (hopefully) be something to add into Nautilus/Gnome? that can give us the thumbnail previews?

---

### Post by ekendra on 2008-03-10
yeah. this is a big hassle for me too. I can't see the thumbnails when i go to open an image via an application. I have to browse via Nautilus, remember the filename and then open it n GIMP.

seems like its a pretty basic thing that I'm surprised has been overlooked.

---

### Post by mortalfunk on 2008-03-10
I managed to find out the solution to this problem.

Installing the package **gnome-raw-thumbnailer** has solve the problem for me.

```
sudo apt-get install gnome-raw-thumbnailer
```

---

### Post by Amon_Re on 2008-03-10
> **PiggiePaul said:**
> I have a Nikon Digital SLR and take all my photo's in RAW format generally.

They end up with a "Photo.NEF" filename.

Now, I can open .NEF files for viewing and editing with various programs, but is there a plug-in or something that lets you see small thumbnails of RAW .NEF files when just browsing folders, like you get when you browse through .JPG and .GIF files?

Thanks.

I just got me a Nikon D40 last friday, and i noticed that GIMP doesn't seem to read these RAW pictures, what applications do you use?

---

### Post by minio on 2008-03-15
try installing "gimp-dcraw" - it should allow GIMP to open RAW files

---

### Post by Steve Angelidis on 2008-03-15
Two other options:

 UFRaw at

[http://ufraw.sourceforge.net/Install.html]("http://ufraw.sourceforge.net/Install.html")

Picasa. I haven't tried it yet with the Linux version, but my Windows version of Picasa allowed me to view and edit (crudely) NEF files.

---

### Post by Jamie Jackson on 2008-07-05
> **mortalfunk said:**
> I managed to find out the solution to this problem.

Installing the package **gnome-raw-thumbnailer** has solve the problem for me.

```
sudo apt-get install gnome-raw-thumbnailer
```

It didn't fix it for me. After installing it, is there something else I need to do to enable/configure it?

---

