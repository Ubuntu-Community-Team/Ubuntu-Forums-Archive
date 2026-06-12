---
title: "help me on wine problem"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by saurabh kakkar on 2007-08-04
hi
  i have just installed wine on my ubuntu 7.04 from the terminal but i dont know how to use it also no help is comming as when i 

am opening wine help browser nothing is coming also a folder has appeared in applications above accessories having name wine 

its sub folder is programs having winrar which i tried to run on wine how can i remove this . i have tried wine software uninstaller 

but its not showing any thing plz help

and do tell me where i can locate wine folder ?

plz help

---

### Post by atomkarinca on 2007-08-04
wine folder is in your home folder. open your home folder and hit ctrl+h you can see it as .wine.

the easy way to open files using wine is this: in a terminal or hit alt+f2 and type
```
winefile
```
open your c: folder and browse through program files. when you find the exe file double-click it.

---

### Post by saurabh kakkar on 2007-08-04
plz help me on my other Questions also

---

### Post by atomkarinca on 2007-08-04
for uninstall:
in a terminal or with alt+f2 type
```
winecfg
```
open "drives" tab and see the c: folder, on the right of it there is the actual location of the c: drive. open that folder from places and find "Program Files" folder. to uninstall just delete the  folder of the software.

or for wine uninstaller
```
uninstaller
```

---

### Post by saurabh kakkar on 2007-08-04
thanks for the reply uninstaller is not showing winrar also no help is comming as when i am opening wine help browser nothing is 

coming 

waiting for reply

---

### Post by atomkarinca on 2007-08-04
how exactly did you install wine? i mean what did you type in the terminal to install? because it seems it's not installed properly.

---

### Post by saurabh kakkar on 2007-08-04
as i am new to linux so i installed using terminal command sudo apt-get install wine

---

### Post by atomkarinca on 2007-08-04
```
winefile
```
type this in a terminal, do you have the wine browser started? if no, what is the output?

---

### Post by saurabh kakkar on 2007-08-04
it shows something like this then wine browser startes

root@ubuntu:/home/saurabh# winefile
wine: creating configuration directory '/root/.wine'...
libGL error: drmMap of framebuffer failed (Invalid argument)
libGL error: reverting to (slow) indirect rendering
libGL error: drmMap of framebuffer failed (Invalid argument)
libGL error: reverting to (slow) indirect rendering
libGL error: drmMap of framebuffer failed (Invalid argument)
libGL error: reverting to (slow) indirect rendering
wine: '/root/.wine' created successfully.
libGL error: drmMap of framebuffer failed (Invalid argument)
libGL error: reverting to (slow) indirect rendering
libGL error: drmMap of framebuffer failed (Invalid argument)
libGL error: reverting to (slow) indirect rendering

---

### Post by ekravche on 2007-08-04
get automatix and install wine using automatix. You can get instructions here [http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38) That's what I've done and it runs fine for me

---

### Post by atomkarinca on 2007-08-04
why do you use terminal as root? type exit and drop back to your user.

---

### Post by saurabh kakkar on 2007-08-04
sir i am not getting what u r saying  tell me the exact steps plz bear with me 

also i have uninstalled wine from my sys but wine folder above accessories still exist with sub folder programs whose sub folder is 

winrar (though its not working ) how to remove this plz see the screenshot

[IMG]http://img400.imageshack.us/my.php?image=screenshotdesktoprx2.png[/IMG]

[http://img400.imageshack.us/img400/9804/screenshotdesktoprx2.png](http://img400.imageshack.us/img400/9804/screenshotdesktoprx2.png)

---

### Post by atomkarinca on 2007-08-04
alright, i'm bearing with you but i have some questions first.
- do you want to install wine?
- do you want to remove winrar?

---

### Post by saurabh kakkar on 2007-08-04
> **atomkarinca said:**
> alright, i'm bearing with you but i have some questions first.
- do you want to install wine?
- do you want to remove winrar?

no i dont want to install wine again as of now will install later 

yes i want to remove winrar and wine folder

---

### Post by atomkarinca on 2007-08-04
delete your wine folder:
```
rm -f -R .wine
```
you may need sudo. (sudo rm -f -R .wine)

---

### Post by saurabh kakkar on 2007-08-04
> **atomkarinca said:**
> delete your wine folder:
```
rm -f -R .wine
```
you may need sudo. (sudo rm -f -R .wine)


sir i have tried these but noting is happening i am still able to see wine folder above accessories plz help

---

### Post by Chad.S on 2007-08-04
To get rid of the menu icon for wine, right click on the main ubuntu icon and click "edit menus". Then, uncheck the wine folder item and hit close. It should be gone from the menu then.

---

### Post by atomkarinca on 2007-08-04
~.config/menus/applications-merged
this folder contains those wine shortcuts on the menu, you can delete the ones with wine in their names.

---

### Post by atomkarinca on 2007-08-04
> **Chad.S said:**
> To get rid of the menu icon for wine, right click on the main ubuntu icon and click "edit menus". Then, uncheck the wine folder item and hit close. It should be gone from the menu then.

this is not a solution on the long run. they stay on your machine but you just make them invisible.

---

### Post by saurabh kakkar on 2007-08-04
i would like to thank both of u for helping this noob nd solving my problem :)

 can u tell me how to install nd use wine properly .

---

### Post by atomkarinca on 2007-08-04
you can use applications > add/remove
type wine and you can see wine windows emulator on the list. select and click apply. there shouldn't be problems.

---

### Post by superstylin on 2007-08-04
I think the wine on the Ubuntu repo's is outdated, it shows as version 9.33 or something, and the current version available is 9.42! So, I would suggest going to the WINE website, you just copy 2 lines of stuff into your terminal which will add the official WINE repo where you can get the latest versions for Ubuntu!

:P

:)

---

### Post by dorath on 2007-08-04
The two lines *superstylin* mentions can be found [here](http://winehq.org/site/download-deb).

Be sure to check out the [Wine Application Database](http://appdb.winehq.org/)!  There you can get an idea if the application(s) you'd like to use work with WINE, and how well they work.  Often you can also find tips from other users on getting things to work.

Also, if you're not comfortable with command line stuff then just use Add/Remove.  Sure the version might not be the newest but it's a start.  After you get more comfortable you can grab the latest verstion too, it's not an irriversable choice. ;-)

---

