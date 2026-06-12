---
title: "possible to delete NTFS partition"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by gwash on 2006-02-02
I have an windows partition that I would like to delete thru unbutu...its the first partition

possible??

---

### Post by earobinson on 2006-02-02
yup just use gparted, you can install it using synaptic.

---

### Post by milstead on 2006-02-02
Yes it is possible.
Just use a partition tool like qtparted and delete it.
This will have side effects though, e.g. device numbers will change. e.g. /dev/hda2 will become /dev/hda1.
Grub might need reconfiguring otherwise ubuntu might become unbootable although you can usually recover from this.

---

### Post by gwash on 2006-02-02
[QUOTE=earobinson]yup just use gparted, you can install it using synaptic.[/QUOTE]

ok.  now I'm lost..can someone explain synaptic?  sorry, real newbie here, only a week into my linux edumacation :D

---

### Post by earobinson on 2006-02-02
synaptic is a tool that can be used to install programs, its in your menu under system -> admin (I think dont use gnome)

or in the terminal, you can type "sudo synaptic" to run the program.

You could also use the command "sudo apt-get install gparted" in the terminal to install gparted.

---

### Post by gwash on 2006-02-02
I get an error message, i think..

"Couldn't find package gparted"

---

### Post by aysiu on 2006-02-02
Here's a tutorial on Synaptic: [http://www.psychocats.net/essays/winuxinstall.php](http://www.psychocats.net/essays/winuxinstall.php)

Just substitute *gparted* for *blender*

And, if you're using Ubuntu/Gnome (as opposed to Kubuntu/KDE), go to System > Administration > Synaptic Package Manager.

---

### Post by Razorback on 2006-02-02
Also, make sure you update your repositories so you have accesss to the latest and greatest programs.
Look at aysiu's signature.  It is the first how-to.

---

