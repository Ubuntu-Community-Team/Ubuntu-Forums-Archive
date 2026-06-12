---
title: "cant find programs installed with synaptic"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by smile_sunshine on 2006-11-17
Hi,
have just installed xubuntu a few days ago (by the way I think its great - really easy to use :)  

I've just got one problem - I've installed new programs using synaptic but they're not added to any menus and I can't find them afterwards. 
If someone could tell me how to find these programs and add them to menus that would be great.

thanks :)

---

### Post by ryu kun on 2006-11-17
In Ubuntu, to find installed programs, hit ALT+F2 and type "gksu /usr/sbin/synaptic", synaptic should run. Then click status button on the bottom left side, and select "installed" on the left panel. Installed applications should be listed on the right panel.

Normally programs add themselves to the menus but if one doesn't, you can use Alacarte Menu Editor in Applications, Accessories menu.

All these are for Ubuntu, sorry if it varies in Xubuntu.

---

### Post by taurus on 2006-11-17
What programs are we talking here?

---

### Post by smile_sunshine on 2006-11-17
various ones - downloaded twinkle (voice over ip) and couldnt find it, also some games, 
but looking at installed packages in synaptic worked :) thanks.
Haven't got Alacarte Menu Editor but have found Xfce4-MenuEditor so not I can figure out how to use that :)  
sorted -
 thanks :)

---

### Post by frogotronic on 2006-11-18
> **smile_sunshine said:**
> Hi,
have just installed xubuntu a few days ago (by the way I think its great - really easy to use :)  

I've just got one problem - I've installed new programs using synaptic but they're not added to any menus and I can't find them afterwards. 
If someone could tell me how to find these programs and add them to menus that would be great.

thanks :)


From the terminal, type ```
update-menus
``` then use alacarte to choose them to display as you see fit.

- CH

---

### Post by ComplexNumber on 2006-11-18
> **smile_sunshine said:**
> Hi,
have just installed xubuntu a few days ago (by the way I think its great - really easy to use :)  

I've just got one problem - I've installed new programs using synaptic but they're not added to any menus and I can't find them afterwards. 
If someone could tell me how to find these programs and add them to menus that would be great.

thanks :)
some programs don't, so there's nothing to worry about. however, if none of them do, it may be that the permissions to the menu have somehow been changed. i've known it to happen. go to /home/<your-username>/.local/share/applications. then right click on any file in there and select Properties. then go to the permissions tab. is the owner 'root'?

---

