---
title: "[SOLVED] Is there more than 1 recycle bin?"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by PiggiePaul on 2008-02-27
Just wondering...........

Something was said in one of my other posts:
[COLOR="Blue"]
be aware that it'll get deleted into root's trash - so it won't appear in yours[/COLOR]

and also I just removed a album from digiKAM and I think it said it was not going to delete the files (but they seems to have vanished somewhere!)

My "normal" recycle bin is empty.

So, is there another one, and how do I access/see it (if there is?)

Thanks.

---

### Post by aysiu on 2008-02-27
If you run a file manager as root and then delete a file, it will go to /root/.Trash

If you run a file manager as user and then delete a file, it will go to /home/*user*/.Trash

---

### Post by PiggiePaul on 2008-02-27
> **aysiu said:**
> If you run a file manager as root and then delete a file, it will go to /root/.Trash

If you run a file manager as user and then delete a file, it will go to /home/*user*/.Trash

thanks for the info.

Ok, next question (you could see this one coming!)

How do I view (and possibly) empty root trash?

Command to become root?

---

### Post by Charcoal1981 on 2008-02-27
A '.Trash' folder is also setup on any usb sticks, phones, cameras etc. that you connect. I think when you unmount these devices, there is an option to empty the respective '.Trash' folders, else you can do it manually, but you will need to go "view>show hidden files" in nautilus in order to see the trash folder for these devices.

---

### Post by Locutus_of_Borg on 2008-02-27
sudo nautilus /root/.Trash should bring you to root's trash with root access, i believe

---

### Post by aysiu on 2008-02-27
> **Locutus_of_Borg said:**
> sudo nautilus /root/.Trash should bring you to root's trash with root access, i believe
Alt-F2 ```
gksudo nautilus
``` is the way to do it. Then press Control-L and type ```
/root/.Trash
``` capitalization on that T in *Trash* is important.

---

### Post by Charcoal1981 on 2008-02-27
you can view root's files by
```
gksudo nautilus
```
And navigating to the appropriate place

edit: apologies to aysiu - double post

---

### Post by warbird on 2008-02-27
```
alt+F2
gksu nautilus
```

enter password, and empty the trash! :)

edit: hmm... i was a bit slow :p

---

### Post by PiggiePaul on 2008-02-27
Thanks for all the postings.

I'll have to write that one down so I don't have to ask again ;)

Well, my root trash is empty, so dunno where those files went?

apart from the other comment in my 1st post in [COLOR="Blue"]blue[/COLOR] which does not really matter.

I was in digiCam (the photo software) and I right clicked on a folder, and selected [COLOR="Blue"]"Move to Trash"[/COLOR]

I deliberately did not tick the box that comes up saying delete files.

So, the folder, went (to trash I guess) but it's not in any trash bin.

Odd?

---

### Post by aysiu on 2008-02-27
You can try entering this in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo updatedb && locate *nameoffile*
``` to find out where it went to. Sometimes programs will create their own weird trash cans (don't ask me why).

---

### Post by PiggiePaul on 2008-02-27
> **aysiu said:**
> You can try entering this in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo updatedb && locate *nameoffile*
``` to find out where it went to. Sometimes programs will create their own weird trash cans (don't ask me why).

Thank's

Found the sucker !!!!

[COLOR="Blue"]/home/USERNAME/.local/share/Trash/files/[/COLOR]

Why do things have to be so complicated :confused:

---

### Post by aysiu on 2008-02-27
> **PiggiePaul said:**
> Thank's

Found the sucker !!!!

[COLOR="Blue"]/home/USERNAME/.local/share/Trash/files/[/COLOR]

Why do things have to be so complicated :confused:
I don't know. Any chance you're using Xubuntu and not Ubuntu? Or maybe since DigiKam is a KDE application, it plops the file into the KDE trash instead of the Gnome trash.

---

### Post by PiggiePaul on 2008-02-27
> **aysiu said:**
> I don't know. Any chance you're using Xubuntu and not Ubuntu? Or maybe since DigiKam is a KDE application, it plops the file into the KDE trash instead of the Gnome trash.

No, not using Xubuntu, so I guess your 2nd idea could well be right.

As long as I know, I'll just have to make a note for the future.

Again, thanks for helping me find it. :)

---

