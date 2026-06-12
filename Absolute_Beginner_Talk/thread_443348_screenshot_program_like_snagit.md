---
title: "screenshot program like snagit"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by afonit on 2007-05-14
is there a screenshot program on ubuntu where you can select an area on your screen to be in the screenshot?


it is a behavior similar to the program snagit on windows

---

### Post by heimo on 2007-05-14
I just tried ksnapshot for very first time, and its Region Capture Mode seems to do what you want.

---

### Post by oilchangeguy on 2007-05-14
go to applications, accessories, take screen shot. (not sure if you can set it to take a shot of anything but the entrie screen)

---

### Post by Dr Small on 2007-05-14
```
gnome-panel-screenshot --window --delay=5
```
Will take a screenshot of the present window, with a delay of 5 seconds to give you time to get to the window.

Dr Small

---

### Post by mcduck on 2007-05-14
Print Screen will capture the whole desktop, and Alt+Print Screen captures current window. I don't know if there's any screenshot utility for Gnome that would allow you to select a region of screen..

---

### Post by digital_k on 2007-05-20
There is a program available called Desktop Data Manager.  You can take selected areas as screen shots, etc. Its very handy. 

[http://data-manager.sourceforge.net/]("http://data-manager.sourceforge.net/")

---

### Post by RedSquirrel on 2007-05-20
You can also install imagemagick.

```
sudo apt-get install imagemagick
```Then run (from the command line):

```
import screen.jpg
```Your mouse cursor will change to crosshair and you can click-and-drag to select the portion of your screen you want to capture.

Run

```
import -help
```to see all of the fancy options you can use. You can change the file type simply by changing the filename suffix, i.e., "import screen.jpg", "import screen.png" etc.

---

