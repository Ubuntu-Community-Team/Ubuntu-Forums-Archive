---
title: "Creating Desktop Shortcuts to my Mounted Drives"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by robinlennox on 2007-03-10
Just wondering how you create shortcuts on my desktop to folders and files...

In Windows it's a case of a right click send to desktop....

With Ubuntu, i'm finding it a bit more diffcult...

Sorry to be a pain!

Regards

Robin

---

### Post by STREETURCHINE on 2007-03-10
sorry missread your post,

---

### Post by raja on 2007-03-10
Look at [http://www.ubuntuforums.org/showthread.php?t=370016](http://www.ubuntuforums.org/showthread.php?t=370016)

---

### Post by Patrick K on 2007-03-10
> **raja said:**
> Look at [http://www.ubuntuforums.org/showthread.php?t=370016](http://www.ubuntuforums.org/showthread.php?t=370016)

Post 7 is the one you want.

---

### Post by robinlennox on 2007-03-10
Cheers for the information

---

### Post by robinlennox on 2007-03-10
Thats kind of what i'm looking for... but how do I add my own icons.

Like a Mounted Drive?

---

### Post by Patrick K on 2007-03-10
I don't have the icons on my desktop anymore but you can probably right click on them then click on the icon in the upper left corner. This should open the icon selection window. If you want to use your own icons, you may have to browse to the dir with your icons.

---

### Post by robinlennox on 2007-03-10
There is no option even when the icons are on the desktop.

Seems to me that the directions simply refer to adding defaults icons. I would like to add custom icons.

---

### Post by rsambuca on 2007-03-10
If you right click on the desktop icon, then select "Properties" at the bottom.  You can then click on the icon picture and change it to whatever you want.  If you look at this screenshot, I have changed some of my icons to things I made.

---

### Post by robinlennox on 2007-03-10
OK,

I can't see the desktop icon... I am running the server version of Ubuntu 6.06 with Gnome.

Maybe I haven't installed something...

---

### Post by rsambuca on 2007-03-10
Exactly what icons do you want on your desktop?

---

### Post by robinlennox on 2007-03-11
> **rsambuca said:**
> Exactly what icons do you want on your desktop?

I have computer, home and trash which I had to add manually using Alt-F2, gconf-editor, then I had to go to apps, nautilus, desktop, then checked:

computer_icon_visable
home_icon_visable
trash_icon_visable

Nothing else is on there apart from the menu bars and the wallpaper

---

### Post by rsambuca on 2007-03-11
Ahh, OK.  Those icons are stock icons and are set for each particular theme you are using.  If you want to change those ones, you will have to go to /usr/share/icons/"name of the theme you are using".  Once you see the set you are using, change the name of the icon you want to change to home_backup, or whatever, and replace the original with the icon of your choice.  

Any other icon you place on the desktop you can customize with a simple right-click, except for those ones that you activate from the gconf-editor.  Quite a pain, I must say.

---

### Post by robinlennox on 2007-03-11
I seem to be getting somewhere now!

Thanks for you patients rsambuca.

I don't want to edit the theme icons... It was suggest in this post that what i needed to do!

But obviously that was just to enable theme icons. :(

Now the right click option seems to be what i'm after, so if I change theme the shortcuts will stay.

Now if I right click on my desktop i get the following options:

Create Folder
Create Launch
Create Document

Now I want to create a shortcut to my mount hda7 located at \mnt\hda7....

Any Ideas how I would do this?

---

### Post by rsambuca on 2007-03-11
If you just open your file browser (nautilus), I think you should be able to just right-click on the folder you want.  Then select "Make Link", and drag it to your desktop.

---

### Post by robinlennox on 2007-03-11
That worked a treat! 

Thanks!

Strange that you need to log in as "nautilus", to create a link. I'm surprised a user can't create there own shortcuts!

Thanks again!

---

### Post by rsambuca on 2007-03-11
Well actually you can make your own shortcuts, but I thought this way was easy to explain!

I'm glad it worked for you.:D

---

### Post by robinlennox on 2007-03-11
If you can be bothered..... :)

Could you tell me how a user could do this normal...?

---

### Post by rsambuca on 2007-03-11
Sorry, I'm not quite sure what you mean here.  When I said open your file browser (nautilus), I didn't mean that you had to log-in as a different user.  Nautilus is simply the name of the file browser that ubuntu uses.

---

### Post by robinlennox on 2007-03-11
Sorry about my responce if it was unclear you said...

> **rsambuca said:**
> Well actually you can make your own shortcuts, but I thought this way was easy to explain!

I was just wondering how else i could make your own shortcuts. Other than using nautilus

---

### Post by stchman on 2007-03-12
> **robinlennox said:**
> Just wondering how you create shortcuts on my desktop to folders and files...

In Windows it's a case of a right click send to desktop....

With Ubuntu, i'm finding it a bit more diffcult...

Sorry to be a pain!

Regards

Robin

If you mount drives in /media folder it will automatically appear on your desktop.  Example if you create a folder /media/windows and then edit fstab file something like this:

dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0

This will then create an icon on your desktop as Ubuntu does this when you place stuff in the media folder.

I prefer to use the /mnt folder and then create a symbolic link in my /home/<name>/Desktop folder.

---

