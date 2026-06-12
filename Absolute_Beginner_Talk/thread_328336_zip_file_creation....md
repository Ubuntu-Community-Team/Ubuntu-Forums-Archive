---
title: "zip file creation..."
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by ardvark71 on 2006-12-30
Hi everyone,

Is there a way to easily create zip archives from files residing on the desktop? 

Thanks!

---

### Post by Hossie on 2006-12-30
Use "ark". You can drag&drop your files there.

---

### Post by bigken on 2006-12-30
right click the file select create archive ;)

---

### Post by ardvark71 on 2006-12-30
> **bigken said:**
> right click the file select create archive ;)

I tried that, it just creates a tarball ;) 

Best Regards...

---

### Post by radu_chindris on 2006-12-30
or the CLI way, in a shell (terminal) type:
```

cd ~/Desktop
zip -r desktop.zip *

```
If you don't have zip installed, just ```
sudo aptitude install zip
```

---

### Post by ardvark71 on 2006-12-30
> **Hossie said:**
> Use "ark". You can drag&drop your files there.

That worked great! Thank you! :) 

Best Regards...

---

### Post by ardvark71 on 2006-12-30
> **radu_chindris said:**
> or the CLI way, in a shell (terminal) type:
```

cd ~/Desktop
zip -r desktop.zip *

```
If you don't have zip installed, just ```
sudo aptitude install zip
```

Thank you radu, Ark did it for me before I saw your post. And since this appears to be your first, allow me to bid you welcome to Ubuntu's forums and to thank you again for offering your expertise. 8) 

Best Regards...

---

### Post by Ptero-4 on 2006-12-30
ardvark71. You can select the format in the create archive dialog.

---

### Post by bigken on 2006-12-30
Here you go 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=21933&stc=1&d=1167522740[/IMG]

---

### Post by ardvark71 on 2006-12-30
Hi Bigken and Ptero...

:confused: 

For some reason I don't get a drop down for the file type, just a box telling me what file I've selected and asking me where I want it.

---

### Post by bigken on 2006-12-30
install automatix this will help you install the other zip file types

---

### Post by ardvark71 on 2006-12-30
> **bigken said:**
> install automatix this will help you install the other zip file types

I installed both Automatix and the archiving tools when I first installed Ubuntu but I wonder why Gnome doesn't let me choose the archive type? :confused:

---

### Post by Ptero-4 on 2007-01-01
Are you using Breezy? It may be that gnome 2.12 didn't have the archive format selection menu and it was added in gnome 2.14/2.16.

---

### Post by ardvark71 on 2007-01-02
> **Ptero-4 said:**
> Are you using Breezy? It may be that gnome 2.12 didn't have the archive format selection menu and it was added in gnome 2.14/2.16.

Yes I am and I'd imagine your guess is right on the money. It's ok though, Ark did the job I needed to do. Thanks for writing back. :) 

Best Regards...

---

