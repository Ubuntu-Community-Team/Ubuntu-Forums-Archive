---
title: "Creating Icon Theme Need Help."
date: 2007-07-24
forum: Art &amp; Design
---

### Post by troseph on 2007-07-24
This is more of a request for help packaging this icon set I am working on. 

[http://gnome-look.org/content/show.php/Yalis+W.I.P?content=62606](http://gnome-look.org/content/show.php/Yalis+W.I.P?content=62606)

These are made in Inkscape in svg format. I would like to know if someone would be willing to package these for gnome. Or show me how to package these to work with gnome. 

Is there an app to create the .theme files? or does it need to be done by hand? Would imagemagik work? I am very new to designing on Linux, and any help would be very awesome.

Also, GiB's (Gnome Icon Builder) website is down. Has anyone tried it? What do you need to get it istalled?

Thanks in advance,
Troy

---

### Post by smartboyathome on 2007-07-24
I would say take an icon theme off gnome-look.org and then use that to package yours. That is what I did for my theme! ^_^

---

### Post by troseph on 2007-07-24
That sounds like a lotta work. :D I'll do it. 

What does everyone think about my icon set??

---

### Post by smartboyathome on 2007-07-24
Looks nice. I will definately have to give it a try sometime ;)

---

### Post by digitalis_vulgaris on 2007-07-24
Your icons are very good. You have my compliments...

---

### Post by troseph on 2007-07-24
Alright. I have been working on trying to over-write every icon in a different icon set, and  my mood and motivation have been going steadily down-hill. I'm so sick of saving 6 versions of every file I just made.

Is there any way of saving the different versions of the files in batches? I've heard of imagemagik, but I don't know how to work it...

---

### Post by crimesaucer on 2007-07-26
> **troseph said:**
> That sounds like a lotta work. :D I'll do it. 

What does everyone think about my icon set??

They look good...I wouldn't use so much yellow, but besides that they look like a nice variation of the UbuntuStudio icons (which are my favorite right now)....


What I really like about your icons, are your round glass buttons...those are beautiful...and way better than UbuntuStudio's round arrows.


...and then when I looked at the two of them side by side, I think I liked your icon's folders better, they were sharp and clean and still had that beautiful blue stripe glass look....I did miss the wavy round feel, but the sharpness was really cool.


I also think you put a lot of effort into the emblems, and the rest of the icons...I like them all except for your music icon....


...anyway nice job.

---

### Post by crimesaucer on 2007-07-30
@ troseph-

Like I said above, I liked your arrow buttons a lot, but I found that they sort of looked better when the arrow was positioned a bit differently.

I used your arrow buttons, and then used the rest of UbuntuStudio to create a new icon pack for my brown theme.

...anyway, here is the way I think those buttons look better when the arrows are positioned more to the center.

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-4b.png[/IMG]

---

### Post by troseph on 2007-08-02
Nice! Can you package these icons? I am installing GiB, but I'm not so sure it will work...

---

### Post by crimesaucer on 2007-08-02
This was the first time I ever tried to theme with icons, so this might not be the best way, but it worked for me:


First, I copied the UbuntuStudio scalable folder into my home folder.


Then what I did was, I took your nice, glassy, round arrow buttons, and centered the "go-next" and "go-previous" arrows (keeping all of the other round buttons the same), and then greyscaled them all, and also added saturation to them all so they became that brown color that I wanted. Then I saved them in to my copy of the "UbuntuStudio" scalable icons, along with the rest of the regular "UbuntuStudio" icons that I also greyscaled and saturated in the exact same way I did with your round arrow buttons....


The next thing I did was to create a "NEW-icons" folder and into it I put my new icons from the scalable folder, with all of it's sub-folders like: actions, apps, devices...


I also made a 48x48 folder, a 24x24 folder, a 22x22 folder and a 16x16 folder and put them all into ~/NEW-icons...then copied all of the scalable .svg icons into each of the individual folders of each size folder except 48x48...


...so now, in ~/NEW-icons, I had 5 folders that were:

scalable
48x48
24x24
22x22
16x16


and in scalable, as well as 24x24, 22x22, and 16x16, I had these same folders in each:

actions
apps
categories
devices
emblems
emotes
mimetypes
places
status

...and each folder contained the exact same .svg icons that I had made brown...


...Then, I would open my Terminal in each individual folder (:~/NEW-icons/24x24/actions$), and then type this command to change them all into 24x24 pixel .png images at once:

```
for i in *.svg; do inkscape -f "$i" -e "$i.png" -w24 -h24; done
```  

-w and -h is width and height, so just use that command in each icon folder (actions, apps, devices...), for each size folder (24x24, 22x22, 16x16),  and just change the -w24 and -h24, to -w22 and -h22, and also w-16 and -h16 for the different size folders....and the 48x48 only had one icon in it so I just copied it from the "UbuntuStudio" folder.


Then after that was done, I used Bulk Rename in the Accessories section of my start menu, and  used "Search and Replace"...

Search for:   .svg.png
Replace with:   .png

...and renamed all my images at once, for each of my three sized folders (24x24, 22x22, 16x16)...


Then, in my File System, I selected to view my files by "type" which separated the .png from the .svg, and then deleted all of the .svg images from every folders in 24x24, 22x22, and 16x16.


Next, I used Terminal to create a second "UbuntuStudio" folder like this:


```
cd /usr/share/icons
```

```
sudo cp -r UbuntuStudio /usr/share/icons/NEW-icons
```  


Then, in your newly created NEW-icons folder, change the name in your index.theme from UbuntuStudio to NEW-icons, and your name in your index.theme~ from ubuntustudio to new-icons.


Then, the last thing is to "alt+f2", and gksudo thunar (I use xubuntu so that is my file system)...


...and then copy and paste all of your ~/NEW-icons (which has scalable, 48x48, 24x24, 22x22, and 16x16 in them)...into your /usr/share/icons/NEW-icons


then, compare your newly created "NEW-icons" with the old "UbuntuStudio" icons, and see what is extra in each folder and delete it, and also see if you need to keep anything that you didn't have in your scalable .svg file (for me it was only a few mouse icons and adding some xfce4 icons)...and that's it.


It seems like a bunch of work, but it went pretty fast with the .svg to .png command and the bulk rename.


As for me uploading the brown buttons, I guess I could ask for permission from you and the creator of the UbuntuStudio icons, I'm also going to try and make it in to a black/white icon pack, and maybe a few other colors that match my gtk-2.0 themes, but since I am very new at this and am just learning how to use inkscape, I hadn't planned on sharing anything yet....it's just that I had been wishing for a few months that someone would make new color themes for the blue UbuntuStudio icons, since they were my favorite, so I tried to do it on my own and accomplished it successfully.

---

### Post by troseph on 2007-11-02
OMG Thank you!!!

---

### Post by twizler on 2007-11-07
:popcorn: WOW -- THAT was AN AWESOME POST!!!! THANK YOU !!!! U ROCK!!!> **crimesaucer said:**
> This was the first time I ever tried to theme with icons, so this might not be the best way, but it worked for me:


First, I copied the UbuntuStudio scalable folder into my home folder.


Then what I did was, I took your nice, glassy, round arrow buttons, and centered the "go-next" and "go-previous" arrows (keeping all of the other round buttons the same), and then greyscaled them all, and also added saturation to them all so they became that brown color that I wanted. Then I saved them in to my copy of the "UbuntuStudio" scalable icons, along with the rest of the regular "UbuntuStudio" icons that I also greyscaled and saturated in the exact same way I did with your round arrow buttons....


The next thing I did was to create a "NEW-icons" folder and into it I put my new icons from the scalable folder, with all of it's sub-folders like: actions, apps, devices...


I also made a 48x48 folder, a 24x24 folder, a 22x22 folder and a 16x16 folder and put them all into ~/NEW-icons...then copied all of the scalable .svg icons into each of the individual folders of each size folder except 48x48...


...so now, in ~/NEW-icons, I had 5 folders that were:

scalable
48x48
24x24
22x22
16x16


and in scalable, as well as 24x24, 22x22, and 16x16, I had these same folders in each:

actions
apps
categories
devices
emblems
emotes
mimetypes
places
status

...and each folder contained the exact same .svg icons that I had made brown...


...Then, I would open my Terminal in each individual folder (:~/NEW-icons/24x24/actions$), and then type this command to change them all into 24x24 pixel .png images at once:

```
for i in *.svg; do inkscape -f "$i" -e "$i.png" -w24 -h24; done
```  

-w and -h is width and height, so just use that command in each icon folder (actions, apps, devices...), for each size folder (24x24, 22x22, 16x16),  and just change the -w24 and -h24, to -w22 and -h22, and also w-16 and -h16 for the different size folders....and the 48x48 only had one icon in it so I just copied it from the "UbuntuStudio" folder.


Then after that was done, I used Bulk Rename in the Accessories section of my start menu, and  used "Search and Replace"...

Search for:   .svg.png
Replace with:   .png

...and renamed all my images at once, for each of my three sized folders (24x24, 22x22, 16x16)...


Then, in my File System, I selected to view my files by "type" which separated the .png from the .svg, and then deleted all of the .svg images from every folders in 24x24, 22x22, and 16x16.


Next, I used Terminal to create a second "UbuntuStudio" folder like this:


```
cd /usr/share/icons
```

```
sudo cp -r UbuntuStudio /usr/share/icons/NEW-icons
```  


Then, in your newly created NEW-icons folder, change the name in your index.theme from UbuntuStudio to NEW-icons, and your name in your index.theme~ from ubuntustudio to new-icons.


Then, the last thing is to "alt+f2", and gksudo thunar (I use xubuntu so that is my file system)...


...and then copy and paste all of your ~/NEW-icons (which has scalable, 48x48, 24x24, 22x22, and 16x16 in them)...into your /usr/share/icons/NEW-icons


then, compare your newly created "NEW-icons" with the old "UbuntuStudio" icons, and see what is extra in each folder and delete it, and also see if you need to keep anything that you didn't have in your scalable .svg file (for me it was only a few mouse icons and adding some xfce4 icons)...and that's it.


It seems like a bunch of work, but it went pretty fast with the .svg to .png command and the bulk rename.


As for me uploading the brown buttons, I guess I could ask for permission from you and the creator of the UbuntuStudio icons, I'm also going to try and make it in to a black/white icon pack, and maybe a few other colors that match my gtk-2.0 themes, but since I am very new at this and am just learning how to use inkscape, I hadn't planned on sharing anything yet....it's just that I had been wishing for a few months that someone would make new color themes for the blue UbuntuStudio icons, since they were my favorite, so I tried to do it on my own and accomplished it successfully.

---

