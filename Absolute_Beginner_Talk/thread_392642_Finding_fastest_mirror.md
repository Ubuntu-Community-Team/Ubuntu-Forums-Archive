---
title: "Finding fastest mirror"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by kpk108 on 2007-03-24
There were several email threads before asking how to find the fastest ubuntu download mirror. Following works in Feisty Fawn, 7.04:

1. Click on "System | Administration | Software Sources"
2. Under "Ubuntu Sotware" tab, choose "Other" in the "Download from" list box.
3. Choose your country and then click "Select Best Server" and choose the recommendation.

This automatically updates the sources.lst file.

The same utility can also be reached from the Synaptic Package Manager, through "Settings | Repositories". Not sure what the cmd line equivalent of this utility though.

---

### Post by mozzo on 2007-10-13
This method just set my source back to the official U.S. Ubuntu mirror.

I was suspicious that it might not be the fastest for me, so I investigated further with netselect and the mirror list at [http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors).

I wrote up a shell script to automate it.  Anyone who's interested can get it [here]("http://tinker.studiomozzo.com/ubuntuns").

---

