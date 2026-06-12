---
title: "Simple Bash Script Assistence"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by RKCole on 2007-12-18
Hello, everyone.

I am on vacation back home in Ohio.  I have a friend here who si visually impaired like myself.  He has a computer which was purchased for him by the government (he is a veteran who lost his sight due to previous war experience), so he is not (apparently) allowed to make any modifications to his computer (such as replacing Windows with Ubuntu, which is what he wishes to do) for two years.  For the time being he wants to experiment with Ubuntu via the live CD (v7.10).  I am working on a script which will set things up so that the system will be usable for him. 

Here is the script; this would be run from a USB flash drive which would have the files which are copied stored in the same directory. (please keep in mind that I have very little scripting experience):

```

#!/bin/bash
sudo cp ./ezoom.xml /usr/share/compiz/ezoom.xml
sudo chown root:root /usr/share/compiz/ezoom.xml
compiz --replace
cp ./bookmarks.html /home/ubuntu/.mozilla/firefox/*.default/bookmarks.html

``` 

So, this script does the following:

1)  Replaces /usr/share/compiz/ezoom.xml with the modified version of the file.
2)  Changes the owner of the file to root so that it will be recognized by the system.
3)  Restarts compiz so the change made will take effect.
4)  Copies my friend's bookmarks.html file to the .mozilla/firefox/*.default directory.

I'm trying to make this as automated as possible because my friend is quite inexperienced with computers, but step number 4 is a bit of a hassle.  See, I have discovered that the ~.mozilla directory is not created until Firefox is started for the first time. So in order for the bookmarks file to be successfully copied over, Firefox would have to be started and then shut down just so that the .mozilla directory would be created.  Is there any way to further automate this so taht Firefox would not have to be opened and then closed?  I've already tried making a copy of a created .mozilla directory, but it si overwritten when Firefox si started.

Any suggestions on this would be greatly appreciated.

Thanks, everyone.

Take care.

---

### Post by hyper_ch on 2007-12-18
You could do it more easily:

(1) save on the usb flash drive following files

--> /home/ubuntu/.mozilla/firefox/profiles.ini
--> /home/ubuntu/.mozilla/firefox/PROFILE.default/bookmarks.html

The profiles.ini file contains also the right path to the PROFILE.default folder. Just be sure to name it correctly.

(2) copy both files back (and not just the bookmarks.html)


OR

Why not having the whole firefox profile on the usb flash drive? You could symlink it

```

#!/bin/bash
sudo cp ./ezoom.xml /usr/share/compiz/ezoom.xml
sudo chown root:root /usr/share/compiz/ezoom.xml
compiz --replace

# Delete existing firefox folder
rm -Rf /home/ubuntu/.mozilla/firefox
# Creat symlink to flash drive
sudo ln -s /path/to/firefox/folder/on/flashdrive /home/ubuntu/.mozilla/firefox

```

---

### Post by RKCole on 2007-12-18
Hello, hyper_ch.

I actually tried this last night. Unfortunately, the .mozilla directory is not created on the Live CD session until Firefox is initially started on the Live CD.  I was just curious as to whether or not it is possible to create the .mozilla directory and copy the bookmarks over without having to start and then shut down Firefox.  Right now the procedure woudl be to:

1)  Start Firefox after teh Live CD is up and runing
2)  Shut down Firefox (these two would ensure that the .mozilla directory would be created)
3)  Run the script to set everything up and copy over the bookmarks
 If this cannot be done, it should not be that big of a problem.

Thanks for the help on this one.

Take care.
I was just trying to see fi there is any way to bypass steps 1 and 2. :)

---

### Post by hyper_ch on 2007-12-18
why don't u just manually create the .mozilla folder and symlink it?

---

