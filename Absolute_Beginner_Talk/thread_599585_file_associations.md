---
title: "file associations"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by lattmau on 2007-11-01
In Ubuntu, is there something that manages file associations?  Such as I want to specify Program A to open file type X instead of Program B.

---

### Post by Maestro23 on 2007-11-01
> **lattmau said:**
> In Ubuntu, is there something that manages file associations?  Such as I want to specify Program A to open file type X instead of Program B.

In Gnome:

Apps>>Other>>File Assoc.

---

### Post by Inxsible on 2007-11-01
> **lattmau said:**
> In Ubuntu, is there something that manages file associations?  Such as I want to specify Program A to open file type X instead of Program B.
Right click file of type X. Select Properties. Navigate to 'Open With' tab and select the application that you want to open it with.

If your desired application is not in the list, click browse and find it under /usr/bin

---

### Post by erginemr on 2007-11-01
> **Maestro23 said:**
> In Gnome:

Apps>>Other>>File Assoc.

Are you sure that there is such a setting? I cannot find it in the Gnome menu.

I also need sometimes to change the file associations, but can only do it via right-clicking a file type -> Properties -> Open with...

---

### Post by Inxsible on 2007-11-01
> **erginemr said:**
> Are you sure that there is such a setting? I cannot find it in the Gnome menu.

I also need sometimes to change the file associations, but can only do it via right-clicking a file type -> Properties -> Open with...
I think that's in kde. If you have installed a couple of kde apps, the Apps-Other-Open With comes up.

You might have to edit the main menu for it to show. But I don't think it would work because it would be kde specific.

Maestro, has it worked for you (provided you use Gnome)? If yes, then it could be yet another way :)

---

### Post by Maestro23 on 2007-11-01
> **erginemr said:**
> Are you sure that there is such a setting? I cannot find it in the Gnome menu.

I also need sometimes to change the file associations, but can only do it via right-clicking a file type -> Properties -> Open with...

Sorry, its a KDE app.  I have it because I have some KDE stuff installed.

---

### Post by Inxsible on 2007-11-01
> **Maestro23 said:**
> Sorry, its a KDE app.  I have it because I have some KDE stuff installed.
Yes, but does it work when you use it to change file associations ?

---

### Post by lattmau on 2007-11-01
can someone clarify this for me?

if i have Ubuntu, can i use and install KDE apps? because isnt amarok a kde app as well? (i installed it yesterday and it worked, so i was confused)

---

### Post by Inxsible on 2007-11-01
> **lattmau said:**
> can someone clarify this for me?

if i have Ubuntu, can i use and install KDE apps? because isnt amarok a kde app as well? (i installed it yesterday and it worked, so i was confused)
Yes KDE apps will work in Gnome and vice versa
xfce apps will work in either too.

---

### Post by lattmau on 2007-11-01
are there any disadvantages to using KDE apps on Gnome?  

if not, why is there a need to specify whether something is KDE or not if its pretty much interchangeable between the two?

---

### Post by Can+~ on 2007-11-01
I really never looked for that, I don't know if there is any graphical app to do this, but you can edit this file:

Alt+F2
> gksudo gedit /usr/share/applications/defaults.list

---

### Post by Inxsible on 2007-11-01
> **lattmau said:**
> are there any disadvantages to using KDE apps on Gnome?  

if not, why is there a need to specify whether something is KDE or not if its pretty much interchangeable between the two?
disadvantage : when you load the VERY FIRST kde app, it might be a bit slow in Gnome because it has to load the relevant KDE packages. the next kde app will load equally fast since the kde packages are already loaded.

The need to specify is just so that someone knows. No biggie.

---

### Post by stchman on 2007-11-01
Yes, KDE needs different libraries than Gnome apps.  Gnome uses GTK libraries while KDE uses QT libraries.  Someone correct me if I am wrong.  The solution is to load kdeinit at startup.  Follow my procedure below.

[http://www.stchman.com/kde_fast.html](http://www.stchman.com/kde_fast.html)

---

### Post by erginemr on 2007-11-01
Quote:
Originally Posted by Maestro23 View Post
Sorry, its a KDE app. I have it because I have some KDE stuff installed.
Yes, but does it work when you use it to change file associations ?

> **Inxsible said:**
> Yes, but does it work when you use it to change file associations ?

I would ask just the same. But probably, it is KDE or konqueror specific. Any news?

---

### Post by Maestro23 on 2007-11-01
> **erginemr said:**
> Quote:
Originally Posted by Maestro23 View Post
Sorry, its a KDE app. I have it because I have some KDE stuff installed.
**Yes, but does it work when you use it to change file associations ?**



I would ask just the same. But probably, it is KDE or konqueror specific. Any news?

Yes it does.

---

### Post by erginemr on 2007-11-01
> **Inxsible said:**
> Yes, but does it work when you use it to change file associations ?

> **Can+~ said:**
> I really never looked for that, I don't know if there is any graphical app to do this, but you can edit this file:

Alt+F2

Thank you very much. I was asking myself for sometime where the heck these settings could be located. Not that the file is easy to edit at all (pretty cryptic, that is), though still good to know where these settings are kept.

---

### Post by Inxsible on 2007-11-01
> **Maestro23 said:**
> Yes it does.

Cool !! I wouldn't have thought it would, but its nice to know it does :)

Yet another way of doing things in Gnome even though you have to install KDE apps ;)

---

### Post by erginemr on 2007-11-01
> **Maestro23 said:**
> Yes it does.

thanks a lot.

---

### Post by erginemr on 2007-11-01
I have some bad news. It turns out that "/usr/share/applications/defaults.list" is actually a symbolic link to "/etc/gnome/defaults.list"!

Probably kde's default app. switcher will not look into a gnome folder, and therefore will have no effect.:confused:

---

### Post by lattmau on 2007-11-01
i'm lost. haha.

---

### Post by erginemr on 2007-11-01
> **lattmau said:**
> In Ubuntu, is there something that manages file associations?  Such as I want to specify Program A to open file type X instead of Program B.

> **lattmau said:**
> i'm lost. haha.

OK. Forget about what we said so far. Maybe we strayed a bit off-topic in our recent talks...

Say, you want to open avi files with VLC instead of the default Totem. Simply put, you can do this practically by right clicking any avi file, select "properties", then open the "open with" tab, press the button with a plus sign on it, select the program from the list, and click OK. now you should have two programs (Totem & VLC) in the program selection window. Whichever you select by the radio button beside them, will the the default application for avi files.

You can do pretty much the same for other file types.

---

### Post by lattmau on 2007-11-01
thanks.

could you also explain  your previous post?  i would like to understand

---

### Post by erginemr on 2007-11-01
> **erginemr said:**
> I have some bad news. It turns out that "/usr/share/applications/defaults.list" is actually a symbolic link to "/etc/gnome/defaults.list"!

Probably kde's default app. switcher will not look into a gnome folder, and therefore will have no effect.:confused:

Nothing über-geek really. Can+~ has stated in his/her post that there is a file somewhere in our computer:
"/usr/share/applications/defaults.list"
that keeps the list of default applications for each major file type.

which we can edit by issuing:
"gksudo gedit /usr/share/applications/defaults.list"
from the console. 

I have opened Nautilus (Gnome's file manager), found this file, but the arrow sign on its icon told me that is is actually a link (shortcut) to another file. I have right-clicked it and checked its properties to see that the real file is
/etc/gnome/defaults.list

So, the actual file is under the /etc folder in our folder tree, and then under /gnome folder, which led me to believe that a KDE app (that Maestro23 was using) normally should not care with a file under gnome's directory.

But then again, I was wrong, because it was probably the file;
/usr/share/applications/defaults.list (the shortcut)

that the KDE config(uration) applet (program) was seeing and dealing with. So, chances are that; contrary to what I was thinking before, tinkering with the KDE applet should do the trick and have the same effect. Probably, a KDE distro is normally dealing with the same shortcut (the real file being probably under a kde folder this time).

That is all there to it. But really, these are just brainteasers. The method I have described above is simple and effective. (I have changed the default applications of a few of my file types this way.) We don't have to bother with that file and what it does.

Take Care...

---

### Post by Versusnja on 2008-03-06
Right click on file -> Properties -> open with

Works as a charm. Thank you!

---

### Post by stchman on 2008-03-06
> **lattmau said:**
> can someone clarify this for me?

if i have Ubuntu, can i use and install KDE apps? because isnt amarok a kde app as well? (i installed it yesterday and it worked, so i was confused)

If you are using Gnome then just do what poster #3 said.  It is very easy.

---

