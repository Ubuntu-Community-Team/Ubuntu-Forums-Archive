---
title: "Installing Beryl (No Internet/Intel Video Card i810)"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by Palko17 on 2007-02-17
Okay, here it goes. Normally I don't ask forums for help (to skip me blabbing go to "The Problem"), but I am making an exception. After googling all day, getting billions of results, I find nothing. I am nearing the part where I lose focus on my goal and resort to Windows.


I really am impressed with the 3D Cube desktop, but not only is it impressive, but it is something I have never seen before. I spent an entire day because when I want something I go after it with all that I know. I have exhausted, confused, and mentally worn myself to the limit. Now I come with you ^_^

----- The Problem -----

**Keep in mind:**
- I have *no* internet connection.
- I have no experience in Ubuntu 6.10, except the experience I have gained today. I installed Ubuntu **today.**
- I have no life, oh wait scratch that, because of Ubuntu I *now* have no life.
- I am running a Intel i810

What I don't understand... is... well... everything. I have found plenty of useful tutorials, but I am sure they all require the internet. The one on the Beryl wiki, [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu#Ubuntu_6.10_.28Edgy_Eft.29](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu#Ubuntu_6.10_.28Edgy_Eft.29) would help me  a lot, but I am sure you have to have a net connection . . .

Can anyone please give me the short answer that doesn't exist? I also appreciate any help, thank-you!

---

### Post by nonewmsgs on 2007-02-17
there's a link with some info here, mate,

[http://www.ubuntuforums.org/showthread.php?t=349732](http://www.ubuntuforums.org/showthread.php?t=349732)

---

### Post by Palko17 on 2007-02-17
Thank-you! I shall proceed on my nearly never ending, adventure.

>  Intel

Install 3D enabled drivers.
file.pngCode:

sudo nano /etc/X11/xorg.conf


Add to Section "Device":
file.png File:/etc/X11/xorg.conf

Option "XAANoOffscreenPixmaps" "true"

and at the end of the file:
file.png File:/etc/X11/xorg.conf

Section "Extensions"
Option "Composite" "true"
EndSection



On that page, [http://doc.gwos.org/index.php/BerylOnEdgy#Intel](http://doc.gwos.org/index.php/BerylOnEdgy#Intel), I get the above for Intel. Some how I think there is more to it than that...

---

### Post by psycosmyth on 2007-02-17
[http://pclinuxos.com](http://pclinuxos.com)

shhhh...I said nothing:rolleyes: :-\"

---

### Post by Palko17 on 2007-02-17
I <3 You!

---

