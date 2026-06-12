---
title: "Set Icon for Speciific Media"
date: 2007-08-12
forum: Art &amp; Design
---

### Post by JJNova on 2007-08-12
Hello folks.

I'm such an idiot. How do I change the icon for a specific program?

For instance, I have movie player currently setup to play my audio files, and so there is a big green music note representing .ogg files. I would like to change that icon to something else. Where do I navigate to in order to replace icons?
In short, I want .ogg files to be represented by the image below.

Thank you much.

---

### Post by evissecx on 2007-08-13
> **JJNova said:**
> Hello folks.

I'm such an idiot. How do I change the icon for a specific program?

For instance, I have movie player currently setup to play my audio files, and so there is a big green music note representing .ogg files. I would like to change that icon to something else. Where do I navigate to in order to replace icons?
In short, I want .ogg files to be represented by the image below.

Thank you much.

You could change the file icon by right clicking on a .ogg-file and choose properties.. In the popup dialog, theres is a little configuration button. When clicking this 
you get a new popup dialog where you can change the icon for just the media type .ogg.
The configuration button is placed under the filename to the right.

hope this helped. :)

Oh I forgot. Stupid me. I am using KDE. What do you use? :)

---

### Post by hikaricore on 2007-08-13
> **evissecx said:**
> 
Oh I forgot. Stupid me. I am using KDE. What do you use? :)

I'm sure your sarcasm escapes the standard Gnome users.

---

### Post by JJNova on 2007-08-13
I do use Gnome, but I use it for a very specific reason.

I use gnome so that I can help the majority of the people who have problems when switching to Ubuntu. I, myself, prefer XFCE, but have concentrated on using Gnome so that I may be of service to new converts...

Apparently I need someone to help me though.

---

### Post by smartboyathome on 2007-08-13
This could be done by creating a new icon set (though it doesn't work for me). Simply create a new folder called scalable inside ~/.icons/default, and inside the scalable folder, make a new folder for mimetypes. Place your icon here as gnome-mime-audio-basic.png (if it is not a png, use GIMP or some other picture editor to change its filetype), and create links to it for other music extentions using gnome-mime-audio-*.png (where * is the extention, I have links to mine for mpeg, mp3, mp4, aac, and others [cannot list them all *_*]). Do this, and the icons should replace (but like I said, the player seems to override the icons).

---

### Post by JJNova on 2007-08-13
> **smartboyathome said:**
> ... and create links to it for other music extentions using gnome-mime-audio-*.png ...

How would I create links to it?

---

### Post by smartboyathome on 2007-08-13
Right click the icon in the folder and click "Make Link". Rename this link to what is said above. You can copy and paste the link and it will still direct to the one picture.

---

