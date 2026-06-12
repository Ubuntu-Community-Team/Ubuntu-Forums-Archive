---
title: "help quick question"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by tim1970 on 2007-02-15
Is there some type of GUI file manager installed by default?  If not, which one is the most popular one for me to install?  Also, what are some common packages installed when ubuntu is initially installed?


Another question..  How do I access a cdrom?  I am wanting to read it from the cd drive that I used to install ubuntu.

Thanks

---

### Post by ramjet_1953 on 2007-02-15
In GNOME the default file manager is called Nautilus.
If you click on Applications>Accessories>File Browser Nautilus will open.

When you install Ubuntu, the Open Office Suite , Firefox Web Browser, Evolution email and heaps of other apps are automatically loaded. Of couse, you can then use the Synaptic Package manager to download literally hundreds and hundreds of other packages.

When you load a CDROM, Ubuntu will automatically mount it and an icon will pop-up on the screen. Depending upon how you have configured Ubuntu, it will either act upon it or not.
ie if it is a music CD and you configured Ubuntu to automatically play music CD's it will play.

Regards,
Roger :cool:

---

### Post by tim1970 on 2007-02-15
If you click on Applications>Accessories>File Browser Nautilus will open.

I do not have a File Browser option under Applications>Accessories.  I went to a terminal window and entered sudo aptitude update and then sudo aptitude install nautilus.  After a few moments the message was 

"0 packages upgraded, 0 newly installed, 0 to remove and 131 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
"

So I am not sure what I need to do now.


Also I was attempting to read a CD that had some JPG files on it.  Since this came from a Windows machine, I assume that is why the CD can not be read??  If that is the case, how can I get some .jpg files from my windows machine to my linux machine?  (Totally separate boxes)

Tim

---

### Post by ramjet_1953 on 2007-02-15
OK, in a terminal type [COLOR="Red"]nautilus[/COLOR] and it should open.

If you want to open nautilus with Administrator Privileges type [COLOR="Red"]gksu nautilus[/COLOR]

Regards,
Roger 8-)

---

### Post by Spike-X on 2007-02-15
> **tim1970 said:**
> 

Also I was attempting to read a CD that had some JPG files on it.  Since this came from a Windows machine, I assume that is why the CD can not be read??  

I just popped in a CD of .jpg files I had sitting around (don't ask, don't tell!) that I burned under Windows, and I was able to read the disc and browse the images just fine. Maybe the disc is faulty in some fashion? How old is it? When did you last try to read it in Windows?

---

### Post by Royel on 2007-02-15
If File Browser is not listed under "> Applications > Accesories" Do the following:
Click: > Applications>Accesories>Alacart Menu Editor, place a check in the "File Manager" box an voila!

Also, if you click on ">Places>Home(folder)" this will open the File Manager as well. In fact many of these options under "Places" will use the File Manager.

---

### Post by igknighted on 2007-02-15
Forget alacarte, file browser is under applications -> system tools.

as for the cd, in the file browser go to the /media folder, there should be a cd icon there for you to browse.

---

### Post by MrKlean on 2007-02-15
I like GNOME Commander...it has 2 panes so you can move files between folders more easily ; )  Just my 2 cents ; )

---

