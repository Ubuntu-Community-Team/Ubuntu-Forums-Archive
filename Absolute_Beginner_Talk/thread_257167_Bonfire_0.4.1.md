---
title: "Bonfire 0.4.1"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by bobanshirl on 2006-09-14
I recently downloaded this software and got both tar.gz and tar.bz2.I put them both on my desk top and right clicked on tar.gz and clicked extract here which it did.I thought great so I double clicked on the extracted icon but got a window with loads of icons one of them said install so I clcked that but then got told I had to do some compiling.Well I have not a clue about that so is there an easy way to install or not by the way bonfire is not shown as installed

---

### Post by calvinthomas on 2006-09-14
You need to do this:

Go to a terminal and navigate to the directory you have extracted it to:

To do this type: **cd Desktop/<name of folder>**

Now you need to configure the package for your system.

**Just type ./configure**

Now you need to make the package:

**Just type make**

Now finally to install **type make install**

You can then run the package by pressing alt F2 and typing bonfire

Its excellent software so its worth the small amount of extra effort.

ALTERNATIVE METHOD:

Notice that on the download part there is an rpm file? You can download that and then do this in a terminal:
[B]
sudo apt-get install alien[/B]

Then after that has installed type:

**sudo alien <name of file>** (easiest to just drag and drop the file into the terminal!)

That will create a .deb, then **double click on the deb file and click install.**

Note: The first method is the preferred method!

Note 2: It is worth learning the method of compiling software and also the alien command, however if your uncomfortable with it K3B is an alternative cd/dvd burner that is excellent. In my opinion however, bonfire is better (although I think i'm in the minority!)

Calv

---

### Post by calvinthomas on 2006-09-14
A third and easiest method, for the very latest version called brasero (version 0.44)

Go to a terminal:

Type gksudo gedit /etc/apt/sources.list

and add this line:

deb [http://mrpouit.tuxfamily.org](http://mrpouit.tuxfamily.org) dapper-pouit backports contrib

Save and then exit.

Then go back to the terminal and type:

wget -q [http://mrpouit.tuxfamily.org/12B83718.gpg](http://mrpouit.tuxfamily.org/12B83718.gpg) -O- | sudo apt-key add -

This will add the required public key for the repository. Press enter

When that finishes (very quick) type:

sudo apt-get update

Then just type sudo apt-get install brasero and it'll install.

I've just tried this method and it worked fine, also the methods from the previous post will work if you want the stable 0.41 release.

Calv

---

### Post by lamego on 2006-09-14
Or even easier to install, using firefox just double click the .deb link:
[http://www.getdeb.net/getdeb.php?file=brasero_0.4.4-1_i386.deb](http://www.getdeb.net/getdeb.php?file=brasero_0.4.4-1_i386.deb)

---

### Post by bobanshirl on 2006-09-14
Thanks to all.I used lamego`s suggestion and I have got it on my desk top.Cheers

---

### Post by bobanshirl on 2006-09-15
hi calvin when i type cd desktop/??? it comes up command not recognised.WHAT IS WRONG

---

### Post by xyz on 2006-09-15
I haven't tried it but could you post your appreciation for Brasero. I'd be interested if there'd be any good reason for switching from K3B or Gnomebaker.
Thanks in advance.

---

### Post by calvinthomas on 2006-09-15
> **bobanshirl said:**
> hi calvin when i type cd desktop/??? it comes up command not recognised.WHAT IS WRONG

You have made the mistake that I made when I first tried to access my desktop from the terminal, you have missed out the capital d, i.e.

cd desktop does not work

cd Desktop does

Calv

---

### Post by calvinthomas on 2006-09-15
> **xyz said:**
> I haven't tried it but could you post your appreciation for Brasero. I'd be interested if there'd be any good reason for switching from K3B or Gnomebaker.
Thanks in advance.

Personally I prefer it to K3B or gnomebaker, i'm not a heavy cd/dvd burner though, i've only burnt an ubuntu iso! I prefer it for the interface, I find it cleaner, nicer and more intuitive, whether its better for advanced users, I don't know

Calv

---

### Post by xyz on 2006-09-15
Thanks **calvinthomas**...I'll give it a try.
I tend to like intuitive stuff!

---

### Post by bobanshirl on 2006-09-15
Ive tried a capital d but it still doesnt work

---

### Post by calvinthomas on 2006-09-15
err i'm not sure, have you left a space between cd and Desktop? Like this: cd Desktop?

Does it work when you just type cd Desktop but not when you type cd Desktop/<name of file>?

I would suggest if your still having problems to start a new thread with this problem because i'm not skilled enough to be able to help but others will be!

Calv

---

