---
title: "My IPOD shuffle is upset with me"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by rawry89 on 2008-03-11
Good day,

I seem to have done something silly, as you do. 

With my 1 gig ipod shuffle (new release, the rather small one) I too had the insufficient space problem. Alas I found the Garbage Bin by lucky mistake and rectified that. However, something rather odd happened, I am not sure, and several files have gone missing. they do not show up on Amarok nor rhythmbox, but they still occupy the space.
I thought it a stellar idea to manually go into the ipod control, navigate to Music and delete all the files in there :) Risque! But it worked - sorta. 
I tried to do that again recently, but alas, everything went rather pear shaped! There are about 4-5 files that contain 11,000 files and all the other files I managed to delete I cannot remove from the Garbage bin because they are now, rather magically, 'read only files'. 
I tried using Gksudo Nautilus (or whatever the command is; i was Root) to delete the files, but that failed and so did using Terminal.
Oh and I did of course attempt to return the files in the Garbage bin to the Ipod, but alas I cannot for I do not have permission and it is a read only disc :S I cannot find the files in the garbage bin on nautilus nor using terminal.
SO, any ideas? 

in b/4 "LOL YOU BROKE YOUR IPOD."

P.S. I cannot mount my IPOD in amarok anymore - read only disc
:D Jolly good!

---

### Post by Arthur Archnix on 2008-03-11
Lovely. There are two problems here. The first is that gnome still insists on creating a trash bin on small removable devices, and last time I checked into the situation, the developers felt the ability to use a delete command that bypassed trash was sufficient  (every other OS on the planet be damned!) The second is that apple ipods suck. The good news is neither of these are your fault (I'm assuming it was a present).

The easiest solution is just to plug it into a friends Windows machine and restore the ipod on itunes. Given everything you've described I would say that it is easiest and highly recommended. If that's not possible, try installing gpod and seeing if it's able to fix the filesystem for you.

Once the ipod is restored you need to be careful about how you remove files. Generally, doing it through something like exaile, amarok or gpo is safest, since they've been written to delete stuff in semi-accordance with what the ipod's expect. If you must delete stuff from the ipod, enable the delete command that bypasses trash (upon up a folder like home, at the top >edit >preferences, under the behaviour tab, you'll find it. Then you right-click delete.

The trick for removing stuff off there in the terminal is these two commands:
```
ls -a
```   (which shows you all files, even hidden ones)  and
```
sudo rm
``` (which uses root to remove files, be careful with this one!) if you want to get rid of the trash on your ipod you would do something like
```
cd /media/ipod
sudo rm -R .Trash
```The -R tells it to delete recursively and forces it to remove the folder. Be very careful with that command, because if you mistype it and hit enter, its possible to render your system totally unusable & unfixable. Also, your ipod might not be mounted at /media/ipod, so that would have to be changed.

---

