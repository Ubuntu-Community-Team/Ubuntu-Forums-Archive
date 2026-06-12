---
title: "[SOLVED] trying to use a new GTK theme"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by -gabe-noob- on 2008-03-27
I am  trying to downloade and enable this theme

[http://duttybreakage.deviantart.com/art/Mire-v2-Grime-77898229](http://duttybreakage.deviantart.com/art/Mire-v2-Grime-77898229) 

 I cant figure out how to make it work, will someone please help me?

---

### Post by forrestcupp on 2008-03-27
All you have to do is download the file to your hard drive, then go to System->Preferences->Appearance, and in the Themes tab, click the install button and navigate to where you downloaded that file to, and choose it.

---

### Post by jordanmthomas on 2008-03-27
First, open the zip file you download from DeviantArt
Then, press Alt + F2 and type 
```
~/.themes
```
Now, in the window with the opened zip folder, double click the folder that you see there.
Drag and drop the folder called Mire v2_grime into your ~/.themes folder you just opened

After this, it should show up in your themes lists.
If you want to install the emerald theme with it, you can just double click mire.emerald in the zip

Hope this helps

---

### Post by -gabe-noob- on 2008-03-27
it didnt come as a .zip thats why I'm having so much trouble

it came with a gtkrc though.


edit: I download it as a .zip but when I extracted from archive manager to my desktop all the files dispers, and are not kept in the .zip.

double edit: I found the .zip but it says its an invalid format.

TRIPLE edit: I did what the person above me said but it still doestn show.

---

### Post by -gabe-noob- on 2008-03-27
still not awnserd. :(:(:(:(:(

---

### Post by forrestcupp on 2008-03-27
Did you try what I said?  Don't unzip it, just try to open the compressed file the way I told you earlier.

---

### Post by -gabe-noob- on 2008-03-27
after stoping my retartedness i got it.

---

### Post by jordanmthomas on 2008-03-27
[COLOR="Silver"]> **forrestcupp said:**
> Did you try what I said?  Don't unzip it, just try to open the compressed file the way I told you earlier.

That won't work.

Try this:
Save file on your desktop
open a terminal type
```
cd Desktop
unzip Mire_v2_Grime_by_DuttyBreakage.zip
mv Mire\ v2\ Grime/Mire\ v2_Grime/ ~/.themes

```
This should **certainly** get it installed[/COLOR]

edit:
Woops, been solved now.  Ignore this post  :)

---

### Post by Therion on 2008-03-27
Okay, so you have the .zip file, right?  
Right click on the .zip file and click on "Extract Here".
Open the Mire v2 Grime folder.
Drag and Drop the Mire v2 Grime folder you find *there* on the the Appearances Manager window.

I did just that, just now, and the theme installed correctly.

---

### Post by forrestcupp on 2008-03-28
> **jordanmthomas said:**
> 

That won't work.


You guys are all crazy.:)  He asked about a GTK theme, right?  Every GTK theme I've used is a tar.gz compressed file.  I've always gone to System->Preferences->Appearance and in the Themes tab I click Install.  In the Install dialog box, I open the tar.gz file I downloaded (that is still compressed) and it automatically installs it for me.  It becomes one of the choices in the list.

In fact, I just tried it.  How can everyone say it doesn't work that way?

Edit:
Ok, I see.  This particular file is an actual zip and not a tar.gz zipped file.

---

