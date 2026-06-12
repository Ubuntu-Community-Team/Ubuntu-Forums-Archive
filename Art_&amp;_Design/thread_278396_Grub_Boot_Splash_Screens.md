---
title: "Grub Boot Splash Screens"
date: 2006-10-16
forum: Art &amp; Design
---

### Post by unlokia on 2006-10-16
Hi guys! :D

I have been experimenting with Grub bootsplash screens - you are more than welcome to download and install them - let me know what you think (or how much you dislike them HAHA!). For the beginners, here is how to install them:

(1) Make sure your bootloader *IS* Grub (duuuh!)
(2) Select the chosen "splash.xpm.gz" and copy it to /boot/grub
(3) Once you have copied the desired screen to /boot/grub, drop to terminal and do:

```
$ sudo update-grub
```

You will be asked for root password possibly - just type it and <<ENTER>>.

I shall be adding more screens over the next few days - the one I have added here, is the KDE wallpaper of two sheep, as seen here:

[IMG]http://i61.photobucket.com/albums/h48/unlokia/twosheepcrazy_14_col_prev.jpg[/IMG]

Have fun - I know it's not much but hey - try them and see if you like 
them!

(Please note that each attachment is different - to see which one you are downloading, refer to the picture directly above the attachment link, in the post!)

---

### Post by unlokia on 2006-10-16
Another...

[IMG]http://i61.photobucket.com/albums/h48/unlokia/preview.jpg[/IMG]

---

### Post by unlokia on 2006-10-16
My own work! :D

[IMG]http://i61.photobucket.com/albums/h48/unlokia/radiate_ubuntu.jpg[/IMG]

Download link below...

---

### Post by hikaricore on 2006-10-19
> **unlokia said:**
> 
[IMG]http://i61.photobucket.com/albums/h48/unlokia/twosheepcrazy_14_col_prev.jpg[/IMG]


lol cute sheeps

---

### Post by unlokia on 2006-10-20
Here is my latest creation - 640 x 480 Background image first:
[IMG]http://i61.photobucket.com/albums/h48/unlokia/640x480bg.jpg[/IMG]

And now how it looks at boot time:
[IMG]http://i61.photobucket.com/albums/h48/unlokia/preview-1.jpg[/IMG]

Please download the pre-gzipped bootsplash below, then drop it into /boot/grub and edit your /boot/grub/menu.lst to point to it.

---

### Post by distroman on 2006-11-01
[http://ubuntuforums.org/gallery/showphoto.php?photo=3891&cat=5](http://ubuntuforums.org/gallery/showphoto.php?photo=3891&cat=5)
I saw this wallpaper and I really liked it, so I made a grub splash of it.
If you don't trust my gimp skills you can make your own really fast :D
[https://help.ubuntu.com/community/GrubHowto#head-616e8477b76f70cdd317812fef0ac88b248e25b4](https://help.ubuntu.com/community/GrubHowto#head-616e8477b76f70cdd317812fef0ac88b248e25b4)
ohh, and nice ones so fare, ill save some and try them later :)

---

### Post by frizzl on 2006-11-02
im sorry guys, but i cant seem to figure out how to get the file into the grub folder

it gives me an error saying i do not have correct permissions to write to the folder...

any help appreciated

---

### Post by wjp.reg on 2006-11-02
You need to open the folder with supervisory privileges in order to make changes in /boot/grub, using **sudo**

---

### Post by unlokia on 2006-11-05
Your command would be:

```
sudo cp splash.xpm.gz /boot/grub
```

Once you have completed that, you do:

```
sudo gedit /boot/grub/menu.list
```

This will allow you to edit grub options, to point to the splash.xpm.gz
that you copied in the first step.

---

### Post by pinguinus on 2007-01-06
I have used, for example, a stylish commercial photo of a desert caravan as my grub splash image (the orange-brownish colors suit default Ubuntu colors very nicely). But because the photo is commercial, I won't post it here.  Instead, here's a link to many nice images (plus links to tutorials if you want to make your own): 
[http://www.schultz-net.dk/grub.html](http://www.schultz-net.dk/grub.html)

---

### Post by Kilk on 2007-01-07
> **unlokia said:**
> Your command would be:

```
sudo cp splash.xpm.gz /boot/grub
```

Once you have completed that, you do:

```
sudo gedit /boot/grub/menu.list
```

This will allow you to edit grub options, to point to the splash.xpm.gz
that you copied in the first step.

What do we put in the menu.list file? And how can we delete the file out of the directory using sudo?

---

### Post by Steve S. on 2007-01-12
Check out Start Up Manager (SAM) in some of the other threads...you can click really effortless in a gui and change out these great screen ideas with absolutely mininimal effort...
[Here it is...]("http://www.ubuntuforums.org/showthread.php?t=295524")


I use it for usplash as well.
[usplash idea]("http://www.ubuntuforums.org/showthread.php?t=334428")

Once again, great artwork!8)

---

### Post by siddharth_moghe on 2007-03-16
yes...but the catch is that when u are changing the images to  xpm.gzip format...then u loose much of the picture quality in that....so its better to change the image to a black and white format and then to gzip. That saves some picture quality !


[:)]

---

### Post by d4rk on 2007-03-16
I totally digg those ubuntu logo boot screens :)
Great work man!

---

### Post by zoogTHOMzoog on 2007-04-16
Your boot splashes are all great. Ever think of adding them to gnome-look.org? Pickings seem a little slim on that site for good Ubuntu splashes!


Rock:guitar:on... -zoog

---

### Post by lotacus on 2007-04-16
I don't understand why your boot screens are using low res. Are you using dapper? My screens are all highcolor. are you using usplash?

In any case, i'm always looking for nice boot screens. One that I had hoped to find would include the ubuntu logo filling up with color in a clockwise fashion (not like filling up a cup of water) instead of using the default status bar animation. Right now i'm using the coffee-beans one. It's still a great splash.

---

### Post by oomingmak on 2007-04-16
> **hikaricore said:**
> lol cute sheeps
That sheep on the right looks a bit shifty (like he's up to no good).

:mrgreen:

---

### Post by Beebock on 2007-04-20
> **oomingmak said:**
> That sheep on the right looks a bit shifty (like he's up to no good).

:mrgreen:

yep, definitely the black sheep of the family!

---

### Post by Thingymebob on 2007-04-25
> **lotacus said:**
> I don't understand why your boot screens are using low res. Are you using dapper? My screens are all highcolor. are you using usplash?


Because these are in the **grub** menu screen, you are limited to a maximum of 14 colours at 640x480 at this point. You normally won't see this screen unless you are dual booting or you press escape right after your system posts.

You are talking about the usplash ie the screen you get when ubuntu is loading

heres mine:
[IMG]http://www.aircooled.info/images/boot.gif[/IMG]

---

### Post by Thingymebob on 2007-04-26
....And my ubuntu themed screen:
[IMG]http://www.aircooled.info/images/grubuntu.gif[/IMG]

---

### Post by xopher on 2007-04-26
Here's one of mine, enjoy ;)

[IMG]http://gnome-look.org/CONTENT/content-pre2/36907-2.png[/IMG]

[http://gnome-look.org/content/show.php/Blubuntu+GRUB+Splash?content=36907](http://gnome-look.org/content/show.php/Blubuntu+GRUB+Splash?content=36907)

---

### Post by Warren Watts on 2007-09-02
So I was bored today and created a small selection (20 or so) of GRUB splash screens. 
As I create more, they will be added to the list.

Anyone who is interested can view/download them at:

[GRUB Splash Screens]("http://kingbeetle66.servehttp.com/cgi-bin/grub_thumb_view.pl")

Enjoy!

---

### Post by jpyanowski on 2007-09-05
I have this thread saved so I can customize my boot splash when I reinstall ubuntu: [http://ubuntuforums.org/showthread.php?t=30341](http://ubuntuforums.org/showthread.php?t=30341)

Hope this helps.

---

### Post by CowzRule on 2007-09-05
Here's mine
[IMG]http://i3.tinypic.com/4lnxnhw.jpg[/IMG]

---

### Post by boob11 on 2007-11-26
thnx man :popcorn:

---

### Post by twist2b on 2007-11-26
it says i dont have permission to place it in the folder :'( so how do i get the permission... or what do i do?

---

### Post by smartboyathome on 2007-11-27
> **twist2b said:**
> it says i dont have permission to place it in the folder :'( so how do i get the permission... or what do i do?

Alt-F2 and type gksudo nautilus, then navigate to the folder and paste it in there.

---

### Post by Tikkel on 2007-12-21
ghehe...I'll have that one! Thanx

---

### Post by aikiwolfie on 2008-10-18
When I tried to make a grub bootsplash all the colours ended up weird. I reduced the image to 640x480 and the number of colours to 14 using gimp. I've also tried messing with the color setting in the start-up manager. Nothing works.

---

### Post by monkey d luffy on 2009-11-19
I did as you described but im unable to load ubuntu. I am getting the grub command line.
How can i solve this?

---

### Post by Steve S. on 2009-11-19
> **monkey d luffy said:**
> I did as you described but im unable to load ubuntu. I am getting the grub command line.
How can i solve this?

Hmmm...most likely something got missed or skipped or overlooked (that's usually what happens to me ;)).  Please retrace your steps and try again.  You may also check the other posts on this thread as perhaps someone else has had the same issue.  Another option is to try a picture someone else has done and use it.

...to be honest with you, I haven't played on an Ubuntu box for a while so the version you are using may have an easier way to do this.  Perhaps others on the forum could help if you give version info, exact steps you followed, etc.?

---

### Post by monkey d luffy on 2009-11-19
It´s allright again I googled it.
I had to manually boot, the problem is I am using grub2.
So i already reverted my settings.
Any idea how to implement custom picture using grub2?
I cant find any information on google.

---

### Post by drs305 on 2009-11-19
> **monkey d luffy said:**
> It´s allright again I googled it.
I had to manually boot, the problem is I am using grub2.
So i already reverted my settings.
Any idea how to implement custom picture using grub2?
I cant find any information on google.

Make the image a size to be compatible with the Grub 2 screen resolution (640x480 by default unless you change it in /etc/default/grub).

Add the file to the folder referenced in /etc/grub.d/05_debian_theme. The two default locations in which G2 looks are /boot/grub and /usr/share/images/desktop-base. The file default types are .tga and .png

Replace the default "moreblue-orbit-grub." filename in the above file, about line 16. Don't forget the period after the filename.

Update grub with "sudo update-grub"

More information is available in the G2 community doc:
[https://help.ubuntu.com/community/Grub2#GRUB%202%20Splash%20Images]("https://help.ubuntu.com/community/Grub2#GRUB%202%20Splash%20Images")

---

### Post by monkey d luffy on 2009-11-19
Thanks alot for the reply!

I did as you instructed:
I placed the image (splash.png) in /boot/grub
I edit 05_debian_theme in /etc/grub.d/ their was no 05_debian. ?
I replaced the String with splash.png
And I used sudo update-grub.
But I still have the same boot logo.
That file looked alot like Java or is it some other language? :p
If it´s currently not possible with grub2 to change the boot logo, I don´t mind.

---

### Post by drs305 on 2009-11-19
> **monkey d luffy said:**
> And I used sudo update-grub.
But I still have the same boot logo.
If it´s currently not possible with grub2 to change the boot logo, I don´t mind.

If you put the filename in /etc/grub.d/05_debian_theme that was the correct location. Did you remember to add the . after the filename. So it looks like:
> 
  for i in {/boot/grub,/usr/share/images/desktop-base}splash.{png,tga} ; do


Is the image size compatible with the setting in /etc/default/grub?

When you were running "update-grub", did you see a line that read something similar to "Found Debian background: splash.png"

If you look in /boot/grub/grub.cfg is "splash.png" listed. You can quickly check with this line:
```
grep splash.png /boot/grub/grub.cfg
```

---

### Post by monkey d luffy on 2009-11-19
The image size is  not listed in /etc/default/grub
I did change 05_debian_theme again I thought I had to put the period after ¨splash¨.
But I corrected it in the file to ¨splash.¨.
When I do sudo grub-update in terminal I don´t get any responses like that.
I also put the file in the other directory but that was no use.
Also the grep splash.png /boot/grub/grub.cfg doesn´t respond.

---

### Post by wirate on 2009-12-30
let me pull up a not very old thread. Heres mine

---

### Post by drs305 on 2009-12-30
> **monkey d luffy said:**
> The image size is  not listed in /etc/default/grub
I did change 05_debian_theme again I thought I had to put the period after ¨splash¨.
But I corrected it in the file to ¨splash.¨.
When I do sudo grub-update in terminal I don´t get any responses like that.
I also put the file in the other directory but that was no use.
Also the grep splash.png /boot/grub/grub.cfg doesn´t respond.

If you post the contents of the /etc/default/05_debian_theme file (or at least the part that deals with the splash image) and the results of "ls /path/splash-image-name" (where the image is located) perhaps we can help you figure this out.

---

