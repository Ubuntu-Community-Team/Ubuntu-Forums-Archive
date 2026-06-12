---
title: "glib probs"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by richieboy on 2006-05-18
hi.
i was having glib problems like the on listed here:  [http://www.ubuntuforums.org/showthread.php?t=178752&highlight=GLIB](http://www.ubuntuforums.org/showthread.php?t=178752&highlight=GLIB).

i followed the direction there and even installed the new glib 2.11.1.  now i get this error message:

checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... *** GLIB header files (version 2.11.1) do not match
*** library (version 2.8.3)
no
configure: error: unable to find the GLib library.

should i cp glib-2.0.pc to /usr/bin/pkg-config?  does anyone have ideas.  i can't run make or make install commands.

thanks,
rich

---

### Post by catlett on 2006-05-18
> i can't run make or make install commands.
I don't know if this is what you're refering to but to compile a tar file or compile from source you need to install a program build-essential. Enter this in your terminal. First refresh your package cache. ```
sudo apt-get update
``` Then install build essential ```
sudo apt-get install build-essential
``` In my signature there are links to pages that explain install. To give a quick run down. If you have to download a tar file. Firefox will put it on your desktop. To be easy about it, keep it there. Right click on the package. Choose "extract here".
When you choose extract here a folder will be made on the desktop. You now have to be in the folder "virtually". So in the terminal you have to move there (for sake of example we'll say the folder is called glib 2.11.1. and that your username is richieboy) Enter in the terminal ```
cd /home/richieboy/Desktop/glib 2.11.1
``` Now that your in the folder with the uncompiled package you can compile it. Enter ```
./configure
``` then enter```
 make
``` and finally ```
sudo make install
``` That's it. Then run whatever you were trying to run before. Or it might already aply itself, I don't know because I didn't check your link to see what you were trying to do.
I hope this helped. If this isn't what you meant, disregard it.

---

### Post by richieboy on 2006-05-18
thanks for the reply.  i already had build-essentials installed.  ./configure gets me this error: 

checking for GLIB - version >= 2.0.0... *** GLIB header files (version 2.11.1) do not match
*** library (version 2.8.3)
no
configure: error: unable to find the GLib library.

i have installed every libglib file i can find and no luck.

---

### Post by catlett on 2006-05-18
Try running an aptitude update and upgrade. Aptitude deals with dependencies better. It will try to resolve them instead of giving an error. It might be worth a shot to try ```
sudo aptitude update
``````
 sudo aptitude upgrade
``` Then try to ./configure it. With a bit of luck aptitude will have fixed the library differences.
Also did you enable the univers/multiverse repositories? These will add more packages to your system. You might get lucky and it's in there.
You enable by opening the synaptic package manager (system<administration<synaptic package manager) When it opens hit on settings and then hit on repositories. You can check off the universe/multiverse repos from there and they will be enabled.

---

### Post by richieboy on 2006-05-18
thanks for the reply.  i tried it and no go.  hopefully i'll find an answer.
rich

---

### Post by catlett on 2006-05-18
sorry I couldn't be of help. If I stumble on something usefull I'll post it here.

---

### Post by catlett on 2006-05-18
I think I might have an answer. Did you follow this exactly
> Re: Glib issues
I'm having this same problem, but with an older GLIB (2.5.7 - There's a 2.8.3 out..?). I can't remove GLIB because way, way too many programs depend on it. It's interwined with GTK I think.

I'm trying to install ATK so I can install GTK+ so I can install various applications, but jesus, I just keep running into problem after problem. I was having trouble with Cairo identifying FreeType, too..

Here's what you can do to fix your problem:

sudo gedit /usr/local/lib/pkgconfig/glib-2.0.pc

Change "Version" to 2.8.3

sudo gedit /usr/lib/pkgconfig/glib-2.0.pc

Do the same.

How did you update your GLIB? Could you give me a link to the download?
Before I claim victory let me explain. This post says to put in 2.8.3 to get the new version to match up. Your now getting this error..>  *** GLIB header files (version 2.11.1) do not match
*** library (version 2.8.3)
Did you change the lists to 2.8.3 but install 2.11.1? What about editing like the post said but use this when you edit ```
2.11.1
```  instead of 2.8.3
Hopefully the next time you run the install will match your edited 2.11.1 to the new install of 2.11.1
Or did you already try this?

---

### Post by disk11 on 2006-05-19
I tried catlett's suggestion and that didn't work.  It seems like 2.8.3 doesn't want to go away or Ubuntu is still being pointed to the 2.8.3 folder.

---

### Post by TriggerHappyChewie on 2006-05-30
Try installing the libglib-dev packages from synaptic.

---

