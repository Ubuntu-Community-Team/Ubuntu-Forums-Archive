---
title: "window manager has gone haywire"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by clinto on 2007-07-08
I've been using Ubuntu for a while now and I haven't run across this problem yet.

I'd installed Feisty on my neighbor's laptop today. After setting a couple things up and restarting it, gnome started acting funny. Every time I open an app, it integrates itself into the upper desktop panel, which makes accessing the applications buttons impossible. I'm totally at a loss.

I would post a couple screenshots, but I can't get pix.nofrag to upload them.

First, I had installed a video driver, but I don't see how that could effect it, especially since I restarted the system and had no problems. The problems arose after I'd edited my fstab and selected to have sessions saved at shutdown. I think it had something to do with the sessions. I changed it back and restarted, but it didn't do anything.

I'll tinker with it a little more and come back here later to see if anyone has any suggestions. If not, I'm just going to reinstall it. These little things are driving me insane.

---

### Post by FleetAdmiral74 on 2007-07-08
You can attach the pic directly when you post, just scroll down and go to the attachments section.

---

### Post by clinto on 2007-07-08
Ah, didn't notice that feature. Thanks.

*edit*
Oh, it's saying it's a png and has the wrong extention. They're jpg's. *sigh*

---

### Post by FleetAdmiral74 on 2007-07-09
just change the file extension to the other (png or jpeg) and try to upload again.

---

### Post by clinto on 2007-07-10
That's what I did originally. Screenshots are saved as .png's by default. I always change the extension to .jpg before saving it. However, when I look at the file in it's properties, it says it's a png.

Back on topic, I'm still unsure what happened. I gave up and tried reinstalling, leaving the /home intact. Apparently, the problem existed within /home, because the problem was there waiting for me. I reinstalled, formatting the /home and the problem went away. I have NO idea what I could have done to cause this.

I still have the pictures, but I can't figure out how to change the extension properly. The properties still say the file is a png. I've tried using gimp and saving a new file as .jpg, but doesn't work.

---

### Post by clinto on 2007-07-10
Okay, I've figured out what I was doing wrong. Here you go:

[[img]http://pix.nofrag.com/bf/77/a4508a5510f44fe781a9cdaa1412t2.jpg[/img]](http://pix.nofrag.com/bf/77/a4508a5510f44fe781a9cdaa1412.html)

[[img]http://pix.nofrag.com/52/e3/728482117bcb554624bcec2c966at2.jpg[/img]](http://pix.nofrag.com/52/e3/728482117bcb554624bcec2c966a.html)

[[img]http://pix.nofrag.com/37/76/ec96f0505f508492df3b54ac93d2t2.jpg[/img]](http://pix.nofrag.com/37/76/ec96f0505f508492df3b54ac93d2.html)

Weird.

---

### Post by Chrissie on 2007-07-10
I have the exact same symptoms. Only it's come up after I had to unistall compiz.
I'm left with one single desktop, and no window manager.
C-

---

