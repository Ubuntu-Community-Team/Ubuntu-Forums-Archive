---
title: "XKB keybaord mapping file"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by gryall on 2007-12-14
Right, the absoulote begginer section is probably not the right place for this, but I'm a beginner.

I was recently [reading a blog entry on xkcd.com ]("http://blag.xkcd.com/2007/08/14/mirrorboard-a-one-handed-keyboard-layout-for-the-lazy/")  about a keybaoard mapping. I decided to try it out, downloaded it, and ran the code:

```
xkbcomp mirrorboard-gb.xkb $DISPLAY 2>/dev/null
``` 

This worked exactly as it was suposed to (although i tweaked the xkb file for a UK layout - hence file name change).

I like this so much i decide to try and get it to apply at every start up. So i go to the sessions option (under system, preferences) and added a new start up programme, with the command as the code above. This didn't work. Now I'm guessing its because he sessions thing is looking for programmes. So how do i get commands to run on start up.

Sorry for the badly written noob question, any help would be appreciated.

---

### Post by diatribe on 2007-12-14
you could add the command to your .xinitrc file

---

### Post by gryall on 2007-12-15
OK, How do i do that?

I just had a look round the forums and found the following: ```
echo "*my code*" >> .xinitrc
```

Howeverhaving run that i now get an error message on start up, saying somthing about the gnome-settings-deamon being unavailable (and unsuprisingly all my icons are now no longer the gnome ones, and my colour scheme has change) whilst also it didn't even get the keyboard map to work.

How do i add to my .xinitrc and how do i undo my last edit to it?

---

### Post by gryall on 2007-12-15
Further to my last post, I have now restarted, and although the .xkb still doesnt strart on start up, all the other problems have stopped (perhaps they where random and unrelated?).

I'd still like to get the xkb to work though.

---

### Post by gryall on 2007-12-15
So to be succeinct my new qustion is how do i find/add to my .xinitrc

---

### Post by gryall on 2007-12-15
I have triedadding my command to the end of /etc/X11/xinit/xinitrc but this had no effect. Perhaps I did this wrong or it is the wrong xinitrc?

---

### Post by diatribe on 2007-12-16
~/.xinitrc at the beginning

---

### Post by gryall on 2007-12-16
sorry - I don't quite follow.

---

### Post by diatribe on 2007-12-16
/home/username/.xinitrc

put whatever you want to execute at the beginning of the file

---

### Post by gryall on 2007-12-16
I might of done this wrong, but it didn't seem to work.

I didn't have a .xinitrc file inmy home folder. So i created one and added my command to it. DO i need anything else in it or is there a syntax to it I've missed? Also do i need to change any other files to let them know i've created the files?

Thanks for your help so far.

---

