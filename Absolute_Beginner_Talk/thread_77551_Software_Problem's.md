---
title: "Software Problem's"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by bigboss2200 on 2005-10-17
Hi Guyz..

1st of all i'd like to say that im a ToTaL NoOoOoOoB in Ubuntu.. and im facing some real problems "well i conceder them as problems while others may find them a pice of cake :) )... but pleeeeeeeease try to make ur answer based in that there is no internet connection coz i dont have any in ubuntu :( 

1 - I have downloaded RealPlayer10GOLD.bin & .rpm .. and i have tried to install them using the Terminal but with no result.. how can i install it ..? 

2 - why i cant install any .rpm packeges..? and y do the command "rpm" is not executing...? and is there any way to install .rpm packeges..?

3 - i can't play any .avi or .mpg or any video or audio formats.. how can i download their libs..? and in which name can i find them..?

4 - while downloading the program "belneder3d" , the help guide included told me to unpack the packege and put .blender in the root folder.. fine.. but it didnt execute when pressing it.. y..? 



well i think those r lllllllllllllllots of questions.. but i loved the ubuntu interface and its login screen.. its better than windows or Fedora in AGES...

thanks for reading.. :)

---

### Post by Swab on 2005-10-17
[QUOTE=bigboss2200]
2 - why i cant install any .rpm packeges..? and y do the command "rpm" is not executing...? and is there any way to install .rpm packeges..?
[/QUOTE]

Ubuntu is based on Debian and as such uses .deb packages.  As far as I know .rpm packages are used on Red Hat based operating systems.

---

### Post by bigboss2200 on 2005-10-17
ok fine.. then what is the sutable extention to download for ubuntu..?!

and final question.. where i can download the realplayer or any other program and install it in ubuntu.?!

thanks for ur quick reply... and sorry for the annoying :)

---

### Post by Brad wilkinson on 2005-10-17
ubuntu uses the _.deb_ format for _packages_.

in the console, that would be _apt-get_, but on the desktop you want _system->administration->synaptic_ for a gui to help you download *packages*. 

if any of those file types you mention have propriatary code (i.e. non-free) then they will not be in the official ubuntu *repositories* (where all the .deb's are stored on the net).

this is to avoid copyright problems.

you could also try the list of howto's or the ubuntu wiki. quite often you will surprise yourself with the things you figure out yourself:D

[try here for starters]("https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29")

---

### Post by ds[de] on 2005-10-17
To install real player (the .bin file), enter the directory where the files are and type 
chmod 755 RealPlayer10GOLD.bin

and then 

./RealPlayer10GOLD.bin

Regards,
ds[de]

---

### Post by odin on 2005-10-17
[QUOTE=bigboss2200]Hi Guyz..

1st of all i'd like to say that im a ToTaL NoOoOoOoB in Ubuntu.. and im facing some real problems "well i conceder them as problems while others may find them a pice of cake :) )... but pleeeeeeeease try to make ur answer based in that there is no internet connection coz i dont have any in ubuntu :( 

1 - I have downloaded RealPlayer10GOLD.bin & .rpm .. and i have tried to install them using the Terminal but with no result.. how can i install it ..? 

2 - why i cant install any .rpm packeges..? and y do the command "rpm" is not executing...? and is there any way to install .rpm packeges..?

3 - i can't play any .avi or .mpg or any video or audio formats.. how can i download their libs..? and in which name can i find them..?

4 - while downloading the program "belneder3d" , the help guide included told me to unpack the packege and put .blender in the root folder.. fine.. but it didnt execute when pressing it.. y..? 



well i think those r lllllllllllllllots of questions.. but i loved the ubuntu interface and its login screen.. its better than windows or Fedora in AGES...

thanks for reading.. :)[/QUOTE]

Well you can use alien to convert rpm packages into deb but I dont know if that's always a good solution cause I had many problems doing that.Many times happened to me that alien said the operation was ok but anything worked as expected.But If you try it ones you get the deb package just typing "dpkg -i "name of the .deb package you just created with alien" the package should be installed.

Anyway I suggest you to install software from the repositories cause it's much easier,no dependencies problems and ,the most important thing, they are meant for ubuntu.If I cant find what I need in the repos I normally prefer to get the tarball (you know the source you normally get in a tar.gz or tar.bz2 format).

If you are new to ubuntu it may help you a lot to have a look in this link:
[www.ubuntuguide.org](www.ubuntuguide.org)

and mostly here at the forums where there are many howto's and people that already had the same problems as you.

---

### Post by UbuWu on 2005-10-17
[QUOTE=bigboss2200]
4 - while downloading the program "belneder3d" , the help guide included told me to unpack the packege and put .blender in the root folder.. fine.. but it didnt execute when pressing it.. y..? 
[/QUOTE]

To install blender (if you are running 5.10/breezy):
Applications -> Add applications -> search for blender -> install

If you are still running 5.04/hoary: System -> administration -> synaptic -> search for blender -> apply

Edit: just saw you don't have internet on this pc, that makes things more complicated than I describe here.

---

### Post by localsly on 2005-10-19
[QUOTE='ds[de]']To install real player (the .bin file), enter the directory where the files are and type 
chmod 755 RealPlayer10GOLD.bin

and then 

./RealPlayer10GOLD.bin

Regards,
ds[de][/QUOTE]

I just wanted to say thanks, you helped me out a little bit here.. and now i am listening to music.. :)

---

