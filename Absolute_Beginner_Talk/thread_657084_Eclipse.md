---
title: "Eclipse"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by Long_Live_Linux on 2008-01-03
Ok, I figured out how to install eclipse on ubuntu 7.10, but how do I run it? Where the heck did I install it? Why doesn't Ubuntu make a shortcut of the program to the desktop like windows? Please someone help me! 

Also, how do I run Aircrack-ng on ubuntu? I installed it, but how do I run it?

---

### Post by jordilin on 2008-01-03
> **Long_Live_Linux said:**
> Ok, I figured out how to install eclipse on ubuntu 7.10, but how do I run it? Where the heck did I install it? Why doesn't Ubuntu make a shortcut of the program to the desktop like windows? Please someone help me! 

I would download eclipse directly from its webpage and not from the repositories. You will get a file like eclipse-java-europa-fall2-linux-gtk.tar.gz, then untar it (tar -xzvf file) and you will get a directory with the name of eclipse. Go into it and execute ./eclipse to get the app up and running. Doing a shortcut or link to your Desktop is as easy as dragging the eclipse file to your Desktop while mantaining the Ctrl+Shift keys pressed.

---

### Post by Fixman on 2008-01-03
> **Long_Live_Linux said:**
> Ok, I figured out how to install eclipse on ubuntu 7.10, but how do I run it? Where the heck did I install it? Why doesn't Ubuntu make a shortcut of the program to the desktop like windows? Please someone help me! 

Also, how do I run Aircrack-ng on ubuntu? I installed it, but how do I run it?

Have you installed it from the repos? Its always the safer way to install things. To install eclipse from them, you can:

a) Applications->Add remove->Eclipse (does not work for all programs)
b) system->Administration->Synaptic (does work with all)
c) applications->accesories->terminal, and write sudo aptitude install eclipse (the fastest)

Once you do one of these three, it downloads it and install it automatically. You can find a shortcut to eclipse on applications->programming->eclipse, or you can right-click it and select "add to desktop".

---

### Post by lswest on 2008-01-03
word of warning, as i did this, be sure to install sun-java-1.6 as well, or else eclipse will install 1.5 which uses the old input method, instead of Scanner.

---

### Post by jordilin on 2008-01-03
> **Fixman said:**
> Have you installed it from the repos? Its always the safer way to install things. To install eclipse from them, you can:

a) Applications->Add remove->Eclipse (does not work for all programs)
b) system->Administration->Synaptic (does work with all)
c) applications->accesories->terminal, and write sudo aptitude install eclipse (the fastest)

Once you do one of these three, it downloads it and install it automatically. You can find a shortcut to eclipse on applications->programming->eclipse, or you can right-click it and select "add to desktop".

Eclipse is one of those apps that is standalone and you do not perform any installation if you download the package from the official eclipse repos (just untar and voila). From eclipse website you will always get the latest and greatest eclipse ide. In any case, it is up to the first poster.

---

