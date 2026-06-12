---
title: "installing Ubuntu-Studio Theme"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by jaywee on 2007-05-11
Ubuntu Studio is a multimedia editing/creation flavour of Ubuntu. It’s built for the GNU/Linux audio, video, and graphic enthusiast or professional. Because I don’t do audio, video and graphic editing or creation, so I didn’t install Ubuntu Studio. But from the screenshot, I really like the theme that is used by Ubuntu Studio. So I decide to install the theme into my Feisty Fawn.

1. Edit /etc/apt/sources.list and put this line:

    deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main

2. Get the gpg for that repo

    $ wget [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add -

3. Run

    $ sudo apt-get update

4. If you want to install all the themes that is used in Ubuntu Studio, including gdm theme, wallpapers, icon theme, session splashes and gtk theme use this

    $ sudo apt-get install ubuntustudio-look

I didn’t installed gdm theme and session splashes so i did this:

    $ sudo apt-get install ubuntustudio-theme ubuntustudio-icon-theme ubuntustudio-wallpapers

---

### Post by infidel on 2007-05-12
Hi, jaywee. I appreciate the tutorial, as I caught a screenie of the Studio theme elsewhere and wanted to give it a try.

I followed your instructions to the letter, and everything installed without incident -- but the theme doesn't appear in my System > Preferences > Theme. All of the relevant files appear to be where they are supposed to be.

Can you offer any guidance as to what I'm probably overlooking? Many thanks in advance.

---

### Post by seshomaru samma on 2007-05-12
I think you will find it in the theme 'details'
go to themes . click on any theme and choose 'theme details' you will be able to see ubuntu studio controls and ubuntu studio icons and window borders

---

### Post by infidel on 2007-05-12
Ah! Yes, indeed. There's everything I need.

It turns out that I don't like the theme much after all. :)

Thanks!

---

### Post by Campingman on 2007-05-12
It is all a bit dark!

---

### Post by deadgobby on 2007-05-12
The sever is down

---

### Post by Campingman on 2007-05-12
> **deadgobby said:**
> The sever is down

It was ok a few minutes ago.  I installed using apt-get

---

### Post by MetalMusicAddict on 2007-05-12
Site is down only. Repo is fine.

---

### Post by siralphred on 2007-05-12
nice tutorial....worked flawlessly

---

### Post by guernicaaa on 2007-05-13
Very cool tutorial.  Quick question, how did you get that little system monitor on your top bar?  And the CPU meter on the side of your screen shot?  (im like a day old to ubuntu :()

EDIT: Cool, I figured out how to add the hardware monitor to the panel!  Thanks for the tutorial, I'm loving this theme.

---

### Post by DG19075 on 2007-10-20
I've just upgraded to 7.10 and want to keep the Ubuntu Studio theme and window borders; however, I get a border that looks like Gilouche, only black, instead of the snazzy Vista-like theme. Any workarounds to this yet?

---

