---
title: "Error after trying to install something that failed!"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by Literatka on 2006-11-03
Okay so I was trying to install flash player properly and I found a .deb file via another post on the ubuntu message board. So I download it but it says installing for some time so I canceled it and it's messed up my system now I get this error when starting up package manager:


E: The package flashplayer-nonfree needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

So...what should I do? I'm lost.

---

### Post by cantormath on 2006-11-03
completely uninstall it through synaptic and use AUTOMATIX2 to reinstall it.

---

### Post by jpeddicord on 2006-11-03
From Synaptic, go to Settings > Prefrences. On the Files tab, click Delete Cached Package Files. Close the prefrences, and find flash. Click on the package and hit reinstall. Now hit apply, and it should re-download and install Flash.

I don't know what to say about automatix for this solution, that is kind of trying to kill a fly with a gun. Automatix never really worked well for me; it had some unwanted side-affects (mplayer). But I haven't tried Ax2, so I guess I shouldn't say too much now. ;)

EDIT: Automatix2 is pretty nice, I take back what I said. :)

---

### Post by Literatka on 2006-11-03
> **jacobmp92 said:**
> From Synaptic, go to Settings > Prefrences. On the Files tab, click Delete Cached Package Files. Close the prefrences, and find flash. Click on the package and hit reinstall. Now hit apply, and it should re-download and install Flash.

I don't know what to say about automatix for this solution, that is kind of trying to kill a fly with a gun. Automatix never really worked well for me; it had some unwanted side-affects (mplayer). But I haven't tried Ax2, so I guess I shouldn't say too much now. ;)

EDIT: Automatix2 is pretty nice, I take back what I said. :)

I can't even find it in Synaptic, it doesn't exist there apparently. But I will try your suggestion anyway.

---

### Post by Literatka on 2006-11-03
I tried it but even looking in synaptic for anything I can't find it. :( Says: 0 packages installed in my Synaptic!

---

### Post by tuxcantfly on 2006-11-03
flashplugin-nonfree is what you're looking for. just enable the universe and multiverse repos

---

### Post by tuxcantfly on 2006-11-03
by the way, I hope you're using i386, because flash isn't available for powerpc, and getting it working on amd64 is hackish

---

### Post by Literatka on 2006-11-03
I am using i386. I know that's the plug-in I'm looking for, but I don't have any files in my synaptic.

[http://i74.photobucket.com/albums/i253/literatka_2006/Screenshot.png](http://i74.photobucket.com/albums/i253/literatka_2006/Screenshot.png)

Screen shot here.

[http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/](http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/) 

This is what I initally tried to install so now I am trying to re-install it.

---

### Post by podunk on 2006-11-03
There is a very nice easy to understand guide on installing things in Unbuntu here:
[http://monkeyblog.org/ubuntu/installing/#package_manager](http://monkeyblog.org/ubuntu/installing/#package_manager)

it's very graphical and it helped me a lot when i was new. You might want to bookmark it. :)

Once you follow that guide you will be able to search for Automatix 2 and about 20,000 other programs you can install just by pointing and clicking.

---

### Post by podunk on 2006-11-03
In the manager there are 4 buttons down on the bottom left. 
sections
Search
Status
custom

You have status clicked - change it to Search or Sections. Right now your status is zero because you haven't installed or uninstalled anything.

---

### Post by Literatka on 2006-11-03
> **podunk said:**
> In the manager there are 4 buttons down on the bottom left. 
sections
Search
Status
custom

You have status clicked - change it to Search or Sections. Right now your status is zero because you haven't installed or uninstalled anything.


Did that - nothing there still - 

[http://i74.photobucket.com/albums/i253/literatka_2006/Screenshot-1.png](http://i74.photobucket.com/albums/i253/literatka_2006/Screenshot-1.png)

---

### Post by Literatka on 2006-11-03
Well I tried to re-install and then just opened it in the terminal and canceld the installation and then the synaptic is back to normal, by just removing it.

---

### Post by user1397 on 2006-11-03
> **Literatka said:**
> Well I tried to re-install and then just opened it in the terminal and canceld the installation and then the synaptic is back to normal, by just removing it.try this in a terminal (applications > accessories > terminal): ```
sudo apt-get update && sudo apt-get install -f
```and then try reinstalling flash

---

### Post by user1397 on 2006-11-07
did that work for you?

---

