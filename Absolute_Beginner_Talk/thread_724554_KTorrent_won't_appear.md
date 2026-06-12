---
title: "KTorrent won't appear"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by NOLU on 2008-03-14
Been using KTorrent for months now but today it won't show up when I click on the icon. I've even started a download but although the box appears to choose what files, the KT application won't show.

Any idea's how I can get this showing please?

---

### Post by joshrobinson on 2008-03-14
run ktorrent from a terminal, and post the output to see if there are any error messages

but have you ever tried azureus? thats the bittorent client i use, and its the best ive found so far

---

### Post by NOLU on 2008-03-15
If I type KTorrent in terminal, it says its running.

I used to use azureus when I used Vista but so haven't really really tried since moving to Ubuntu.

---

### Post by forestpixie on 2008-03-15
have you lost you notification area ? - try adding it to the panel

---

### Post by NOLU on 2008-03-15
Sorry. How do I go about doing that?

---

### Post by oliviacond on 2008-03-15
right click on KTorrent launcher from the left corner menu, and select "Add to launcher"

---

### Post by forestpixie on 2008-03-15
right click the panel - Add to panle - find notification area and add it

---

### Post by NOLU on 2008-03-15
The Ktorrent icon is on the bar although I had this on my AWN bar below but it still won't show the application even when I try to launch it. It's running but I can't see it still.

---

### Post by forestpixie on 2008-03-15
oh I see - you're clicking the panle icon - just assumed you meant the menu one - sorry

Have you tried reinstalling it - after you've got rid of the hidden folder in /home. I had to do that last year with an older version of KTorrent.

---

### Post by NOLU on 2008-03-15
re-installed but still won't show up :(

---

### Post by NOLU on 2008-03-15
I'm going to install Azureus and see what happens with that.

---

### Post by forestpixie on 2008-03-15
did you try removing the hidden folder?

---

### Post by NOLU on 2008-03-15
This may sound dumb as I'm new to this but where will I find a hidden folder? How do I make something hidden unhidden :D

---

### Post by forestpixie on 2008-03-15
Doesn't sound dumb in the least unless you expect to born with all knowledge.
If you've currently got ktoorent installed - uninstall it

```
sudo apt-get remove --purge ktorrent
```

open nautilus, got to view and click view hidden files, nautilus being the file manger - assumption here being that you're using ubuntu

now you'll see the hidden files - as an aside to make a file/folder hidden precede the name with .

now - look for .kde - open that in ther navigate to share/apps/ delete ktorrent - now reinstall

```
sudo apt-get install ktorrent
```

---

### Post by NOLU on 2008-03-15
I an on Ubuntu but can't see anything called nautilus. Is it in the System drop down menu?

---

### Post by billgoldberg on 2008-03-15
Nautilus is the name of the file manager. (like the filemanager in windows is called "explorer")

You open it by going to places -> home folder.

And to view hidden files it's easier to press "ctrl + h"

Maybe a stupid question, but I also use ktorrent and when I click the icon in the top bar it won't pop open if it is on another desktop.
Is it on another desktop?

---

### Post by NOLU on 2008-03-15
I deleted the hidden folder and re-installed but it still won't launch. I've looked on the other desktops and there is nothing showing there.

---

