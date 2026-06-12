---
title: "a few questions around Wine, Compiz Fusion, Newsgroups and VLC media player"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by iamthenoob on 2008-04-02
Well i am getting there slowly but surely.

I now have a working install with the correct resolution 

I have got most of the stuff i want working for compiz fusion but there is one thing i would like to know how to do which is how to zoom in and out when you are rotating a cube. I have seen various videos where they go to the rotate cube bit with 3d windows and they can zoom in and out away from the cube to see all the windows etc.

Second question is around installing applications in Wine. Is there a good sticky or guide on using Wine as i think i may want to use newsbin because of a couple of features i dont think i have in Pan. which brings me onto 

Pan. is there any way for me to make it act in a very similar way to newsbin by grouping binary posts by name so i can in 1 click download a full set of files instead of having to click them one at a time.

Basically i want newsbin and i dont think i would be happy with anything less. Can i get Pan to act like newsbin or is that askign to much?

other question is how to make VLC media player play network files. i currently have a windows box with all my files on which i want to keep that way but VLC will not play any of these network files it seems to onloy want to play local ones. 

Last but not least for general useability i think the standard file explorer window is pretty crap. what do you use and what would you suggest i use. + how do i setup my mouse so that the back and forward buttons actually do that job instead of pasting etc

Thanks

T

---

### Post by forrestcupp on 2008-04-02
About the cube.  Go to System->Preferences->Advanced Desktop Effects.  In there, you should find a plugin called 'Rotate Cube'.  Click on that and in there is a setting for zoom.  You can't dynamically change the zoom, but you can set how far out the cube is zoomed when you are rotating it.  If you don't have an entry for Advanced Desktop Effects, you still need to install it.  It isn't installed by default
```
sudo apt-get install compizconfig-settings-manager
```

About installing things with Wine.  If Wine is installed, you can use it one of two ways.  From a command line, you can **cd** to the directory where the Windows program is that you want to run and type
```
wine ./*programname*
```
substituting the name of the program.  Or you can navigate to it in your file browser, right click on the file and set it to open exe's with wine.  Then you can double click exe's and they will run.  Be advised that not every Windows app will just run on Wine.  Some programs *will* run, but they require tweaking.  A good source for this info is [the app database](http://appdb.winehq.org/) at Wine's official site.

About your file browser.  The default browser in Gnome is Nautilus.  It's not really any worse than Windows Explorer, but if you don't like it, there are a few other choices.  A couple of popular ones are Thunar, which is used with Xfce, and Dolphin, which is the new one in KDE4.  You can install either of those from the repos, and they will both work in Gnome.

---

### Post by Odd-rationale on 2008-04-02
#1: To get 3dwindows effect when you rotate cube, you will have to install extra plugins. Here is an easy way to do that: [http://ubuntuforums.org/showthread.php?t=620000](http://ubuntuforums.org/showthread.php?t=620000)

For more information on how to make compiz-fusion look better see [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

#2 First check the wine appdb to see if your application can be installed using wine: [http://appdb.winehq.org/](http://appdb.winehq.org/)

For general direction on using wine see [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

As for #3 and #4, I don't use either Pan or VLC. So I can't be of much help there.

EDIT: and as forestcupp stated above, make sure you have compizconfig-settings-manager

---

