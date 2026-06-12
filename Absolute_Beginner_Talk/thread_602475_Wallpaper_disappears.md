---
title: "Wallpaper disappears"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by petri on 2007-11-04
In Feisty my wallpaper started to disappear and it is sitll doing it with Gutsy. In Dapper that worked fine. Now I am left with the light brown wallpaper after a few minutes (not even Ubuntus own standard wallpaper stays on).

Anyone?

---

### Post by Pumalite on 2007-11-04
Post your specs.

---

### Post by petri on 2007-11-04
Motherboard is Asus M2NPV-VM with Nvidia 6150 inbuilt chipset
BIOS is original (don't know how to upgrade bios with Linux)
nvidia-glx is the graphics driver

RAM 2GB
AMD 5000+
but that should be irrelevant.

---

### Post by Pumalite on 2007-11-04
Can't blame your specs, but memtest might be the way to go.

---

### Post by SunnyRabbiera on 2007-11-04
are you using desktop effects?

---

### Post by petri on 2007-11-04
Yes. But the wallpaper disappears even with no desktop effects enabled.

---

### Post by SOULRiDER on 2007-11-04
Does it disappear randomly and reappear after a while or does it happen when you reboot? Move the wallpaper to a location like your home directory and select the copy as your wallpaper. I had a problem like this, it was because partitions mounted automatically in different locations everytime so sometimes GNOME could find my wallpaper and sometimes it couldnt.

---

### Post by Pumalite on 2007-11-04
The image has to be located within the systemfile.

---

### Post by petri on 2007-11-04
It disappears after a few minutes and is always gone after restart. It never reappears by itself.

By the way, when I want to shut down the computer it takes about 30-40 seconds before the shutdown/log out etc. buttons appear.

I did the memtest, no errors found.

Pumalite what do you mean with the systemfile? Where should I store my backgrounds so that every user can reach them?

---

### Post by Pumalite on 2007-11-04
I keep the image in /home

---

### Post by petri on 2007-11-04
It does not help where I have the images, wallpaper just disappears.

---

### Post by petri on 2007-11-07
Bump

---

### Post by swoll1980 on 2007-11-07
was the wallper file that you are using moved or deleted.  The wall paper links it's self to a path to a file if that file is moved or deleted then the wall paper will vanish next time it refreshes its self

---

### Post by petri on 2007-11-08
Thanks for your post.

I deleted all the wallpapers and added them back. The result is the same the wallpaper vanishes still.

---

### Post by petri on 2007-11-13
Bump again.

---

### Post by baloo56 on 2007-11-16
Hi Petri,

I have exactly the same Wallpaper & 30-40 second shutdown problem as you have described. The two problems seem to run hand-in-hand. My Wallpaper is located in /home.
I run Gutsy on a Dell Demension 8400. I did not have the problem when I had Dapper on the Dell. That is the only problem I have had with Gutsy. Other than that minor problem, Ubuntu is a pleasure to run.
Hope someone can solve our problem.

---

### Post by petri on 2007-11-20
Hello baloo56!

About the suspend problems we have a fix here: [http://ubuntuforums.org/showthread.php?t=603655](http://ubuntuforums.org/showthread.php?t=603655)

The wallpaper was worse. I forgott to tell averyone that I had an beta Gutsy wich was upgraded to the real one when the time was. I have now created a new installation and even a new /home and everything works like charm as I have read before in these forums.

Of course there is a little bit job to do with a new fresh installation but I think it is worth it. By the way howto move Evolution files to new home this worked for me: [http://ubuntu.wordpress.com/?s=move+evolution&searchbutton=go%21](http://ubuntu.wordpress.com/?s=move+evolution&searchbutton=go%21)
after I choosed to not care about not finding the .xml file. When I started Evolution for the first time in new Gutsy partition it just works directly. :)

---

### Post by baloo56 on 2007-11-26
Thanks Petri...
I appreciate the follow up. And yes....it did rectify my suspend problem.
I bet someone will soon solve the wallpaper issue too. All the best.

---

### Post by overdrank on 2007-11-26
Excuse my post as I responded to a malicious command [http://ubuntuforums.org/announcement.php?f=73](http://ubuntuforums.org/announcement.php?f=73)
Edit : Malignant code removed

---

### Post by ubuntu27 on 2007-11-26
Note: This message was directed toward a post containing malign command. 

What are you trying to accomplish posting the remove command in different threads? 
Are you trying to have "fun" by bulling?  It's not nice at all.


Forum Staff bodhi.zazen: "The user in question has been banned and I jailed all of the posts I could find :twisted: "

---

### Post by gercokees on 2008-01-31
Hi
I have the same problem. The wallpaper very often disappears after a re-login, and also i noticed that nautilus is running at 90% cpu. When i go to system > preferences > theme the wallpaper comes back...
is there a solution for the problem? Is it something that i am doing wrong? I could not find any launchpad issue, is it useful to post one?

Thanks in advance.

Greetz,
Gerco-Kees
<><

---

