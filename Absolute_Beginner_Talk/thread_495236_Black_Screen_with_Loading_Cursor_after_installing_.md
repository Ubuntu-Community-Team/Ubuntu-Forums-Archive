---
title: "Black Screen with Loading Cursor after installing new cursor scheme"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by snwbord2456 on 2007-07-07
I tried to install an alternative cursor scheme and after rebooting I got a black screen with the default cursor stuck in loading.


Scheme link:

[http://gnome-look.org/content/show.php/Silver+XCursors+3D?content=5533](http://gnome-look.org/content/show.php/Silver+XCursors+3D?content=5533)


I moved both files to my desktop and after entering:

cd
cd Desktop
cp Silver ~/.icons

I got

cd: Omitting director Silver (I think...I don't really remember)

Then I did

cp default ~/.icons

and got the same omitting response.

Then I rebooted and got the black screen with the loading cursor.

I entered the virtual terminal and did

rm -rf ~/.icons/Silver/
rm -rf ~/.icons/default/

now the only thing in my .icons folder is

glass-icons

which is a folder scheme and has been installed since yesterday and has worked fine with other installations and reboots.

---

### Post by overdrank on 2007-07-07
Hi In the instruction it says you can modify your xorg to stop the cursor from blinking did you and by the way it doesn't help making a new thread about the same problem. :(

---

### Post by snwbord2456 on 2007-07-07
Are you talking about the change to the XF86Config file? I don't know where I would locate it, I went to:

/dev and tried

cd /XF86Config

but it says that no file or directory exists. I also have an ATI card.


Sorry, it gets really frustrating though when you go unanswered for hours I will stop though.

---

### Post by overdrank on 2007-07-07
> **snwbord2456 said:**
> Are you talking about the change to the XF86Config file? I don't know where I would locate it, I went to:

/dev and tried

cd /XF86Config

but it says that no file or directory exists. I also have an ATI card.


Sorry, it gets really frustrating though when you go unanswered for hours I will stop though.

I understand your frustration, we all don't have all the answer. I would suggest to your just to reconfigure your xorg but I really dont think it will help.

---

### Post by snwbord2456 on 2007-07-07
So am I screwed as far as this goes, or how would I configure my xorg file?

---

### Post by overdrank on 2007-07-07
> **snwbord2456 said:**
> So am I screwed as far as this goes, or how would I configure my xorg file?

When you boot and see the grub loading use the ctrl,alt,F1 keys all at the same time and this will bring you to the terminal, login and then use the command
```
sudo dpkg-reconfigure xserver-xorg
```
I really hope this helps. :(

---

### Post by snwbord2456 on 2007-07-07
It messed up the drivers cause I have an ATI card and I got the no screens error when I first installed ubuntu because of the ATI drivers. I'm going to fresh install windows and set up a partition for ubuntu which is something I'm alright with, it'll just take a while, if anyone knows how to install the cursor theme safely it would be nice if I could get a step-by-step on how to do it after I reinstall both OSs

---

