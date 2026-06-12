---
title: "Sound won't work"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by Watchtow3r on 2007-12-30
I was trying to get the sound to work on my HP dv2000 following [this]("http://ubuntuforums.org/showthread.php?t=455147") guide, but step 4 isn't working for me... when I enter in "mkdir /home/user/alsa" I get a message saying "mkdir: cannot create directory `/home/user/alsa': No such file or directory".

how can I fix this? Please note that I just loaded ubuntu on my USB drive, and so the user still just says Live Session User (in the upper right hand corner of the screen next to the time and date). Thanks.

---

### Post by Watchtow3r on 2007-12-30
bump

---

### Post by Riffer on 2007-12-30
Try the "sudo" command, so it reads..

"sudo mkdir /home/user/alsa"

---

### Post by Watchtow3r on 2007-12-30
I did and I still got the same message.

---

### Post by Riffer on 2007-12-30
ok whats the folders in your "home" folder?  On mine I have no /home/user/ folder, what I have is my user login name for a folder.  I would use that folder name in the command line.

For instance if you log in as "alfred", the folder in you home folder should be named "alfred".  So the command in your terminal should read..

mkdir /home/alfred/alsa

I hope that helps

---

### Post by Watchtow3r on 2007-12-30
I don't have a folder saying anything like that... I do have a "public" folder

---

### Post by Watchtow3r on 2007-12-30
oh nvm I have a folder like that.

 
But, on step 7, I kept getting this message:

root@ubuntu:/home/ubuntu# cd alsa-driver-1.0.15rc3/
bash: cd: alsa-driver-1.0.15rc3/: No such file or directory

How can I fix this? Because I get this same message when trying to install the:
cd alsa-lib-1.0.15rc3 , cd alsa-utils-1.0.15rc1 and cd alsa-firmware-1.0.15rc1 files.

Also, in step 14, I don't even see a Recording tab.

---

### Post by Riffer on 2007-12-30
LOL now I'm confused... What is the contents of your home folder.   You would find that by going to the "places" drop down menu and clicking on "Home Folder"

---

### Post by Watchtow3r on 2007-12-30
My home folder has a folder marked jake (my username) and ubuntu (the live session user thing).

I think I solved the problem by just making it mkdir /home/jake/alsa (even though it didn't display any messages) but I'm still having some trouble with the next part)

---

### Post by Riffer on 2007-12-30
> **Watchtow3r said:**
> oh nvm I have a folder like that.

 
But, on step 7, I kept getting this message:

root@ubuntu:/home/ubuntu# cd alsa-driver-1.0.15rc3/
bash: cd: alsa-driver-1.0.15rc3/: No such file or directory

How can I fix this? Because I get this same message when trying to install the:
cd alsa-lib-1.0.15rc3 , cd alsa-utils-1.0.15rc1 and cd alsa-firmware-1.0.15rc1 files.

Also, in step 14, I don't even see a Recording tab.

The default for downloading files is to place them on your desktop.  Right now I'm wondering if step 6 even worked for you.  Is those files on your desktop?

---

### Post by Watchtow3r on 2007-12-30
sorry, in my post above, this: root@ubuntu:/home/ubuntu# cd alsa-driver-1.0.15rc3/     should say this: root@ubuntu:/home/jake# cd alsa-driver-1.0.15rc3/

---

### Post by Watchtow3r on 2007-12-30
> **Riffer said:**
> The default for downloading files is to place them on your desktop.  Right now I'm wondering if step 6 even worked for you.  Is those files on your desktop? 

No

---

### Post by Watchtow3r on 2007-12-30
although I do have a folder in my "jake" folder marked alsa with a bunch of that stuff

---

### Post by Watchtow3r on 2007-12-30
Now that you mention that, I think that the files all got downloaded and unpacked to the "alsa" folder under "jake" rather than the desktop.

---

### Post by Riffer on 2007-12-30
> **Watchtow3r said:**
> sorry, in my post above, this: root@ubuntu:/home/ubuntu# cd alsa-driver-1.0.15rc3/     should say this: root@ubuntu:/home/jake# cd alsa-driver-1.0.15rc3/

Ok this is where I get confused.  You should be in '/home/jake/alsa/', why you're in '/home/jake/' I have no idea.

From what I understand is that if you followed the code correctly you should have all the files you downloaded and the folders that you unarchived all in the '/home/jake/alsa/' folder, if thats the case then you need to get into that folder.. try 

cd /home/jake/alsa

Check to see if you 'tar.bz2 are there and that they have been unarchived.  In terminal you can use the 'ls' command for this.

---

### Post by Riffer on 2007-12-30
> **Watchtow3r said:**
> Now that you mention that, I think that the files all got downloaded and unpacked to the "alsa" folder under "jake" rather than the desktop.

LMAO great minds

---

### Post by Watchtow3r on 2007-12-30
hmm well I accidentally turned off my computer just now and when it turned back on I seemed to have sound. That's weird but it worked lol. Anyways thanks a lot for all your help.

---

### Post by Watchtow3r on 2007-12-30
Just out of curiosity : When I loaded the ubuntu live cd without the usb installed, I still had sound. I'm just wondering why this is, seeing as I thought the drivers were all installed on the usb drive.

---

