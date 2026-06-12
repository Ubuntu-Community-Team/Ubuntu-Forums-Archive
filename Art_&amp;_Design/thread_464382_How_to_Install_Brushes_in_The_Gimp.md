---
title: "How to Install Brushes in The Gimp"
date: 2007-06-04
forum: Art &amp; Design
---

### Post by sneeker on 2007-06-04
Ok, i've been fiddling with it for an hour now and cant find out how so..

ho do i install new brushes into The Gimp WITHOUT MAKING NEW ONES

any help is appreciated thanx

---

### Post by Ted D. on 2007-06-04
Go to this link.
[http://www.gimptalk.com/forum/topic/1100-Gimp-Brushes-For-Download-24-1.html](http://www.gimptalk.com/forum/topic/1100-Gimp-Brushes-For-Download-24-1.html)

---

### Post by sneeker on 2007-06-04
Thank You So Much!!!! the problem is i dont know where to put them after i download them! :P

do you?

---

### Post by nlfrederick on 2007-06-04
Well, I made a specific folder for all of my downloaded GIMP brushes.

Then, in the program, I went to File>Preferences>Folders>Brushes, and there should only be one button you can click, that is basically an "Add New Folder" button.  Click that and if you've got them all in a specific folder, browse to that folder and add that folder and the brushes will show up in GIMP.

---

### Post by Vadi on 2009-04-03
Just a fyi, they go into ~/.gimp-2.6/brushes

So go to your home folder, and press Ctrl+H to see all hidden folders (ones starting with a dot are considered hidden). Then go into the .gimp-2.6 folder (or .gimp-2.4 if you're on an older version), and then into the *brushes* folder. Put the brushes into there and it'll work.

---

### Post by E.T.Smith on 2009-04-04
I'm trying to install some ne toys into the brushes folder, but the browser keeps giving me a "permission denied" error. Since it looks like this isn't a common problem, what gives?

---

### Post by Vadi on 2009-04-04
That would mean root owns the brushes folder. Why I don't know, but you give it back to you, do alt+f2, and launch the file browser with "gksu nautilus".

It'll look a bit different from your normal one, so go to *home*, *your-username*, *.gimp-2.6*, right-click on the brushes folder, select permissions, and make sure that your username is selected instead of root.

I attached how it looks like for me and works.

---

### Post by AJB2K3 on 2009-04-06
Or you could try this link
[Gimp brushes]("http://www.geocities.com/ajb2k305/tutorials/brush.html")

---

### Post by Cycron on 2009-12-12
Thanks, this post helped me. :)

---

### Post by airtonix on 2009-12-24
remember that the folder they live in will need to change every time your copy of gimp goes up a version.
```

~/.gimp-2.6/*
~/.gimp-2.7/*
~/.gimp-2.8/*
etc
etc

```

---

### Post by girlette on 2010-05-26
> **Vadi said:**
> Just a fyi, they go into ~/.gimp-2.6/brushes

So go to your home folder, and press Ctrl+H to see all hidden folders (ones starting with a dot are considered hidden). Then go into the .gimp-2.6 folder (or .gimp-2.4 if you're on an older version), and then into the *brushes* folder. Put the brushes into there and it'll work.

This is great. It works! Thanks! :)

---

### Post by upokers on 2010-05-26
ohhh I've been looking for this for agess... thanks for sharing.. :) very handy.

---

### Post by kaustavdm on 2010-08-03
Thanks! It helped!

---

### Post by UOutCailin on 2010-11-27
> **vadi said:**
> just a fyi, they go into ~/.gimp-2.6/brushes

so go to your home folder, and press ctrl+h to see all hidden folders (ones starting with a dot are considered hidden). Then go into the .gimp-2.6 folder (or .gimp-2.4 if you're on an older version), and then into the *brushes* folder. Put the brushes into there and it'll work.


\\:d/

---

### Post by Pinkie on 2011-02-09
Perfect installaton guide, now enjoying gimp to it's full capacity.....LOL, THANK YOU!!

---

