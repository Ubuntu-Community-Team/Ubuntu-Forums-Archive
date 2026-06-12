---
title: "Ubuntu Splash Image Retouched"
date: 2005-12-26
forum: Art &amp; Design
---

### Post by theCore on 2005-12-26
I retouched the original Ubuntu Splash. I tried to keep the Ubuntu look as much as possible. Here the result:
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=4850&stc=1&d=1135655164[/IMG]

This one was "gimped" a little bit more:
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=4851&stc=1&d=1135655164[/IMG]

I also tried smooth the corners a little bit, but it lool like that Ubuntu don't render very well the transparents pixels.
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=4852&stc=1&d=1135655452[/IMG]

Thanks for any feedback :KS

---

### Post by anil_robo on 2005-12-27
Nice work in GIMP. The changes are subtle, but noticeable. I think you can also try to convert them to other colors so that users can match them with their wallpaper color! :)

I have a blue wallpaper, and would love to see an Ubuntu splash matching that! :D

---

### Post by DoorGunner on 2005-12-27
very nice....i like the third down with the rounded edges....Looks a little softer

---

### Post by anil_robo on 2005-12-27
Oops! I almost failed to notice the rounded edges of the third screen! Bravo! I strongly recommend the rounded edges be included in Dapper by default! :)

---

### Post by Gray. on 2005-12-29
Looks alot better with rounded edges. Nice work.

---

### Post by towsonu2003 on 2005-12-29
I like the second one (but with the rounded edges of the third one)... Very romantic indeed ;) Now we need a howto to change our splash ;)

---

### Post by noob_Lance on 2005-12-29
where can you put it to override the one that is set in ubuntu?? i love the 3rd one... but will do some gimping myself to make it kinda... blend in and make it seem like it fits..

---

### Post by Snakey on 2005-12-29
In GConf-editor, goto apps > gnome session > options ; then you'll find splash image on the right, just edit the path to your new image ;)

---

### Post by tseliot on 2005-12-29
The 2nd and the 3rd Splash Images are great!

---

### Post by ubuntu27 on 2005-12-29
Good job theCore !! :D I like all of them :)  though my favorite one is the third one ;)

---

### Post by kperkins on 2005-12-29
[QUOTE=Snakey]In GConf-editor, goto apps > gnome session > options ; then you'll find splash image on the right, just edit the path to your new image ;)[/QUOTE]
Or even easier go to System > Preferences > Splash Screen > Install (browse  to the new splashscreen, choose it, hit ok) > Highlight it > Activate
(You need gnome-splashscreen-manager installed--it's in universe.)

---

### Post by noob_Lance on 2005-12-29
cool... s there anyway t change this one with the one at boot up :D

---

### Post by John.Michael.Kane on 2005-12-29
Will these be done in blue? they look great.

Also maybe the OP could make a guide for those who want to make their own let them know how it's done.

---

### Post by theCore on 2005-12-30
Thanks for the comments! :) 

Here how to install new splash screens:

In the Terminal:
```

   $ sudo cp your_new_splash /usr/share/pixmaps/splash/
   $ cd /usr/share/pixmaps/splash/
   $ sudo ln -s your_new_splash ubuntu-splash.png
```
Just replace `your_new_splash' by the name of your splash.

Here a blue version of the splash:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=4933&stc=1&d=1135923387[/IMG]

The round-edged splash isn't working properly. There will be some noise where is the transparent pixels. I will try to fix that bug soon. Stay tuned! ;)

---

### Post by drfalkor on 2005-12-30
Very smooth and nice.
I like the 3rd image best :p

EDIT: and the [COLOR="Blue"]blue[/COLOR] one (feeling blue)

---

### Post by muchmusic on 2005-12-30
[QUOTE=theCore]Thanks for any feedback :KS[/QUOTE]


They are good. I like the rounded edges. I was typing this mainly to ask for a blue version and there it was! 

Maybe blue could match clearlooks more? (try clearlooks-cairo thread in art forum for ideas I think) it looks more kubuntu now, not that that is a bad thing but maybe three are necessary =)

---

### Post by John.Michael.Kane on 2005-12-30
@theCore Damn fine work!!! Thanks...

for those who want to install these splashes you can use this tool ```
sudo apt-get install gnome-splashscreen-manager
``` found listed here [http://www.ubuntuforums.org/showthread.php?t=77694](http://www.ubuntuforums.org/showthread.php?t=77694) Credit to Ai...

---

### Post by theCore on 2005-12-30
[QUOTE=muchmusic]
Maybe blue could match clearlooks more? (try clearlooks-cairo thread in art forum for ideas I think) it looks more kubuntu now, not that that is a bad thing but maybe three are necessary =)[/QUOTE]

I had Kubuntu in mind, when I maded the blue version of the splash.

Here the last variation I will make for this splash. The next one I will be a brand new splash. :rolleyes: 
[img]http://www.ubuntuforums.org/attachment.php?attachmentid=4962&stc=1&d=1135991665[/img]

---

### Post by jsmidt on 2005-12-30
You do wonderful work.

anil_robo said:

> I have a blue wallpaper, and would love to see an Ubuntu splash matching that! 

I'm with him.  I would like to see some work in blue too.  The above thread looks really good. :D

---

### Post by muchmusic on 2005-12-31
[QUOTE=theCore]I had Kubuntu in mind, when I maded the blue version of the splash.

Here the last variation I will make for this splash. The next one I will be a brand new splash. :rolleyes: 
[img]http://www.ubuntuforums.org/attachment.php?attachmentid=4962&stc=1&d=1135991665[/img][/QUOTE]

Woah! Can't wait for more!

Good work again!

---

### Post by brentroos on 2005-12-31
*

---

### Post by Havoc on 2005-12-31
Yeah, I've got a "workaround" you could use...

First, Open up a new image in Gimp, with a resolution that matches your desktop resolution.
Then, apply the backround color of your choice.
Get the splash of your choice.
Append it on your image, and try to center it.
Save the image!

The whole idea is to make the splash screen fullscreen, so that the brown backround is not visible.

Have a nice day! :cool:

---

### Post by endersshadow on 2005-12-31
[QUOTE=brentroos]Is there any way to change the brown background? What I mean is that if I was using a blue ubuntu splash, I'd like to have the background match it, to maybe blue, or something. 

When the blue ubuntu splash is loading, the background is still brown.

I cannot figure this out. I have been looking for the longest time for this solution.

There has got to be a config file or xml file of some sort to edit. Can anyone please point me to this? I would very much appreciate it.

Thank you, everybody.[/QUOTE]

System>Administration>Login Screen Setup

Click on the GTK+ Greeter tab.  In the lower right hand corner is a button for Background Color.  Change that to your desired color, and you're all set!

---

### Post by brentroos on 2006-01-02
*

---

### Post by endersshadow on 2006-01-02
[QUOTE=brentroos]Yeah, already figured it out, when messing with settings. But thanks though. I figured it out when I wasn't looking for it. Pretty ironic. I searched for a long time to figure this out, then just happened upon it. Funny how silly little things like that work out.

Thank you for your friendly response.[/QUOTE]

Good to hear, and I'm glad you got it working.

Oh, and go Giants :-D

---

### Post by ubuntu27 on 2006-01-03
I've installed the new Spalsh image with Gnome Splash Screen Preferences [System/Preferences/Splash Screen] and I don't have any splash Screen at all...LOL

How do I restore my previous [the default] splash screen?

---

### Post by theCore on 2006-01-04
Here another splash for Ubuntu! This one is a custom creation ... made in 30 min. ;)
[img]http://www.ubuntuforums.org/attachment.php?attachmentid=5081&stc=1&d=1136354979[/img]

Here a rounded variant:
[img]http://www.ubuntuforums.org/attachment.php?attachmentid=5082&stc=1&d=1136354979[/img]

---

### Post by kperkins on 2006-01-04
Dude--Dapper Drake is actually Version 6.04, and Breezy is 5.10.
Other than that, nice work. :D

---

### Post by encompass on 2006-01-06
I would take the first image but with rounded edges myself.  But good work... wish I was could draw like that.

---

### Post by theCore on 2006-01-07
[QUOTE=kperkins]Dude--Dapper Drake is actually Version 6.04, and Breezy is 5.10.[/QUOTE]

Thanks for the correction.

I included the XCF source file of the image. You can download it [here]("http://www.ubuntuforums.org/attachment.php?attachmentid=5193&stc=1&d=1136693433")
You are free to modify it, according to terms of the [Free Art license]("http://artlibre.org/licence/lal/en/")

---

### Post by theCore on 2006-01-25
I got some more splash images, enjoy!

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=5579&stc=1&d=1138251097[/IMG]
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=5580&stc=1&d=1138251097[/IMG]
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=5581&stc=1&d=1138251097[/IMG]
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=5582&stc=1&d=1138251097[/IMG]

---

### Post by leveliv on 2006-01-26
hi...wow these are amazing  :D im stuck on using the thirdo ne on the first page...I like the rounded corners nice job guyz

---

### Post by robtotheb on 2006-01-27
Love your work core.  Been using your original curved edge splash for a few days when I had an idea to remove the box completely.  I can add more colours if people like it.  Its the default brown in Breezy atm.

Let me know what you think.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=5624&d=1138377209[/IMG]


[ATTACH]5624[/ATTACH]

---

### Post by benplaut on 2006-01-27
[QUOTE=theCore]Thanks for the correction.

I included the XCF source file of the image. You can download it [here]("http://www.ubuntuforums.org/attachment.php?attachmentid=5193&stc=1&d=1136693433")
You are free to modify it, according to terms of the [Free Art license]("http://artlibre.org/licence/lal/en/")[/QUOTE]

thanks for that... remember, if you post your origionals, you get a hug :rolleyes:

---

### Post by skylark on 2006-01-27
robtotheb - that is an awesome design. Crisp, simple and effective!

---

### Post by robtotheb on 2006-01-27
Thanks skylark.  

In case my first post wasn't clear the background colour at login is the brown on my design by default (#523921) so the splash image blends with the rest of the screen eliminating the box effect which I personally have never liked.

Now onto the log in screen... the Ubuntu logo is just too BIG!

Brown is back. Who would have thought it?!

---

### Post by mustang on 2006-01-27
[QUOTE=theCore]I got some more splash images, enjoy!
...
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=5582&stc=1&d=1138251097[MG][/QUOTE]

I really like the last one. Nice job

---

### Post by John.Michael.Kane on 2006-02-14
@robtotheb could you do that one in blue or maybe even a medum gray..

---

### Post by Ghetto_Smurf on 2006-02-17
theCore i lked the 2nd one on the first page and the first one on this page. shamme it looks like it has lots of damaged pixels. if could make it sound more like the first ones but in that tone of blue it would so rock for those (like me) that have a dark desktop

---

### Post by Garyu on 2006-02-24
[QUOTE=robtotheb]Let me know what you think.[/QUOTE]

Wow. One of the best splashes ever for Ubuntu IMO. Great job! And as noted before, how about similar ones in blue, gray and maybe a dark blood red? =)

---

### Post by robtotheb on 2006-02-26
Here you go. I finally had the time to make them!

Black:
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=6446&stc=1&d=1140952741[/IMG]

Blue (#3c5cb2):
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=6447&d=1140952694[/IMG]

Red (#ee2233):
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=6448&d=1140952694[/IMG]

White:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=6449&d=1140952694[/IMG]

[ATTACH]6446[/ATTACH]

[ATTACH]6447[/ATTACH]

[ATTACH]6448[/ATTACH]

[ATTACH]6449[/ATTACH]

---

### Post by John.Michael.Kane on 2006-02-26
@robtotheb **NICE!!!!!!**

---

### Post by Ghetto_Smurf on 2006-02-26
the black one is soooo going to my splash screen

---

### Post by Garyu on 2006-02-26
[QUOTE=Ghetto_Smurf]the black one is soooo going to my splash screen[/QUOTE]

hear hear :cool:

---

### Post by Ghetto_Smurf on 2006-02-27
i retouched the black one a bit... now the logo is light blue in black... im editing all my ubuntu desktop to have this pair of coulours

---

### Post by jordanm on 2006-03-03
Call me old-fashion but I like the first one you posted in the first thread the best. If you were to round the 4 corners and add "Ubuntu 5.10 Dapper Drake" in the lower right like you did later in the later post it would look awesome IMO.

---

### Post by meborc on 2006-03-03
[QUOTE=jordanm]Call me old-fashion but I like the first one you posted in the first thread the best. If you were to round the 4 corners and add "Ubuntu 5.10 Dapper Drake" in the lower right like you did later in the later post it would look awesome IMO.[/QUOTE]

you must mean 6.04 Dapper Drake... or 5.10 Breezy Badger :rolleyes:

---

### Post by jordanm on 2006-03-03
My fault, meant 6.04 Dapper.

---

### Post by Mathias-K on 2006-03-03
Wow, this thread is just full of nice artwork. 

@theCore/robthetheb

I've always thought that the Kubuntu bootup/splash logos and screens were a little less attractive than those for Ubuntu. With your skills, i must encourage you to do something for KDE, and btw: you two should be on the artist team for the whole distro, you work is AMAZING :)

---

### Post by Who on 2006-03-20
Here is some of my work

[http://www.gnome-look.org/content/preview.php?preview=1&id=36223&file1=36223-1.png&file2=36223-2.png&file3=36223-3.png&name=Cornfield+Dapper+Splash](http://www.gnome-look.org/content/preview.php?preview=1&id=36223&file1=36223-1.png&file2=36223-2.png&file3=36223-3.png&name=Cornfield+Dapper+Splash)
or [http://www.gnome-look.org/content/show.php?content=36223](http://www.gnome-look.org/content/show.php?content=36223) to download
[IMG]http://www.gnome-look.org/content/pre1/36223-1.png[/IMG]
I'm really liking the simple brown one by robtotheb

Enjoy,
Who

---

### Post by John.Michael.Kane on 2006-03-24
@Who Looks good. think you can pull that off in a gray tone.

---

### Post by Madpilot on 2006-03-26
I've switched to robtotheb's plain brown splash, I really like how it blends into the background!

But Who's sine wave Dapper splash is tempting, and I don't even run Dapper!

I really like the jittery outline of the Ubuntu logo & name.

---

### Post by haddog on 2006-04-20
[QUOTE=SD-Plissken]@theCore Damn fine work!!! Thanks...

for those who want to install these splashes you can use this tool ```
sudo apt-get install gnome-splashscreen-manager
``` found listed here [http://www.ubuntuforums.org/showthread.php?t=77694](http://www.ubuntuforums.org/showthread.php?t=77694) Credit to Ai...[/QUOTE]
Thnx SD. Splashscreen manager works great.

---

### Post by haddog on 2006-04-20
[QUOTE=Who]Here is some of my work

[http://www.gnome-look.org/content/preview.php?preview=1&id=36223&file1=36223-1.png&file2=36223-2.png&file3=36223-3.png&name=Cornfield+Dapper+Splash](http://www.gnome-look.org/content/preview.php?preview=1&id=36223&file1=36223-1.png&file2=36223-2.png&file3=36223-3.png&name=Cornfield+Dapper+Splash)
or [http://www.gnome-look.org/content/show.php?content=36223](http://www.gnome-look.org/content/show.php?content=36223) to download
[IMG]http://www.gnome-look.org/content/pre1/36223-1.png[/IMG]
I'm really liking the simple brown one by robtotheb

Enjoy,
Who[/QUOTE]
This is Very Nice Who!

---

### Post by tsrjzq on 2006-04-26
very nice work, though my splash is a nature theme from gnome-look.org...

---

