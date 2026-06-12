---
title: "Very Confused (Filesystem)"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by BigLebowski on 2006-10-24
Hello again,

I'm having real trouble understanding the filesystem.. What i want to be able to do is move a whole program such as aMule into a encrypted partition, now this was easy in Windows you would:

Go to Mycomputer> Cdrive> programfiles> then you would find the program in its very own folder.. then just move it to the encrypted partition..


But in Ubuntu it seems the program files are spread all over the place.. i just don't understand.. 




Any help would be great, thanks

Lebowski


(And yes i know with most Windows programs and some linux programs ask you where you want to install but not all.. especially if i install using something like automatix)


EDIT: I turned off hidden files and found the aMule directory is that all the files.. can i just move that to my enxrypted partition and it will function properly?

---

### Post by kidders on 2006-10-24
Hi there,

> **BigLebowski said:**
> What i want to be able to do is move a whole program such as aMule into a encrypted partition
Most of the time, you won't want to try doing this, since on most operating systems, programs scatter their data all over the place. Between system libraries, documentation, user preferences, configuration data, the application's binaries themselves, etc., there are lots of places to look. Then, depending on exactly *why* you wanted the application encrypted, you'd have to worry about protecting your virtual RAM, etc.

Having said that, every now and then you'll find applications that don't scatter data around quite so much, especially if they're not native to the platform you're running them on.

What are you trying to achieve by putting an app in encrypted filestorage?

> **BigLebowski said:**
> I can't seem to find the .deb file for VLC(Im guessing its a .Deb file i need to click on correct me if im wrong)
A .deb is just an installer archive. You want the application binary itself, I'd say.

---

### Post by maaronB on 2006-10-24
You are asking a pretty big question.  And the answer does depend on a few factors. 

> EDIT: I turned off hidden files and found the aMule directory is that all the files.. can i just move that to my enxrypted partition and it will function properly?

No, the hidden file in your home directory is most likely just some storage and setup files.  
The first thing you need to do is understand how the Linux filesystem works.
This is a good/quick read on that:  [http://ubuntuforums.org/showthread.php?t=126107](http://ubuntuforums.org/showthread.php?t=126107)
basically what you need to know is that the executable program is stored in 
/bin, /usr/bin, or some such.  
docs are stored in 
/usr/doc or /usr/share/doc 
temp files can be stored somewhere else.
your personal settings will be stored in that hidden file you mentioned.
and the files that you are sharing will be stored where ever you point aMule to store/read them.


I suppose if you wanted you could move the the executable to your hidden folder the add the folder to your path.  Then encrypt the entire thing.  But there is probably a better way to accomplish what you want.

If you could specify what you are actually trying to accomplish somebody could probably help a little easier.

---

### Post by Ben Sprinkle on 2006-10-24
```
sudo mv /media/hda1/folder /media/hda2/folder
```
Easy eh?

---

