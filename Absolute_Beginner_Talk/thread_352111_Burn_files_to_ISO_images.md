---
title: "Burn files to ISO images"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by jms1989 on 2007-02-02
OK, I have a small problem. I have some files in seperate directories that I would like to burn to a audio cd, but here's the catch, I want to burn it to a iso image. In windows, I would use Nero to burn the files. In Ubuntu, I haven't found a app that would do it. K3b wouldn't allow me to add mp3s to a audo cd project, although I use it for my cd burning needs.

Is there a graphical app that would allow me to do it. There is Nero linux, but it cost $20.00 USD. Money I don't have, I am all about open source software. They have a demo version, but I don't like demos. Either be free and I'll use it or require money and you can just forget it. 

The software app I'm searching for must be open source and has a graphical interface.

Please help.

A friend in need,
jms1989

---

### Post by K.Mandla on 2007-02-02
Would Gnomebaker work for you? If you don't want something Gnome-based, I use Graveman and it does data CDs, and I believe writing to an ISO is an option. Check for Graveman in your Add/Remove Programs or in Synaptic.

---

### Post by jms1989 on 2007-02-02
I tested the two but I didn't see an option to burn to an ISO image. Is there something I overlooked?

---

### Post by K.Mandla on 2007-02-02
I think it's under CD-to-CD copy in Graveman. Or something like that. "Other operations" maybe? I can picture the two CDs with a plus sign between them ... :-k (I'm at work now.)

I think Gnomebaker has a click-button to save to ISO instead of burning it. I'm not as familiar with that one, though.

---

### Post by meng on 2007-02-02
Plain Nautilus CD-burner has this, after you press Write to Disc ... choose the "device" to write to as "File image".

---

### Post by Marsolin on 2007-02-03
[K3b]("http://linuxappfinder.com/package/k3b") will work, you just need to make sure that the libk3b2-mp3 package is installed first. It's in the universe section of the repositories.

---

### Post by jms1989 on 2007-02-03
@ K.Mandla --- Ok, I started with graveman and it does have a CD to CD feature with support to burn to a ISO, but I need to burn mp3 to a ISO in a audio cd format.

In gnomebaker, I didn't see a click-button to burn to ISO. Can you perhaps post a screenshot of what it should look like?

@ meng ---- The nautilus cd burner seems to only do data disks. Thanks anyway, sorry.

@ Marsolin --- I install the plugin for k3b and it now lets me add mp3s but it doesn't ask where to save a iso file. It just decodes the files when I use the "Create Image File Only" or some sort.

I am appreciating the help, but I haven't found something to complete the task.

---

### Post by moffa on 2007-02-03
In Gnomebaker:
- Select your project type (Audio CD) 
- Drag and drop your files to the bottom half of the screen
- Click Burn (bottom right corner of the screen)
- Under Options, Select "Only Create Image"
- Specify your path for the iso file and select Start

Hope that explains it for you

---

### Post by jms1989 on 2007-02-03
> **moffa said:**
> In Gnomebaker:
- Select your project type (Audio CD) 
- Drag and drop your files to the bottom half of the screen
- Click Burn (bottom right corner of the screen)
- Under Options, Select "Only Create Image"
- Specify your path for the iso file and select Start

Hope that explains it for you


I gave that a shot and the attached file will show you what I have to work with. It's from gnomebaker.

---

