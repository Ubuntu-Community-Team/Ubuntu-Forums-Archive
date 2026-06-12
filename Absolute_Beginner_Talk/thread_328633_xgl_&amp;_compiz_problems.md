---
title: "xgl &amp; compiz problems"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by Skidlz on 2006-12-31
I have a Nvidia GeForce 6200 512Mb card. I have had to format after updating to 6.10 and trying to install xgl and compiz. Some how it removed all window border and made it impossible to use. I have down graded to 6.06 again and would like some help with the xgl part. What is the easy way of doing it? I can't find the deb files anywhere and apt-get can't find them. I don't consider myself a total noob so you don't need to go too slow but easy is better. I have read most if not all of the how tos but had no success(.probably my own fault) ](*,) Any ideas? :confused: 

Thank You!

---

### Post by tc48 on 2006-12-31
same problem here with xgl... no window borders with the close minimize and maxamize right?  and you cant move windows either.. i made a thread about it too.. still no response..

---

### Post by Jussi01 on 2006-12-31
Check out this thread, it may have some answers for you. 

[http://ubuntuforums.org/showthread.php?t=320168&page=2&highlight=window+borders+compiz](http://ubuntuforums.org/showthread.php?t=320168&page=2&highlight=window+borders+compiz)

Oh, and remember you can use the search - it came up with a load of different threads for me ;)

---

### Post by Skidlz on 2006-12-31
> **tc48 said:**
> same problem here with xgl... no window borders with the close minimize and maxamize right?  and you cant move windows either.. i made a thread about it too.. still no response.. Exactly! It also would not let me change what window was on top. :( Did you get any of the other features to work? My system was only missing the bars and gained nothing.

Oh and my card is AGP8X if that matters...

---

### Post by mahiyar on 2006-12-31
Just installed berryl today, of course there were a few prob;em like what u described. I just closed the windows w/o title and opened new session. Of course yours could be more complicated, but this problem typically happens when switching over from Gnome "metacity" to berryl desktop. Typically u can open a terminal and run the >>emerald --replace command, and keep the window open. Later u can move the same command to start up.

---

### Post by Skidlz on 2006-12-31
Did you use a how to? If so what and link. I can't even get xgl. apt-get wont find it and the source wont compile. What did you do?

---

### Post by mahiyar on 2006-12-31
Unfortunately I have 6.1 edgy som my steps wony apply, however I followed the wiki Ubuntu guide. A similar guide with a link for installation and all is here [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29)

---

### Post by mahiyar on 2006-12-31
I use 6.10 edgy so my steps would not apply, however I used the Wiki guide to the letter for installation. A similar guide for installation of compiz/Beryl is here [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29)

---

### Post by Skidlz on 2006-12-31
Ok. Thank you!

---

### Post by Skidlz on 2006-12-31
I got compiz installed but I get the old "GLX_EXT_texture_from_pixmap is missing" message.
What will fix it?

---

### Post by mahiyar on 2006-12-31
try following this link though I must agree it all sounds gibberish to me [http://gentoo-wiki.com/HOWTO_XGL/Troubleshooting#GLX_EXT_texture_from_pixmap_is_missing](http://gentoo-wiki.com/HOWTO_XGL/Troubleshooting#GLX_EXT_texture_from_pixmap_is_missing)

---

### Post by Griffongob on 2006-12-31
I followed the instructions but when I go to run compiz I get 

gnome-window-decorator, Failed to load shadow images
compiz.real: No composite extension

what can I do

---

### Post by Griffongob on 2006-12-31
OK for some reason I cant get ANY of the keyboard shortcuts to work like the expose thing or changing desktops what are the commands and how can I change them?

---

### Post by beamo on 2007-01-01
> compiz.real: No composite extension

I know what causes this error because I had it too. Open your /etc/X11/xorg.conf and look at the very bottom. There should be two lines that read:
```

Section "Extensions"
    Option         "Composite" "Enabled"
```

Yours will say "Composite" "Disabled" 

Just change it to Enabled and save it. Did you edit your xorg.conf file while following the How To? I know the How To I followed made a mistake with this line but that was the only problem I had installing Beryl on 6.10 64 bit. Good luck.

---

### Post by Skidlz on 2007-01-01
It Works Now!! Sweet!!

---

