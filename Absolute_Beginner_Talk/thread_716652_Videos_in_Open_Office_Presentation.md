---
title: "Videos in Open Office Presentation?"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by marenkar on 2008-03-06
How do I put videos (.avi) into my open office presentation. Btw, will the open office presentation work on microsoft powerpoint?

---

### Post by marufaberlin on 2008-03-06
Sure will. But there could be some compatibility problems. You just have to save as a ppt file. You go on Insert -> Viedeo and Sound and that insterts the .avi video.

---

### Post by marenkar on 2008-03-12
Uhh there no insert--> video  or sound in the insert tab.

---

### Post by Sef on 2008-03-12
> Uhh there no insert--> video or sound in the insert tab.

In Presentation, insert is between view and format, while movie and sound is between picture and object on the tab.  If you are missing something, then it seems that Presentation was not installed correctly.

---

### Post by marenkar on 2008-03-13
Yep it aint there. P.S i'm using 6.06 LTS, where can I get the open office presentation that can have videos?

---

### Post by marufaberlin on 2008-04-10
You should first do a dist upgrade. Maybe that fixes your problem:

```

sudo apt-get update
sudo apt-get dist-upgrade

```

You should have your online sources available for that:
```

sudo software-properties-gtk

```

Otherwise, remove openoffice using apt-get remove and reinstall using apt-get install or just use sudo synaptic.

Hope this helps.

---

