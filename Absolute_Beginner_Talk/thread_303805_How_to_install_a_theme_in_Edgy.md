---
title: "How to install a theme in Edgy?"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by habtish on 2006-11-20
I have downloaded some themes from gnome-look.org and am stuck right there.I have looked at most of the "how to install a theme threads in this forum and most have been left hanging without a definite answer For example, for a speficific theme, I extracted the .tar.gz into a folder

```
tar -vxf themename.tar.gz
```

I then try to add this by clicking on Install themes, the folder opens up to show files like GTK, GTK2.0, Metacity and opening these folders gives some .png files and an .xml file. doubleclicking on either of these gives the error <the file format is invalid>
Pardon my ignorance, what file extension do theme files have? (.png, .xml, .theme? ) I even tried dragging and droping the whole folder containing the extracted "theme" files into the theme manager only to get the same error.

What am I doing wrong here? I am sure this is a simple problem for lots out there and hope not too simple and silly to reply to.

Thanks for the help...

---

### Post by aysiu on 2006-11-20
Don't extract the .tar.gz

Just drag and drop the .tar.gz to the theme manager window (System > Preferences > Themes)

---

### Post by CatKiller on 2006-11-20
You should be able to drag-and-drop the tar.gz file onto the Theme Manager window. No need to extract. If you use art.gnome.org, you don't even have to download it yourself - just drag-and-drop the link.

You can also extract the files into ~/.themes.

EDIT: beaten to the punch

---

### Post by habtish on 2006-11-20
Thanks for the prompt replies guys, I appreciate you both. First of 4 threads (on different issues) I got a reply on. Thank You

---

### Post by freshmaker on 2006-11-20
> **aysiu said:**
> Don't extract the .tar.gz

Just drag and drop the .tar.gz to the theme manager window (System > Preferences > Themes)

by doing this I cannot achieve the same effect shown in the pictures 
for example in this case [http://www.gnome-look.org/content/show.php?content=30972](http://www.gnome-look.org/content/show.php?content=30972)
or here [http://www.gnome-look.org/content/show.php?content=30859](http://www.gnome-look.org/content/show.php?content=30859)

everything is fine but I do not have the same scrollbars and even the same buttons
Do you have any idea what I do wrong???

---

### Post by CatKiller on 2006-11-20
It's often considered impolite to hijack another thread.

> **freshmaker said:**
> by doing this I cannot achieve the same effect shown in the pictures 
for example in this case [http://www.gnome-look.org/content/show.php?content=30972](http://www.gnome-look.org/content/show.php?content=30972)
or here [http://www.gnome-look.org/content/show.php?content=30859](http://www.gnome-look.org/content/show.php?content=30859)

everything is fine but I do not have the same scrollbars and even the same buttons
Do you have any idea what I do wrong???

Have you installed the Clearlooks engine that it says is required. I don't know much about such things, but a ```
sudo aptitude install gtk2-engines-clearlooks
``` might help.

---

### Post by gunksta on 2006-11-20
Actually you will need to install the pixbuf engine.

```
sudo aptitude install gtk2-engines-pixbuf
```

This will make some of the themes have the cute OSX-like slide-bars. However, not all of the themes do this.

--andy

---

### Post by freshmaker on 2006-11-21
> **CatKiller said:**
> It's often considered impolite to hijack another thread.


I am really sorry if I did insult anybody. I did not mean to be impolite or especially a hijacker. I thought will be easier than posting my own thread. You know how many threads on the same problem are there, but anyways... thanks for your help I have got clearlooks installed :-k 

@gunksta

```
sudo aptitude install gtk2-engines-pixbuf
```
I will try this later thanks :)

---

### Post by Perfect Storm on 2006-11-21
Read more about eyecandy and stuff: [http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694)

---

### Post by freshmaker on 2006-11-21
> **Artificial Intelligence said:**
> Read more about eyecandy and stuff: [http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694)

Thanks AI I read your HOWTO and thik it is great but I still have one question. How to get rid of the default recycle bin icon (I did what you propose about this
```
sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
sudo ln -s /home/<insert your username here>/.fonts /root/.fonts

```but it did not work for this ICON )
see what I mean here [http://img156.imageshack.us/my.php?image=screenshotvm9.jpg](http://img156.imageshack.us/my.php?image=screenshotvm9.jpg)
Thanks in advance,

freshmaker

---

### Post by Perfect Storm on 2006-11-21
You use edgy right? In edgy the trash can icon path is broke.

---

### Post by freshmaker on 2006-11-21
Yes! I am with Edgy.

> **Artificial Intelligence said:**
> In edgy the trash can icon path is broke.

Which means...
Sorry for not understanding this ](*,)

---

### Post by Perfect Storm on 2006-11-21
That alot of icon themes have the icon trash rolled back to gnome default.

---

### Post by CatKiller on 2006-11-21
> **Artificial Intelligence said:**
> That alot of icon themes have the icon trash rolled back to gnome default.

If, for the theme you want, you create a link to the icons you want called **user-trash** and **user-trash-full** (I think - I'm not at an Edgy machine at the moment) you'll get your bin icon working again. I'm not sure of the reason for the change with the Edgy version of Gnome, since I've not looked into it much, but it does seem to be the case.

---

### Post by freshmaker on 2006-11-22
Thanks AI !!!
Thanks CatKiller !!!
I kind of managed to do it... have some little adjustments left but I have got the main Idea

Thaks again....and my apologies to habtish for stealing his/her thread.

freshmaker

---

### Post by CatKiller on 2006-11-22
> **freshmaker said:**
> I kind of managed to do it... have some little adjustments left but I have got the main Idea

Thaks again....and my apologies to habtish for stealing his/her thread.

Glad to help.

Hijacking the thread is only really a problem, as I understand it, if the OP doesn't get their problem fixed - which I don't **think** was the case here. And if the problem is different enough that it probably ought to be in a new thread to get different eyes looking at it, which is why I mentioned it.

---

### Post by habtish on 2006-11-22
> **freshmaker said:**
> 
....and my apologies to habtish for stealing his/her thread.
freshmaker

It really is not a problem for me. I had my question answered, wouldn't bother me if someone appends to the discussion and gets help, so long as we achieve what we come here for

---

### Post by MarkNZ on 2006-11-28
I had this same issue when trying to use the Theme option in Preferences.

Try this instead:

```
sudo gdmsetup
```

Try install from there, worked for me!

---

