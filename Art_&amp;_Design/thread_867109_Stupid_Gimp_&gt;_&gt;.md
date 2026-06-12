---
title: "Stupid Gimp &gt;_&gt;"
date: 2008-07-22
forum: Art &amp; Design
---

### Post by sportscar on 2008-07-22
Hey gang, Linux newb here.

I've just what could possibly rank in my top twenty-five most fustraiting experiences. 

I've been interested in using GIMP, I like to dabble here and there with drawing pictures, and scanning them in, drawing in lines using vectors and then colouring them in. I've had great success in the past using photoshop, and hoped that GIMP could do the same.
I managed to find a plug-in called Gimp-shop which arranges the menus and other things in GIMP to make it more user friendly towards photoshop users. So I added it.
It loaded up just fine and I thought everything was cool.
At a later point I decided to give it a go, and the funny thing was that it didn't load at all. I tried then running it from terminal, by simply typing in GIMP. To my surprise it worked. (or at least it loaded up)

So tonight I did just that, started a new project and got to work. I'd just put in a few blue lines mapping out the picture, I added a picture of a car as another layer, then started a third layer for lines. Then I got to work putting in lines, essentially painstakingly tracing over the car using the pen tool. Now perhaps this is where I went wrong, I'm not sure. But I would add a line, then to add another one, I would select the pen tool again, which would get rid of the previous paths.

I was just about to get started on the windscreen when it closed with out warning. Very Fustraiting. 
The terminal window was still open, and here's what it read.

```
:~$ gimp
/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:15756): LibGimpBase-WARNING **: gimp: wire_read(): error

(gimp:15756): Gimp-Vectors-CRITICAL **: gimp_vectors_real_stroke_get_next: assertion `stroke != NULL' failed

(gimp:15756): Gimp-Vectors-CRITICAL **: gimp_vectors_real_stroke_get_next: assertion `stroke != NULL' failed

(gimp:15756): Gimp-Vectors-CRITICAL **: gimp_vectors_real_stroke_get_next: assertion `stroke != NULL' failed

(gimp:15756): Gimp-Vectors-CRITICAL **: gimp_vectors_real_stroke_get_next: assertion `stroke != NULL' failed

(gimp:15756): Gimp-Vectors-CRITICAL **: gimp_vectors_real_stroke_get_next: assertion `stroke != NULL' failed

(gimp:15756): Gimp-Vectors-CRITICAL **: gimp_vectors_real_stroke_get_next: assertion `stroke != NULL' failed

(gimp:15756): Gimp-Vectors-CRITICAL **: gimp_vectors_real_stroke_get_next: assertion `stroke != NULL' failed

(gimp:15756): Gimp-Vectors-CRITICAL **: gimp_vectors_real_stroke_get_next: assertion `stroke != NULL' failed

(gimp:15756): Gimp-Vectors-CRITICAL **: gimp_vectors_real_stroke_get_next: assertion `stroke != NULL' failed

(gimp:15756): Gimp-Vectors-CRITICAL **: gimp_vectors_real_stroke_get_next: assertion `stroke != NULL' failed

(gimp:15756): Gimp-Vectors-CRITICAL **: gimp_vectors_real_stroke_get_next: assertion `stroke != NULL' failed

(gimp:15756): Gimp-Vectors-CRITICAL **: gimp_vectors_real_stroke_get_next: assertion `stroke != NULL' failed

(gimp:15756): Gimp-Vectors-CRITICAL **: gimp_vectors_real_stroke_get_next: assertion `stroke != NULL' failed

(gimp:15756): Gimp-Vectors-CRITICAL **: gimp_vectors_real_stroke_get_next: assertion `stroke != NULL' failed

***MEMORY-ERROR***: gimp[15756]: GSlice: assertion failed: sinfo->n_allocated > 0
gimp: terminated: Aborted

(script-fu:15758): LibGimpBase-WARNING **: script-fu: wire_read(): error

```

Perhaps I shoud've posted here about my seemingly faulty GIMP before I lost a fun little project but hey. *shrug*

So is this problem unusual, or has anything similar happened to other users in the past? 
Could this problem be an isolated GIMP problem, or is there something that could affect similar future programs running on this install of linux?
Are there any clues as to how I could fix this problem?
Does GIMP usually abort with out warning? 
Are there any _stable_ programs for linux akin to photoshop?

---

### Post by scragar on 2008-07-22
try reinstalling the libaries first, incase that's the problem
```
sudo apt-get install --reinstall libgimp2.0
```

---

### Post by Xfcn on 2008-07-22
GIMPshop, I've found, is really meant for Windows users. On Linux, best to stick with pure-bred GIMP. Then go and change the preferences of the keyboard layouts to what you remember or like (I used to change a few of them in Photoshop as well).

---

### Post by sportscar on 2008-07-22
Well I've tried installing gimp once more, and I still get the same problem. :/
Looking at the error message again, could it have crashed because its missing a print libary? Surly not?

---

### Post by lyceum on 2008-07-22
I am not an expert, but I would say that > (script-fu:15758): LibGimpBase-WARNING **: script-fu: wire_read(): error is your problem. Get rid of the script-fu and see what happens.

---

### Post by sportscar on 2008-07-22
> **lyceum said:**
> I am not an expert, but I would say that  is your problem. Get rid of the script-fu and see what happens.

How could I go about removing script-fu?

---

### Post by lyceum on 2008-07-23
> **sportscar said:**
> How could I go about removing script-fu?

/home/user/.gimp-2.4

---

### Post by Orlsend on 2008-07-23
Sur excuse me

What do I do when this Happens:

> (gimp:7269): LibGimpBase-WARNING **: gimp: wire_read(): error

Halp is much thanked

---

### Post by Jon Monreal on 2008-07-23
> **Orlsend said:**
> Sur excuse me

What do I do when this Happens:



Halp is much thanked

Could you post the rest of the output?

I experienced this once because of librsvg not being installed, but this is not necessarily your case.

---

### Post by DPic on 2010-03-30
My friend is having the same problem, down to not being able to run from the menu, and being forced to run from the command line (actually, we created a shortcut). 

Except he's having it with the default Gimp 2.6 that comes with Ubuntu, not GIMPshop. 

~$ gimp
/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:4074): LibGimpBase-WARNING **: gimp: wire_read(): error

(gimp:4074): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gimp:4074): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gimp:4074): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gimp:4074): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gimp:4074): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gimp:4074): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

***MEMORY-ERROR***: gimp[4074]: GSlice: assertion failed: sinfo->n_allocated > 0
gimp: terminated: Aborted

(script-fu:4076): LibGimpBase-WARNING **: script-fu: wire_read(): error

---

### Post by Fixman on 2010-03-31
```
/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory
```

This is definely the main error, try reinstalling libgimp from APT.

---

