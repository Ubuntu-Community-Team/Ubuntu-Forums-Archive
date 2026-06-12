---
title: "Working Canon Bjc 4300 printer"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by richbarna on 2006-05-14
Just in case anyone is still having a problem with this printer, or any Canon printer for that matter.

This is what I did :-
Make sure you have got the cupsys gimp print drivers installed.
1. You can open Adept/Synaptic and type "cupsys-driver-gimpprint" and install from there.
2. Open the terminal and type :-
> sudo apt-get install cupsys-driver-gimpprint
3. Download Turbo Print From :- [http://www.turboprint.de/english.html]("http://www.turboprint.de/english.html")
Enter your details and download the file "turboprint-1.94-2.tgz" to the desktop.
4. Right click on the file and Extract/ Here
5. Click open the folder and do a right click on the mouse and choose Actions/ Open Terminal Here.
6. In the Terminal/Console type :- su (to switch user to root)
7. Enter your password click enter.
8. Type :- ./setup and enter (this will start the install script)
9. You will now have a Turbo Print Setup and a Turbo Print Config icon/file on the desktop, click and configure.
10. Open your print manager and click add-printer
11. This time don't choose the Canon printer but the Canon Turbo Printer

That worked for me please post if you have any problems.

---

### Post by richbarna on 2006-05-14
It broke.............
AGAIN !!!!!!!!
What is wrong with CANON !!!!!!!!

---

### Post by richbarna on 2006-05-15
Er, my fault, I changed the login to the print server to anonymous.
Now works fine :)

---

### Post by Sef on 2006-05-15
> What is wrong with CANON

Would be nice if they open sourced their drivers.

---

### Post by richbarna on 2006-05-15
Yeah, I know.
Mission 1: Make everybody reject windows and come over to Ubuntu.
Mission 2: Boycott Canon for being capitalist un-open source gits.
Mission 3: Buy an Epson printer.

---

### Post by pierre.s.rosen on 2006-06-02
What a great fix!  Although I hate using closed source drivers, I will if there is no opensource solution that works.  This driver will allow me to fully use Linux!

Now if only there was a closed source driver for my Creative Webcam....

---

### Post by meng on 2006-06-02
[QUOTE=pierre.s.rosen]Now if only there was a closed source driver for my Creative Webcam....[/QUOTE]
I'm a tad confused about this statement, I can't figure out if it's a clever joke, or if you're having a problem then perhaps you can tell us about it.

---

### Post by dvarsam on 2006-06-02
Hello!

I have an Ubuntu Dapper v6.06.

I performed as your Suggested!

I have the 2 icons on the Desktop, but when I double-click on them nothing happens...

I do NOT know what is wrong with the program.

When I tried to install the program with "./setup", I got the following:

> Checking shared libraries:
(add missing libraries with your package manager)

* gtk     library NOT found
* gdk     library NOT found (part of gtk)
* gmodule library NOT found (part of gtk)
* gmodule library NOT found (part of gtk)

The program seems to have installed, but when I click on the icons on the Desktop, I get nothing!!!

Can somebody tell me if I am missing a package, & if YES which one?

Thanks.

---

### Post by pierre.s.rosen on 2006-06-03
I was serious, until i discovered that Dapper recognized my webcam, at least in Ekiga!   I wasn't able to get it to work with Amsn though....and it seems that the libraries loaded with amsn conflict with Ekiga.  I had to uninstall all of amsn and libraries and then ekiga (which uninstalled the desktop...wtf is up with that!?) and then reinstalled both and everything is working fine now.  Now if only gaim-vv would work...

---

### Post by pierre.s.rosen on 2006-06-03
dvarsam:

You are missing some packages.  You need to install those packages that you cut and pasted above.  Those packages will be installed if you install most of the optional software listed in the Ubuntu Desktop Guide ([http://help.ubuntu.com/ubuntu/desktopguide/C/index.html](http://help.ubuntu.com/ubuntu/desktopguide/C/index.html) ) and the packages for Restricted Formats.

---

### Post by meng on 2006-06-03
That uninstall desktop thing is confusing, but think of it like this:

The desktop is a big box that all the default applications come in. (Those defaults applications are listed as dependencies, and the box itself doesn't really do anything except hold it all together.)

Now, if you want to remove one of those components, well, you have to remove the k/x/ubuntu-desktop package too, because officially it's dependent on the component you're discarding. But really all that happens is that you're being forced to throw out the "box".

Feel free to dis my analogy, by the way.

---

### Post by dvarsam on 2006-06-04
[QUOTE=pierre.s.rosen]dvarsam:

You are missing some packages.  You need to install those packages that you cut and pasted above.  Those packages will be installed if you install most of the optional software listed in the Ubuntu Desktop Guide ([http://help.ubuntu.com/ubuntu/desktopguide/C/index.html](http://help.ubuntu.com/ubuntu/desktopguide/C/index.html) ) and the packages for Restricted Formats.[/QUOTE]

Dear "pierre.s.rosen",

Could you please tell me the _exact_ names of the packages I need to install?

Cause the above URL you suggested, contains dozens of links & it is impossible to locate & confirm which packages listed in there, apply to my case...

Thanks.

---

