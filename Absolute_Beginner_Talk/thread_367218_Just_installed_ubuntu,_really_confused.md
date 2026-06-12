---
title: "Just installed ubuntu, really confused"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by Matt1632 on 2007-02-21
I just installed Ubuntu 6.06.:) It all went much smoother that I though a dual-boot install would.  But, what now?  I made 3 partitions 1gb swap, 10gb / and 10gb /home.  Where do I save my files?  How do I access /home?  I mounted my windows partition at the default "/media/hda1"  will this cause problems?  I'm sort of confused:confused:  I'm not sure where to save documents and access them easily.  All my partitions (execpt swap, of course.) are ext3, is this correct?

---

### Post by Veggieb0i on 2007-02-21
The linux partitions are ext3, yes.

That's all I can do to help; I'm a linux noob. :/

---

### Post by skyhopper88 on 2007-02-21
Home is more or less like a my documents folder, more like my settings folder though. I put a My Documents folder in home to use myself. Home should be under the places menu up top.

---

### Post by Luk0r on 2007-02-21
If you're using Gnome (Ubuntu, not Kubuntu), click Places at the top, then select Home Folder.  That should be /home, it's where you save your documents and stuff.  To get to your windows partition, type /media/hda1 in your address bar.

---

### Post by Maestro23 on 2007-02-21
> **Matt1632 said:**
> I just installed Ubuntu 6.06.:) It all went much smoother that I though a dual-boot install would.  But, what now?  I made 3 partitions 1gb swap, 10gb / and 10gb /home.  Where do I save my files?  How do I access /home?  I mounted my windows partition at the default "/media/hda1"  will this cause problems?  I'm sort of confused:confused:  I'm not sure where to save documents and access them easily.  All my partitions (execpt swap, of course.) are ext3, is this correct?


Welcome to the community. Couple of sites to get your feet wet:

Commands and File Structure:
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://www.tuxfiles.org/](http://www.tuxfiles.org/)

How to Install in Ubuntu: [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Restricted Formats(mp3 and DVD): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

*All your personal files (mp3, docs, pic, etc..) should go in your /home/username directory.

---

### Post by j.dub on 2007-02-21
you have made 2 different partitions, but its used as one in ubuntu. Its not like windows OS where you have a C drive and a D drive. Just save in your home folder under "Places" i think...

---

### Post by Matt1632 on 2007-02-21
okay. The icon on my desktop is /media/hd1.  Is there a way to change this to /home, because having an icon to my windows partition isn't very useful in linux.

---

### Post by Luk0r on 2007-02-21
You should be able to drag 'Home Folder' from the Places menu straight onto the desktop to make an icon.

---

### Post by letitsnow on 2007-02-21
if you save anything on the desktop it automatically goes on the home partition.

---

### Post by Matt1632 on 2007-02-21
Ok, thank you very much for the help.

---

