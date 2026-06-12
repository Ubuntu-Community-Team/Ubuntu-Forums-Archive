---
title: "How to Install GIMPshop"
date: 2009-05-24
forum: Art &amp; Design
---

### Post by emotionlovesyou on 2009-05-24
I downloaded the GIMPshop .deb package and installed it. Then I ran GIMP but nothing seemed different.

I'm confused. Is GIMPshop it's own program intended to be ran independent of GIMP? If so, how do I run it after installing it? If not, how do I install GIMPshop AS PART OF my original GIMP installation?

Anyone know how to install GIMPshop? Thanks!!!

---

### Post by jerrrys on 2009-05-24
check this out...

[http://en.wikipedia.org/wiki/Gimpshop](http://en.wikipedia.org/wiki/Gimpshop)

---

### Post by emotionlovesyou on 2009-05-24
Thanks. I've read it. I didn't find it useful. Have you installed GIMPshop with a .deb package? Perhaps you could run me through what you did.

---

### Post by jerrrys on 2009-05-24
i run gimp...i did not need a photoshop look-a-like...as far as your problem...if your running gimp and gimpshop, im guessing there is a conflict and you need to uninstall gimp or maybe even both and then reinstall only gimpshop...

---

### Post by xrecar on 2009-05-24
alt+f2, then type: gimpshop

---

### Post by emotionlovesyou on 2009-05-24
> **xrecar said:**
> alt+f2, then type: gimpshop

I get:
Could not open location 'file:///home/***user***/gimpshop'

---

### Post by emotionlovesyou on 2009-05-24
I also tried un-installing GIMP and just running GIMPshop alone but nothing happens when I run/open GIMPshop

---

### Post by jerrrys on 2009-05-24
have you...

"uninstall gimp or maybe even both and then reinstall only gimpshop..."

also keep in mind that your trying to install a package that has'nt been updated since 2007 to the latest (and still under testing)  Karmic Koal, may not even work...

and last...

"installed GIMPshop with a .deb package? Perhaps you could run me through what you did."

[http://www.google.com/search?q=installing+deb+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=installing+deb+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by emotionlovesyou on 2009-05-24
> **jerrrys said:**
> have you...

"uninstall gimp or maybe even both and then reinstall only gimpshop..."

also keep in mind that your trying to install a package that has'nt been updated since 2007 to the latest (and still under testing)  Karmic Koal, may not even work...

and last...

"installed GIMPshop with a .deb package? Perhaps you could run me through what you did."

[http://www.google.com/search?q=installing+deb+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=installing+deb+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

I just realized today that I actually updated to 9.04 and not 9.10 so it should be stable.

Anyway, I just downloaded the .deb package for GIMPshop, double clicked it from the desktop which is where it downloaded to, clicked "install package" or whatever it says, and followed the steps. Then I ran GIMP and nothing had changed. That's when I thought maybe GIMPshop is supposed to run on it's own so I un-installed GIMP and just ran gimpshop from command. Nothing happens.

Is there another way to install GIMPshop. I always use .deb packages to install everything cause there's usually no command prompt involved and I think it's easier.

Thanks for your help on this by the way

---

### Post by jerrrys on 2009-05-24
i could not find a "how to" for 9.04. but maybe this will help you...

[http://www.ubuntugeek.com/howto-install-gimpshop-in-ubuntu-hardy.html](http://www.ubuntugeek.com/howto-install-gimpshop-in-ubuntu-hardy.html)

---

### Post by arvin555 on 2009-08-21
Hi, I am a new ubuntu user though this topic is a bit old, I'd like to add a bit more info I recently learned from my own install.  I found Jerrry's link very helpful when I installed Gimpshop.  Here is what I did.

1. Uninstalled Gimp first (not sure if necessary, but I did).
2. Downloaded and installed Gimpshop as per instructions in 
[http://www.ubuntugeek.com/howto-install-gimpshop-in-ubuntu-hardy.html](http://www.ubuntugeek.com/howto-install-gimpshop-in-ubuntu-hardy.html)

3. I am using Ubuntu Jaunty, so the deb (gimpshop ver. 2.2 11-1) file automatically opened with "package installer"

4. The important point I almost missed, is that after the installation, you have to run gimpshop by opening terminal and typing gimp .  Gimpshop should finish installation/setup.  

5. Lastly I was surprised that there was no new icon in Applications/Graphics  or anywhere at all.  I had to use terminal to launch gimpshop!

6. Only today though I found some info about Launchers, and so I did the following steps....

a. Go to System/Preference/Main Menu   (Ubuntu Jaunty) or a KDE Menu editor.

b. In the Main menu (program) I clicked on Graphics then on the right hand side of the screen I clicked add.

c. Entered:  Type:  Applicatiton  Name: Gimpshop  Command: Gimp  and I clicked on the icon on the left side of the window, and changed, I tried to find the icon for Gimp, I found it, but if it is not there, then try a different icon or download an svg file somewhere (sorry I wouldn't even bother).

d. click OK and then close "Main menu" editor.  Check in Applications/Graphics if you have your launcher already.

I am not sure why an install for Gimpshop is this complicated, I was hoping for an easy install package, but that is what we get for now, and I really wanted a photoshop looking interface to help me get used to Gimp.

TTFN
Arvin

---

### Post by haddog on 2010-03-16
Used this post to install Gimpshop on Ubuntu Netbook Remix 9.10, which is a variation of Karmic Koala 9.10. Gimp appears not to have been installed in UNR by default. From a terminal I ran sudo apt-get remove. Received a message that Gimp was not installed. I then followed the instructions at this site:

  [http://www.ubuntugeek.com/howto-install-gimpshop-in-ubuntu-hardy.html](http://www.ubuntugeek.com/howto-install-gimpshop-in-ubuntu-hardy.html)

I installed the Gimpshop deb file from the terminal as instructed in the above link. Run Gimpshop the first time also from terminal as per the instructions by typing gimp to complete the installation of Gimpshop. 

Next I created a launcher menu item for Gimpshop. I first found and dloaded an icon for the launcher. Got my icon from here:

 [http://4.bp.blogspot.com/_f1pA_pj4ZQ8/R7NBG4oru1I/AAAAAAAAAzU/_D3n6C-Qaz4/s200/gimp_icon_sm.jpg](http://4.bp.blogspot.com/_f1pA_pj4ZQ8/R7NBG4oru1I/AAAAAAAAAzU/_D3n6C-Qaz4/s200/gimp_icon_sm.jpg)

TIP: When you save the file for the icon, change the .jpg extension to .svg

To create launcher in UNR 9.10 I went to System> Main Menu> Graphics> +New Item. This will open the Launcher Properties. Next I typed the following in the applicable entry fields:

Name: Gimpshop
Command: gimp

Click on the icon button to the left in the Launcher Properties and navigate to the icon file you dloaded, select it. (Note. You don't have to use a launcher. If you don't want to use a launcher you can ignore all the rest of this post and open Gimpshop by typing gimp from a terminal.) Use the Close button once you have completed launcher setup. You should now have a Gimpshop launcher located in the panel under Graphics. Click to launch Gimpshop and get to Gimpin!

---

### Post by Rasa1111 on 2010-03-17
> I really wanted a photoshop looking interface to help me get used to Gimp. how would that help one get used to GIMP? 
wouldnt it really only be helping them "continue using photoshop"? 

 the best way to get used to GIMP is to use GIMP,
as it is. ;)

 I started using it a few years ago though when I still had wiNdOws and PS. 

 I dont see how anyone could ever get used to GIMP by using a PS interface..
what, you going to use the PS interface forever? 

 youll be just as confused if you "learn gimp" with "gimpshop" 
and then stop using gimp shop and start using GIMP.... so whats the point? 
unless of course one didnt really care to ever learn the actual program; 
 then go for it. lol  :KS

---

### Post by haddog on 2010-03-17
I am actually pretty well versed in GIMP. But I had someone who wanted to be able to use GIMP quickly and they were familiar with PS already. They didn't want to go thru the learning curve. So there it is...

I'm with you on learning to use GIMP as GIMP. I have at least convinced them to try Ubuntu :-)

---

### Post by Ukebane on 2010-03-22
I'm a hardened Photoshop user, but since I'm no longer in college I'm no longer the proud owner of a copy.

Since I'm not easily depressed I decided to try Gimpshop, only to get the following errors after launching it and playing with it for a minute or 5.

```

/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:9649): LibGimpBase-WARNING **: gimp: wire_read(): error

***MEMORY-ERROR***: gimp[9649]: GSlice: assertion failed: sinfo->n_allocated > 0
gimp: terminated: Aborted
ukebane@nofailxdw2:~/Downloads$ 
(script-fu:9651): LibGimpBase-WARNING **: script-fu: wire_read(): error

```

Any idea what could cause this?

---

### Post by eksasol on 2010-03-24
I never felt the need to use Gimphoto or Gimpshop, but this is how I organize my GiMP interface:
[[IMG]http://i20.photobucket.com/albums/b233/eksasol/th_gimp.jpg[/IMG]]("http://s20.photobucket.com/albums/b233/eksasol/?action=view&current=gimp.jpg")

Since the version 2.8 is going to have single windows, this layout will make it look just like Photoshop.

---

### Post by haddog on 2010-04-02
> **Ukebane said:**
> I'm a hardened Photoshop user, but since I'm no longer in college I'm no longer the proud owner of a copy.

Since I'm not easily depressed I decided to try Gimpshop, only to get the following errors after launching it and playing with it for a minute or 5.

```

/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:9649): LibGimpBase-WARNING **: gimp: wire_read(): error

***MEMORY-ERROR***: gimp[9649]: GSlice: assertion failed: sinfo->n_allocated > 0
gimp: terminated: Aborted
ukebane@nofailxdw2:~/Downloads$ 
(script-fu:9651): LibGimpBase-WARNING **: script-fu: wire_read(): error

```

Any idea what could cause this?

I just installed on another pc and have had no issues. Followed the instructions as per the links in this post.

---

### Post by 23dornot23d on 2010-04-02
I must admit I agree with the previous assessment ....  by Rasa1111

why use Gimpshop ........ use GIMP


Its almost as crazy as a Gimp user going to windows and having a interface to convert
Photoshop menus to look like GIMP menus  .......

Now that would be funny ... ROFL ......... :D ,,,,,, 


Gimpshop does it work ? and when GIMP 2.8 comes out will you be ready to make the change ...  > ? ....  if you ever get it running properly that is  ...... 

Why bother ...........

Wasn't this interface designed in 2006 to work with a very old version of GIMP ..... 

Unless they keep updating it every time a new version of GIMP comes out ...... its never going to be up-to-date ...... please just use GIMP as it is ........ 

its not that difficult.

or carry on if you just enjoy messing about ............ ok have fun ......... :)

---

