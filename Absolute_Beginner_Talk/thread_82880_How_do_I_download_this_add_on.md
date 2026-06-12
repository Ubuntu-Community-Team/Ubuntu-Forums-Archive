---
title: "How do I download this add on?"
date: 2005-10-27
forum: Absolute Beginner Talk
---

### Post by Breezy Badger on 2005-10-27
I need libtiff3g to install my printer but I just have no option get it, any idea.  I def need this.




```
xxxxxxr@xxxxxxx:~$ sudo apt-get install libtiff3g
Reading package lists... Done
Building dependency tree... Done
Package libtiff3g is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libtiff3g has no installation candidate
```

Badger

---

### Post by az on 2005-10-27
[http://packages.ubuntu.com/breezy/libdevel/libtiff4-dev](http://packages.ubuntu.com/breezy/libdevel/libtiff4-dev)

libtiff3g is old.

---

### Post by Breezy Badger on 2005-10-27
thanks for the link but I am not exactly sure what I am supposed to download on that page, it looks like libtiff4

Badger

---

### Post by Mustard on 2005-10-27
[QUOTE=Breezy Badger]thanks for the link but I am not exactly sure what I am supposed to download on that page, it looks like libtiff4

Badger[/QUOTE]

libtiff4-dev

Install via synaptic or apt-get.

Might as well install libtiff4 too.  I can't see how it will hurt.

---

### Post by dbott67 on 2005-10-27
Basically, do the same thing you did for libtiff3, but replace with libtiff4:
```
sudo apt-get install libtiff4
```

-Dave

---

### Post by Breezy Badger on 2005-10-27
hey guys I already have libtiff4, but I need 3, is there something I am just overlooking here?

Badger

---

### Post by az on 2005-10-27
[QUOTE=Breezy Badger]thanks for the link but I am not exactly sure what I am supposed to download on that page, it looks like libtiff4

Badger[/QUOTE]
I am assuming that you are trying to compile something.  Try using that package instead of the libtiff3 package.  Not knowing what you are trying to do, I would give it a shot...

---

### Post by Breezy Badger on 2005-10-27
I am trying to do this, (get my printer to work, which depends on libtiff3)

```
first go to canon and download the rmps bjfilter cups and bjfilteri250
then in super user mode (su or just use sudo infront of everyline) do this:
alien bj*
after that dpkg -i *.deb
now since these packages were made for redhat 9 there are some dependencies..
so do this
apt-get install libtiff3g libxml1 libglade0 libpng2
that should do it.. now just add a printer and choose the i250 driver
now the problem i had is with the resolution.. i can only run high quality printing.. do you have anyway of printing draft papers.. it's not a good idea to print a full book with high quality (i learned that the hard way)

later all..
```

Still think I should try 4?

---

### Post by Breezy Badger on 2005-10-27
UPDATE: I have libtiff installed, I still get the original msg I posted, I need libtiff3, I cant use the canon deb pack is its dependent on libtiff3

Badger

---

### Post by Mustard on 2005-10-27
[QUOTE=Breezy Badger]UPDATE: I have libtiff installed, I still get the original msg I posted, I need libtiff3, I cant use the canon deb pack is its dependent on libtiff3

Badger[/QUOTE]

It would appear that you are still trying to sudo apt-get libtiff3g if you are still recieving the error in your first post.  The point that was probably not made was that libtiff4 is the newest version (in ubuntu) and therefore should supercede the older version.  This should mean that you no longer need to include libtiff3g in the apt-get command you are trying to run.  Drop libtiff3g from the the apt-get command completly, or replace it with libtiff4 (which would be redundant now, since you have already installed it).

Does that help?

If you are getting a different error altogether then you will need to paste that error in here too.

-edit-

If you are running dpkg on a non ubuntu deb, which you seem to be doing, and this is the issue you are having, then you will probably need to edit the .deb package to make it depend on libtiff4.  It might be helpful if you actually printed the output you recieve when you run dpkg on this .deb you have created, rather than the output of the apt-get command.  Editing .deb packages is not a straightforward operation and would require more experience than I have.

---

### Post by Breezy Badger on 2005-10-27
I will try that in a bit mustard, I am on XP right now. Soon as I get a chance I will post back and let you know if that works

thanks

---

### Post by noigeaR on 2005-10-28
looks like you're trying to install the linux drivers for a canon printer. i don't know if this helps for your model, but there's a how-to for installing linux drivers for the canon pixma printers here: [http://ubuntuforums.org/showthread.php?t=38995]("http://ubuntuforums.org/showthread.php?t=38995")

especially step 6 could be interesting for you

> 6. Fix libs

$sudo ln -s /usr/lib/libpng12.so.0 /usr/lib/libpng.so.2
**$sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3**
$sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1

(i don't know why i do this but otherwise the printer does not work)

---

### Post by Breezy Badger on 2005-10-29
Sorry for the delay guys but here is what I have come up with.

this is what I am trying to do:

> "intalling Canon i250 printer drivers for KUBUNTU"

firts download the "canon-i250_2.3_i386.deb" (its here: [http://www.livux.org/otros/canon-i250_2.3_i386.deb](http://www.livux.org/otros/canon-i250_2.3_i386.deb)) on your Desktop.
Use dpkg --force-depends -i canon-i250_2.3_i386.deb to brutally install it.
Now type: apt-get -f upgrade
if you have any broken packages do an: apt-get install knetworkconf, that sould do it.
apt-get upgrade to finish all cleanly
and lets check if all work out, type apt-get install canon-i250
You should see a message like this: "canon-i250 its already in its latest version"

add your printer and thats it 

When I do what he says above this is the results I get:

```
badger@badger:~$ cd Desktop/
badger@badger:~/Desktop$ sudo dpkg --force depends -i canon-i250_2.3_i386.deb
Selecting previously deselected package canon-i250.
(Reading database ... 81994 files and directories currently installed.)
Unpacking canon-i250 (from canon-i250_2.3_i386.deb) ...
dpkg: canon-i250: dependency problems, but configuring anyway as you request:
 canon-i250 depends on libtiff3g; however:
  Package libtiff3g is not installed.
Setting up canon-i250 (2.3) ...
badger@badger:~/Desktop$

```


I tried typing this code before I did the install, and it made no difference:

```
$sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
```

I am really stumped here guys and I do not know how to get this damn printer working without libtiff3

Badger

---

