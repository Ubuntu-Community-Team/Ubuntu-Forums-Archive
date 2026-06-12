---
title: "[SOLVED] Problems with windows manager in 7.10"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-09-01
I am running ubuntu 7.04 and 7.10 dual boot on my Gateway comp (specs at bottom of post). The 7.04 runs flawlessly, so thought I would give the 7.10 a try before it's release in Oct. The first few days everything went waaaayyy too smooth. Installation was fast and easy. All hardware worked first time, internet connection no problem, I was very impressed !! Then yesterday turned comp on and selected kernel 2.6.22-8-generic for 7.10 and it took about five minutes to get to the desktop. All windows that I open have no minimize or close tab in the upper right corner, I can't grab and move them either. They open in the upper left hand corner and that is where they stay until I go to file>close. Same when I open terminal. Went to System > Preferences > Windows and got error message in upper right of screen saying "Window manager "unknown" has not registered a configuration tool". Any ideas as to what might have happened ? I realize there will be problems with 7.10 up to and probably after the release date, just trying to get a little jump on things. Thanks for the help and interest.

---

### Post by Jimmyfj on 2007-09-02
You do not mention anything about your graphics card in your specs. But the way compiz is used in Gutsy is by default activation, meaning that you have the desktop effects set to normal on startup. This might not be the best for your graphics just yet. Try right-clicking on your desktop. Select "Change background" and tick the tab "Desktop Effects" - Here you deactivate the effects and your screen will flicker a few times while disabling the effects.

As for the kernal. I run 2.6.22.10 on my 7.10 Tribe 5 with nVidia graphics card. If you can't correct the error in your GUI try booting up in safe mode and update the system. Kernel for Gutsy should be 2.6.22.10 after an update. This kernel fits your graphics driver. Or it should fit it.

---

### Post by jerrynewt on 2007-09-02
Good deal -- did what you suggested and worked like a charm. This may sound silly but with my intel i810 graphics card will I not be able to use the desktop effects, or can I install the Nvidia drivers and get it to work that way ??

---

