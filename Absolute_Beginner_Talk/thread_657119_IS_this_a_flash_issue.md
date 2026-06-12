---
title: "IS this a flash issue?"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by beanco on 2008-01-03
I am in the process of chaning ISPs,

and i had some questions so I went [[COLOR="DarkOrange"]to my new ISPs site[/COLOR]](http://home.datanet.hu) 

I cannot open the menues... they are supposed to be drop downs.. the first one is the one I need, 

I called the ISP and asked what's up, they say it is likely flash but cannot help me over the phone.... now if I weren't such a n00b I would have known kye jargon that would have gotten them to help me....

so, knowing nothing about flash I really do not know if 

1 this is a flash issue

2 what flash I have installed

3. what flash I should have installed


Thanks

Robi

---

### Post by philinux on 2008-01-03
The drop downs aren't flash cos I've got flash block on and I can see the pull downs. Maybe its java script. Have you got it enableb under Edit prefs content. Assuming your using firefox.

[edit] its java script cos if I uncheck it then pull downs dont work.

---

### Post by lswest on 2008-01-03
yea i checked out the site, the menu is a javascript file, the images are gifs.  best thing to do would be check if javascript is enabled on firefox.  (checked the source of the page)  turns out philinux checked at the same time:P

---

### Post by beanco on 2008-01-03
ok, will check soon

but I have been using epiphany and galeon too.. guess I have to check them

wierd that a techie at teh help desk would suggest flash.

robi

---

### Post by beanco on 2008-01-03
it is enabled in all three browswers!

robi

---

### Post by hyper_ch on 2008-01-03
can you play videos from youtube? If not, it's a flash issue...

---

### Post by dannyboy79 on 2008-01-03
if you're using gutsy, download the flash tarball from a terminal session by entering this command:

wget [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

this will save the file where ever you're located in the filesystem (most likely you're in your home directory. you can find out by issuing: 
pwd)

then, untar and ungzip it with this command

tar -xvvzf install_flash_player_9_linux.tar.gz

this will create a folder with the same name as above, "install_flash_player_9_linux"

I didn't use the installer with gutsy, something doesn't work with it. So I just copied the libflashplayer.so to these 2 folders: 
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/firefox/plugins/libflashplayer.so

So, the commands to copy it would be like this

sudo cp ~/install_flash_player_9_linux/libflashplayer.so /usr/lib/mozilla/plugins/
sudo cp ~/install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/

Now restart firefox and you should be able to watch youtube vides, that's how I check to make sure flash is installed. if that doesn't fix it, then you need java installed. that's another story.

---

### Post by dannyboy79 on 2008-01-03
if it's a java issue, then you'll need sun-java6-jre I believe.

---

### Post by milton1 on 2008-01-03
This is an issue with flash in firefox. I have seen it many times, and do not know how to fix it. The menu is working correctly, but it being obstructed by the flash graphic. One workaround: konqueror seems to display the site perfectly.

---

### Post by philinux on 2008-01-03
> **dannyboy79 said:**
> if it's a java issue, then you'll need sun-java6-jre I believe.

Its a java script issue.

---

### Post by lswest on 2008-01-03
i agree, there is no flash on that page, the gif's should display fine, and the rest is a javascript file.

---

### Post by philinux on 2008-01-03
Oh no. Look at these - first one shows drop downs but I have flash block on.

Second one is where I've let the flash play and it hides the drop downs. Mmmmm.

---

### Post by milton1 on 2008-01-03
> **lswest said:**
> i agree, there is no flash on that page, the gif's should display fine, and the rest is a javascript file.

The giant image in the center of the page is a flash object.

---

### Post by lswest on 2008-01-03
you're right, sorry didnt bother check the source further past the menu, assumed the image would just be, you know, an image:P

---

### Post by milton1 on 2008-01-03
> **lswest said:**
> you're right, sorry didnt bother check the source further past the menu, assumed the image would just be, you know, an image:P

No problem. Sometimes the big obvious things right in front of us are the hardest to see. :)

Sadly, this type of flash imaging and the resultant blocking of menu items is becoming very popular. It causes no problems on IE, so the developers tend to ignore it.

---

### Post by beanco on 2008-01-03
well I do not and will hopefully never have IE!!!

I am still on Feisty!

So, what should I do?

robi

---

### Post by philinux on 2008-01-03
Well if you install the addon 

flashblock for firefox at least you'll get the pull downs.

---

### Post by WearZeeP on 2008-01-03
Well, its a problem of the website, not on your side, so if you really need to go to a mane item, you could just check the source and see where the menu options is linked, and then go there manually.
Either that, or you could turn off flash while you visit the site, or get adblock plus add-on for Firefox and block the big annoying flash image.

Edit: oh, didn't see philinux's post when i posted :P

---

### Post by FuturePilot on 2008-01-03
Yes, it's a Flash issue. Adobe doesn't seem to want to find a way to get WMode Transparency to work on Linux. ](*,)

---

### Post by milton1 on 2008-01-03
> **beanco said:**
> well I do not and will hopefully never have IE!!!

I am still on Feisty!

So, what should I do?

robi

As previously stated: Try konqueror; it displays this site just fine, flash, menus and all.

---

### Post by hyper_ch on 2008-01-03
I see the problem now. With firefox in linux the menus are opened BEHIND the flash... the second menu from the left is longer than the flash and you will see it appearing at the bottom.

---

### Post by philinux on 2008-01-03
Correct and very odd. But thats browsers for you.

And +1 for Konqueror

---

### Post by beanco on 2008-01-03
well konqueror is fine but i already have 3 browsers and not in the mood for 4th.

how do i check the source and manual go to the item in the menu?


Thanks

Robi

---

