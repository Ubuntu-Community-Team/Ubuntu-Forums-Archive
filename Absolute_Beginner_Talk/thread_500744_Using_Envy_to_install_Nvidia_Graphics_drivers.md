---
title: "Using Envy to install Nvidia Graphics drivers"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by beastrace91 on 2007-07-14
When using the Envy program to install my Nvidia graphics drivers (This link : [http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_1](http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_1)) when I get to step 6 and I open the file to put the code into I get the following message when I try to save the file : Window Labeled: Error - Kate

The window reads:
The document could not be saved, as it was not possible to write to file.///j3ff/share/applications/NVDIA-Settings.desktop.

Check that you have write access to that file or that you have enough disk space available.

I know I have enough disk space so I guess my real questions is how do I give myself write access?

Any input welcome,
~J3ff

---

### Post by mills on 2007-07-14
did you open the file with root privileges?

sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

---

### Post by beastrace91 on 2007-07-14
Meh I got it working, I ended up saving the file to a different dir and then sudo cp the file to the folder it needed to go into.

~J3ff

---

