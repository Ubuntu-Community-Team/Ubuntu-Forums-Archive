---
title: "Webcam/TV card help"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by DiscoKiller on 2006-03-15
hi all, i have recently re installed a tv card under ubuntu ad now when i start applications like camorama and camstream to grab images from my webcam ufortunately the programs grab from the default device /dev/video0 which is my tv card and ot my webcam which i think is /dev/video1. is there a way i can swap these two devices around to allow the programs to view my webcam?

thanks 

DK

---

### Post by flip on 2006-03-15
I don't believe you can change the file names for devices (but I've been wrong before). There is however a way to tell camorama which device to capture from.

Camorama's kinda strange like that. I couldn't find a way to change the video device it uses in any of the gui config / preferences dialogs. It turns out you can specify which device you want it to use on the command line like so

```

camorama -d /dev/videoX

```

A really bad, quick fix is to create a launcher on your desktop ... right click on the desktop and choose 'create launcher ...'. 
In the 'Name:' field put whatever you want. The important one is 'Command:' here you put the command from above, make sure you put the right video device after the -d. Click on 'Ok' and it should work when you double click on the launcher.

Ideally you would change the command executed by the camorama launcher in the Applications->Graphics tab in the panel Applications launcher ... but I have no idea how to do that. But since this is more fun to figure out than my homework ... I'll post when I get it :-D

Cheers!

---

### Post by flip on 2006-03-15
Ok that was easier than I thought it would be, I should have known this one  ::blushing ::

Right click on the 'Applications' menu on the gnome panel and select 'Edit Menus'.
In the window that pops up select 'graphics' in the left pane and then right click on 'Camorama Webcam Viewer' in the right pane. Select 'Properties' from the drop down menu and then edit the 'Command:' text field as described above.

Should work!

---

### Post by DiscoKiller on 2006-03-15
I would like to extend a large virtual hug.....thank you, it worked a treat, if u need help with your homework let me know hehe :D

---

