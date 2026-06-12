---
title: "Slow Internet"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by moose4204l on 2007-10-01
My internet has been going extremely slow for the past two weeks. its taking like a minute to load every page i click to. is there a way to clean things out like windows hidden local services folder that contained a temp and temporary internet folder. 

also is there any way to check and see how much room is left on my laptop from the command line. 

any information about testing the internet or cleaning it out is appreciated. thanks.

---

### Post by alienexplorers on 2007-10-01
Try clearing out your cache and cookies.

---

### Post by moose4204l on 2007-10-01
how do i do that?

---

### Post by Linux_Man on 2007-10-01
Which browser are you using? It is possible it could be that a badly-coded extention has caused Firefox to run slowly, also try clearing your cache or cookies. If all these have failed, try a different browser such as Konqueror or Galeon.

---

### Post by Gwasanaethau on 2007-10-01
Hi there!

First of all, to test your Internet connection speed, you could try [http://www.speedtest.net/]("http://www.speedtest.net/") and select the nearest server to your location.

To delete the browser cache, cookies, etc. (assuming you're using Firefox), go to Edit &#8594; Preferences &#8594; Privacy &#8594; Private Data; and click on 'Clear Now'. You can also get rid of temporary Debian packages that Apt and Synaptic downloaded (a sort of temporary cache) by opening a terminal and typing:
```
sudo apt-get autoclean
```
You might also want to run:
```
sudo apt-get autoremove
```
too as this will remove repository packages that are no longer needed for your current configuration.

Finally, you can use the command 'du' to see how much space a particular folder is using. To check the whole file system without displaying how much space individual folders use, try:
```
sudo du -hs /
```

Hope that helps. Sorry it's so long!

---

### Post by Bloch on 2007-10-01
Tip: try a different browser - dillo is the smallest GUI browser theres is
sudo apt-get install dillo
from the terminal

If he internet is slow on all browsers then it may be your provider.
There are also websites whioch test your connection speed:
[http://www.speedtest.net/](http://www.speedtest.net/)



A command to see your disk free space is 
df

sudo fdisk -l
will show your disk partitions and their sizes

---

### Post by Linux_Man on 2007-10-01
Also, if there is any toolbars that you didn't installed, its possible you have generic Firefox spyware, its incredibly rare but it could happen or the toolbars could just be badly coded

---

### Post by jose158 on 2007-10-01
Are you running Bit torrent? My brother ran it once and my wireless was really slow.

---

### Post by antisocialist on 2007-10-01
well if you remove all your toolbars and set all add ons to dont use (or whatever its called) it should go somewhat faster, to see how much memory you have left go to 
places>computer
choose filesystem
look at bottom left of the window and it will say
**X**items and Xgb/mb free space
that tells you how much space you have

---

### Post by kerry_s on 2007-10-01
> **moose4204l said:**
> how do i do that?

you kidding right?

---

### Post by moose4204l on 2007-10-02
thanks, the clearing of everything did the trick. i knew how to do it from windows because I grew up on that. i just recently switched over to ubuntu and linux to try it out. i like it but people like Kerry_s have to understand that not everyone is a wiz with linux. Also, this is the first time i am using mozilla firefox so in a nice way, hush hush.

thanks again peoples.

:guitar: Rock On!

---

### Post by kerry_s on 2007-10-02
> **moose4204l said:**
> thanks, the clearing of everything did the trick. i knew how to do it from windows because I grew up on that. i just recently switched over to ubuntu and linux to try it out. i like it but people like Kerry_s have to understand that not everyone is a wiz with linux. Also, this is the first time i am using mozilla firefox so in a nice way, hush hush.

thanks again peoples.

:guitar: Rock On!

my apologies if you were offended, i just think if your using a browser, you would have tried the buttons, menus and settings, that's standard for anything not just linux, doesn't take a wiz.

---

