---
title: "Adding New Icons for iRiver music player"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by nandotron on 2007-03-17
Hi!

I just started using ubuntu.  I own an iriver H340, which, when i plug into my computer shows up with an ipod icon on the desktop.  

I downloaded some really nice new icons from gnome-look.org for the iriver, a 22x22, 48x48 and a scaleable.  Is there a place in the filesystem that i can house these so that nautilis will implement all three when i am browsing the player?  

i tried to add them to usr/share/icons but it wouldnt allow me write access.  any help would be really appreciated!

Thanks,
Enda

---

### Post by steve101101 on 2007-03-17
to gain access to a folder type

```

sudo chown -R system_username /location_of_stuff

```

or/and

```

sudo chgrp -R system_username /location_of_stuff

```

with both of these commands the "-R" adds the access presences to all folders inside the original folder. 

I hope this helps.

---

### Post by nandotron on 2007-03-17
hi

thanks a lot, i was able to write the iriver icons folder to usr/share/icons.

Not sure if i'm doing this right, but i assigned the scaleable icon to the mp3 player on the desktop by going into properties and pointing it to the location of the icon.

However, in nautilis the smaller icons are all still the original ipod 22x22 and 48x48 icons.  anyone know what i'm doing wrong?

---

### Post by nandotron on 2007-03-22
Hi guys,

so i renamed all the iriver icons to match the names of the ipod icons already present in the human theme and substituted the iriver icons into the human icon folder.

theoretically, shouldnt this replace all instances of the ipod icons in nautilis with the iriver icons?  I'm still seeing the ipod icons in rhythymbox and in parts of nautilis (like in the location buttons across the top of each window.  

anyone know how i messed up?


nando

---

