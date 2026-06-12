---
title: "images"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by antgul3382 on 2007-01-11
is there a "my pictures slideshow" screensaver like windows xp has??? or just a slideshow maker??? i have about 5000 pics in one folder with many subfolders, ive found that gthumb has a slideshow option but doesnt get into the subfolders, is there anything i can use??? ive also noticed that in the screensavers it has a pictures folder screensaver.....is this what i should be using?? it just comes up black

---

### Post by antgul3382 on 2007-01-11
anybody???

---

### Post by partsdale on 2007-01-11
I believe you are correct... the picrures folder screensaver...
I know the xscreensavers package has what you are describing

---

### Post by antgul3382 on 2007-01-11
yes but there is nothig to configure where your "pictures" folder is where do iahve to put my pics???

---

### Post by dbd on 2007-01-11
With xscreensaver just run xscreensaver-demo and click on the Advanced tab, then you can choose were it gets images from (just under where it says "Choose random image")

By the way, if you have your images in different folders you could just provide a load of links to those folders in one folder, then you don't have to move anything about that you don't want to.

---

### Post by antgul3382 on 2007-01-12
where do i get xscreensaver?

---

### Post by blackened on 2007-01-12
> **antgul3382 said:**
> where do i get xscreensaver?

```
sudo apt-get install xscreensaver
```
. o O
or grab it with Synaptic.

---

### Post by dbd on 2007-01-12
Its in the repositories, so you can install it as your would install anything else, just use the Add/Remove&#8230; item in the Applications menu and look for xscreensaver. 

You may need to add some extra repositories if you haven't done some already (you probably have), for info see here:
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html#id2580924](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html#id2580924)

Edit: lol, looks like Blackened beat me to it :)

---

### Post by blackened on 2007-01-12
You went the extra mile to add the repo link, otherwise you would've beaten me. ;)

---

### Post by antgul3382 on 2007-01-12
ok i got it but theres no advanced button for the pictures folder screensaver

have a look

---

### Post by dbd on 2007-01-12
xscreensaver is a separate screensaver program, so you need to disable the normal screensaver and then configure xscreensaver using the command:
xscreensaver-demo

Also you'll need to set xscreensaver to run at boot. To do this Choose System->Preferences->Sessions and click on the Startup Programs tab, and then add xscreensaver as one of the startup programs.

---

### Post by antgul3382 on 2007-01-12
does anyone know how to get my pics on this damn screensaver or what folder i gotta put em in to get it to show em?????
heeeeeeeeeeeeeeeeelp!!!!!](*,)

---

### Post by blackened on 2007-01-12
Have you tried what dbd suggested?

---

### Post by antgul3382 on 2007-01-12
i got the this up to configure it but what do i do now???  i see nothing with pictures/images/etc in the name   also not sure how to disable the other screensaver

---

### Post by sloggerkhan on 2007-01-12
I would recomend using f-spot and then the f-spot screen saver. Just make sure that some of the photos you keep in f-spot are tagged as favorites and the f-spot screen saver works perfectly.

---

### Post by blackened on 2007-01-12
Alright. Babysteps. First Alt+F2 then xscreensaver then "Settings".

From there choose from the dropdown box "Only One Screensaver".
Then in the list on the left choose "GLSlideshow".
Then choose the "Advanced" tab.
In the top left box labeled "Image Manipulation" check the "Choose Random Image" box.
Then in the text field below that enter the path to your pictures.
Then flip back to the "Display Modes" tab and test it out with the "Preview" button.

---

### Post by blackened on 2007-01-12
As sloggerkhan suggest, f-spot as a screensaver might be a bit more lightweight.

---

### Post by antgul3382 on 2007-01-12
thanks alot for the help but the xscreensaver doesnt do ****](*,) 
im gonna try the other one now!

---

