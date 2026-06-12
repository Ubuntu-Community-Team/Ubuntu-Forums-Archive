---
title: "File associations lost?"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by XFocus on 2008-03-19
Recently all of my file associations seem to have gone nuts.  

What I mean is that whenever I click on an image, for example, I get the following error:
```
"IMG_0511.png" cannot be opepend.
No application is known for this kind of file.
```

I can go into the properties of the file and select "Open with" and specify the image viewer and that works for opening the file, however, if I were to try and set the icon for a drive/directory then the nautilus window won't recognize any of the pngs I have.  Nothing will show up within a folder full of pngs.  Also, the "Supported image types" drop down is empty.  I'm assuming it should show the different file types that it's looking for.

The same issue is happening with other extensions.  .tar.bz2, .rar, etc.

Is there a quick way to reassociate all of the file extensions?

Any help is appreciated!

---

### Post by wormser on 2008-03-20
Go to properties then the Opens With _TAB_.  Then all the files of that type will be associated with that application.

---

### Post by XFocus on 2008-03-20
Right, I can do that and the file will open with the application fine, however, doing things such as trying to set an icon for a particular drive won't work.  When I right click on the folder/drive and try and set a custom icon, the nautilus window will show an empty folder when I KNOW that it is full of png's.  

Also, trying to set custom wav files for the system sounds results in errors.

```

The file /usr/share/sounds/Intro.wav is not a valid wav file.
```

Any ideas?

---

### Post by XFocus on 2008-03-23
After some more research I've run across some people with similar problems and I'm thinking that I need to possibly rebuild the Mime database?

Here are some posts with similar problems:
[http://ubuntuforums.org/showthread.php?t=534288](http://ubuntuforums.org/showthread.php?t=534288)
[http://ubuntuforums.org/showthread.php?t=434254](http://ubuntuforums.org/showthread.php?t=434254)

Can anybody guide me through how to rebuild the MIME database?  

Thanks!

EDIT:  **I SOLVED IT!**
Here's a link to the fix:
[https://bugs.launchpad.net/nautilus/+bug/19101/comments/41](https://bugs.launchpad.net/nautilus/+bug/19101/comments/41)

And here's a copy of the freedesktop.org.xml file if you need it:
[http://webcvs.freedesktop.org/mime/shared-mime-info/freedesktop.org.xml.in?view=markup](http://webcvs.freedesktop.org/mime/shared-mime-info/freedesktop.org.xml.in?view=markup)

---

