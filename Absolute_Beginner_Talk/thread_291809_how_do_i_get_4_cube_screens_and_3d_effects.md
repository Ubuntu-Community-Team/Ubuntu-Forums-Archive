---
title: "how do i get 4 cube screens and 3d effects?"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by noktekniq on 2006-11-03
so i recently was browsing youtube and i found this video on linux ubuntu that allowed users to have these cool 3d type graphix with like 4 cube display. the video that i found was here [http://youtube.com/watch?v=V1iet8MWJr8](http://youtube.com/watch?v=V1iet8MWJr8)

where do i found the programs to install'? are their good places where i can go to get howto's and direct installation help? i'm running on 7800gt. a64 based computer. 

thanks for the help.

---

### Post by moffa on 2006-11-03
You need to install compiz and xgl and set them up.  There should be a sticky somewhere.  Try [http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

---

### Post by 23meg on 2006-11-03
You're looking for Beryl or Compiz. Check [this]("http://www.ubuntuforums.org/showthread.php?t=263851") out if you're using Edgy.

---

### Post by noktekniq on 2006-11-03
yeh i'm using edgy


i was looking at the how to.
but when i get to this section

> STEP 4: Enable compositing in X

This next section is from: [http://www.nvnews.net/vbulletin/showthread.php?t=77030](http://www.nvnews.net/vbulletin/showthread.php?t=77030)

in /etc/X11/xorg.conf (Remember to back it up again just incase)

Add this to Section "Screen"
Code:

# Enable 32-bit ARGB GLX Visuals Option "AddARGBGLXVisuals" "True" # If you are using an older version of compiz that # does not support rendering into the Composite # Overlay Window, you will need to disable clipping # of GLX rendering to the X Root window with this # option, or you will get a blank screen after # starting compiz: # Option "DisableGLXRootClipping" "True"


how do i do this? i don't understand this part. where do i go to enter this information?

---

### Post by Peepsalot on 2006-11-03
look more closely at the instructions.

it is saying you have to edit this file: "/etc/X11/xorg.conf"
open it in a text editor(you'll need admin priviledges so use sudo), and find that section marked as "Screen".  depending on the text editor, you can probably use some searching function to help get to that section quickly.

---

### Post by noktekniq on 2006-11-03
so do i type sudo /etc/X11/xorg.conf ? in the terminal?
or ? i'm new to ubuntu so i don't really know where i find all these stuff.

---

### Post by noktekniq on 2006-11-03
bump the thread. need a bit mroe help on the above. thanks

---

### Post by marx2k on 2006-11-03
type 'sudo gedit /etc/X11/xorg.conf' and make the necessary changes

you might want to back up the file first 'sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak'

---

### Post by noktekniq on 2006-11-03
thanks for the reply. i will try it out when i boot into linux

---

