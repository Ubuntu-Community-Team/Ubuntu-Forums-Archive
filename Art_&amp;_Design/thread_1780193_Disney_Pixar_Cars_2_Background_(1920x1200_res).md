---
title: "Disney Pixar Cars 2 Background (1920x1200 res)"
date: 2011-06-11
forum: Art &amp; Design
---

### Post by shreepads on 2011-06-11
Hi Folks

Got all the Cars 2 wallpapers from the official site and packaged as a background where the image changes every minute.

Of course, the images are copyright of Disney/ Pixar, as mentioned on the images themselves.

**Instructions: (EDIT: See next post for another method that doesn't need sudo or the command line)**

1. Unzip the zip contents (images and xml file) to a folder

2. Create a new folder 'cars2' in /usr/share/backgrounds

```
cd /usr/share/backgrounds
sudo mkdir cars2
```

3. Copy the images and xml file into the new cars2 folder

```
cd /location/where/files/unzipped
sudo cp * /usr/share/backgrounds/cars2
```

4a. Right click on the desktop, choose 'Change Desktop Background'.
4b. Click 'Add...' button.
4c. Navigate to the /usr/share/backgrounds/cars2 folder. 
4d. In the dropdown just above the 'Open' button, choose 'All Files'
4e. Select the xml file 'background-2.xml' in the list view, hit 'Open'

5. Your background is ready to go!

Immediately after step 1, you could open the xml file 'background-2.xml' with gedit and mess around with the transition times if you want. Or change the order or the number of photos that appear, though this is a little more tricky.

Turns out the file is too large to upload here, so have stored it on this 3rd party server.

[https://rapidshare.com/files/177683028/cars2background.zip](https://rapidshare.com/files/177683028/cars2background.zip)

Hit the 'Free Download' button near the right bottom after opening the above mentioned link. Need to wait for around 5 mins (unless you have a Rapidshare account) and then click 'Download Now'...

To make sure you get the correct file, please check the md5sum as below after downloading:

```
~$ md5sum cars2background.zip 
a517eeeca7a672c4fa5b40c5260e049d  cars2background.zip
~$
```

---

### Post by shreepads on 2011-06-12
Another method, that doesn't require sudo or the command line.

- After Step 1 in the first post, open the xml file 'background-2.xml' with gedit.
- Find-Replace all occurrences of '/usr/share/backgrounds/cars2' with '/location/where/files/unzipped'
- Browse through the edited file and check the path to the image files is corect
- Save and close

Now jump to Step 4a in the first post. At Step 4c navigate to the folder where the files were unzipped and then choose the xml file edited above.

Another good thing of this option is that you can edit the xml or image files and they will take effect right away.

---

### Post by desktorp on 2011-06-12
Seems like I can't buy a box of cereal without seeing an ad for this movie.  Now this?!  Nooooo..  

*downloads and installs*

---

### Post by shreepads on 2011-06-26
OT but... Finally saw the movie, much recommended, esp for adults. Kids might lose interest after a while though :-)

---

