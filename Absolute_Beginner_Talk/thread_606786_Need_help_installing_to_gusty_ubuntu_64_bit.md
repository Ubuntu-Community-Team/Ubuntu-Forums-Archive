---
title: "Need help installing to gusty ubuntu 64 bit"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by bluespider on 2007-11-08
Hello, I need help to install this   [http://www.graphicall.org/builds/builds/showbuild.php?action=show&id=529](http://www.graphicall.org/builds/builds/showbuild.php?action=show&id=529)   to gutsy ubuntu 64 bit, and I have no idea how to do it, I have only been using Ubuntu for a few days and do not know how to install programs which are not in the regular depositories, Could someone help me do this? Thank you.

---

### Post by Paul820 on 2007-11-08
Hi, first open a terminal and type or copy and paste this into it
> sudo apt-get install libsdl1.2debian-all nautilus-open-terminal
Then press Ctrl+Alt+Backspace to log out and back in so that nautilus-open-terminal appears in your context menu. Nautilus-open-terminal just allows you to open a terminal from whatever folder you happen to be in. It saves typing the path to where you are. 

Extract the folder that you downloaded that contains blender, into your home folder. Open the folder so you see the blender icon, now right click( not on the icon, on an empty space ) and select 'open in terminal'. Now copy and paste the command from that website into the terminal and press enter:
> export SDL_AUDIODRIVER=alsa && ./blender -g noaudio
Blender should start, don't close the terminal otherwise you will close blender at the same time. I will try to figure out how to make a shortcut from the main menu, it's having non of it a the moment because of the command required to run blender. For now you should save that command to a txt file until i can the shortcut thing going.

You should already have python 2.5 so you are good to go....:)

---

### Post by bluespider on 2007-11-08
Hello, I think I did everything you said but it didnt  work Im not to sure what you ment by home folder though but I went to the folder that has the same name as my account and put the file in there and did everything you said but blender does not open .


Ok forget what I just said I just tried it again an it  did open a blender but not that one I can tell because it opened my old blender with its default settings ..I dont even know where ubuntu keeps it either I tried to uninstall it but it  must still be somewhere because it keeps opening that one.

---

### Post by Paul820 on 2007-11-08
Ok, go inside the folder where blender is and open the terminal, right click and open the terminal if you installed nautilus-open-terminal, and type
> ./blender
If it doesn't start there will be some error messages in the terminal, what are they? Copy and paste them here.

---

### Post by Paul820 on 2007-11-08
To completely remove the old blender, copy and paste this in the terminal
> sudo apt-get --purge remove blender

---

### Post by bluespider on 2007-11-08
Ok I did that and it still keeps opening some other  old blender  here is what was in the terminal window 


a@a-desktop:~/Blender 2.45.7 (AMD64 SSE2)$ ./blender
guessing './blender' == '/home/a/Blender 2.45.7 (AMD64 SSE2)/./blender'
Compiled with Python version 2.5.1.
Checking for installed Python... got it!

Blender quit
a@a-desktop:~/Blender 2.45.7 (AMD64 SSE2)$

---

### Post by Paul820 on 2007-11-08
Well by the looks of the terminal output it is opening the correct one. What makes you think it's the other version that is being opened?

EDIT: If it was opening the old blender then the ouput will be like this: guessing 'blender-bin' == '/usr/bin/blender-bin'
the new one will use the old blender preferences that are stored in the hidden folder inside your home folder. Find it and delete it, go to your home folder and press Ctrl+h, then look for the folder named .blender and delete it and try to run the new blender again.

---

### Post by bluespider on 2007-11-08
In blender you can set up a number of different options so it always opens with those options, so you can tell when it opens up if it opens with your preset options, and when it opens it is definatly  my old blender it even remembers  the last few files I worked on , which a new version wouldnt know . I dont know how its doing it , But the blenderI was using at first was on another drive a usb removable drive, I think that somehow it might be getting that one, because I removed all blender that was on ubuntu and deleted them from where ever I could find them. I even checked in the package manager no blenders in there.
By the way thanks for helping . Im going to try disconecting that usb drive an see what happens then. Maybe The changes dont take effect till I restart ?

---

### Post by Paul820 on 2007-11-08
If you read my post above it tells you what is happening. ALL your setting are stored in the hidden folder inside your home folder and the new blender is reading them. You have to remove that folder and start from scratch. All your setting are stored in there, lights, camera, theme, everything. I have an old blender from the repos and i am using a 2.45 build and both settings are exactly the same.

I don't mind helping you out. I know how frustrating some things can be. :)

---

### Post by bluespider on 2007-11-08
Ok I deleted Ubuntu and reinstalled it after writing zero's to  the drive.Then did a fresh install
When I get to the part in terminal when I put this in : export SDL_AUDIODRIVER=alsa && ./blender -g noaudio    


This is what I get 


./blender: error while loading shared libraries: libgettextlib-0.16.1.so: cannot open shared object file: No such file or directory

I dont know what any of that means....

Update   Well I got it working thanks for the help , much appreciated.

---

### Post by Paul820 on 2007-11-08
You did a clean install? :shock: You will have to get all the dependencies that blender now needs. You need to search synaptic for libgettextlib and install that, no doubt there will be a lot more that it needs. Here is a list of the dependencies that it needs, installing one of them will probably install several others along with it. You might have some of them to begin with so just keep installing and running blender until you have them all. It might seem like a lot of work but remember it's not installed through synaptic, so synaptic can't grab the dependencies for you.

---

### Post by Maestro23 on 2007-11-08
> **Paul820 said:**
> You did a clean install? :shock: You will have to get all the dependencies that blender now needs. You need to search synaptic for libgettextlib and install that, no doubt there will be a lot more that it needs. Here is a list of the dependencies that it needs, installing one of them will probably install several others along with it. You might have some of them to begin with so just keep installing and running blender until you have them all. It might seem like a lot of work but remember it's not installed through synaptic, so synaptic can't grab the dependencies for you.

Paul, he can also generate the dependencies for Blender by:

> sudo apt-get build-dep blender

Then go ahead and compile the source.

---

### Post by Paul820 on 2007-11-08
It's not the source he has though Maestro23, it's a prebuilt file that someone else has done. All there is is a 30Mb blender file to execute and a folder with plugins. There is nothing to build.

---

### Post by Maestro23 on 2007-11-08
> **Paul820 said:**
> It's not the source he has though Maestro23, it's a prebuilt file that someone else has done. All there is is a 30Mb blender file to execute and a folder with plugins. There is nothing to build.

Ah, ok.  He should still be able to satisfy the dependecies that way though.  Keep in from running it multiple times. :smile:

---

### Post by Paul820 on 2007-11-08
You're right, that command you gave will be a lot easier :) I never knew about that.

---

### Post by Maestro23 on 2007-11-08
> **Paul820 said:**
> You're right, that command you gave will be a lot easier :) I never knew about that.

Yeah, I found some great docs the other night as well as digging thru the **man** pages. :smile:

1. Aptitude:[https://help.ubuntu.com/community/AptitudeSurvivalGuide?highlight=%28Aptitude%29](https://help.ubuntu.com/community/AptitudeSurvivalGuide?highlight=%28Aptitude%29)
2. Apt-Get: [https://help.ubuntu.com/community/AptGetHowto?highlight=%28get%29%7C%28apt%29](https://help.ubuntu.com/community/AptGetHowto?highlight=%28get%29%7C%28apt%29)

---

### Post by Paul820 on 2007-11-08
Bookmarked, thanks :)

---

### Post by Maestro23 on 2007-11-08
> **Paul820 said:**
> Bookmarked, thanks :)

No prob man.  It's not about **knowing** everything... but knowing **where** to go.:guitar:

---

