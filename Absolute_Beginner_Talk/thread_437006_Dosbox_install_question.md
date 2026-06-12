---
title: "Dosbox install question"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by David4 on 2007-05-08
Hi, just installed Dosbox using Synaptic, double checked that is installed and it shows on the Synaptic window as installed, where is it? I checked on Applications and folders etc but cannot find it.
I am trying to run a Dos program.
thanks.
David

---

### Post by dannyboy79 on 2007-05-08
it's most likely because dosbox is normally run from a terminal, like wine.

well I am not familar with how dosbox works but if it's to run a dos program than you wouldn't want to add the actual dosbox program to your menu, you'd want to add the full command in order to run your dos command using dosbox similarly to how you would run a wine program. like this:

wine /home/username/Homeworld/homeworld.exe

so, unless dosbox has some kind of gui or whatever that you want to pop open first then point to your dos program, you would want to just add a custom command to your menu by using the menu editor and add something like this

doxbox [options] /home/username/dosprogram

and you can search thru some symbols to pick one you like for the command within the menu editor. i am not aware of dosbox so maybe you can learn more about it by typing 

man dosbox 

to see if it has a manual for it. otherwise gogle it and you might find out more on it.
good luck.

this goes for any apps you install that don't end up showing up in the menu. otherwise, the debian menu normally almost always shows all installed apps, you can install that, then go thru that menu which will be within you normal menu.


sudo aptitude install menu-xdg

sudo dpkg-reconfigure menu

sudo dpkg-reconfigure menu-xdg

then all your apps will be in the debian menu.

---

### Post by David4 on 2007-05-08
thank you Danny gives me a guide, just installed wine, looks will take me some time to work with this.
Appreciate your help
David

---

### Post by DarkN00b on 2007-05-08
Press <Alt>F2 to bring up the Run Application dialog. Enter the word [COLOR="Blue"]dosbox[/COLOR] into it and hit enter. I have mine configured to automount a virtual c:\ drive, a CD drive and a virutal a:\ drive.

BTW - Version 0.70 has been released at the DOSbox website.

---

### Post by David4 on 2007-05-08
Great, have it. now the prgm I have is on a external USB HD, not sure how to access it using the commands, as does not have really a letter such as J D or whatever will be in windows dir.
any ideas 
David

---

### Post by DarkN00b on 2007-05-08
When you plug in your USB HD, what does it show up as?

The command to mount a c:\ is:

```
mount c /path/to/folder/or/drive
```

---

### Post by David4 on 2007-05-08
It shows as WD USB 2
David

---

### Post by DarkN00b on 2007-05-08
Okay. Open a file browser window and go to /media and tell me what is listed there. Once I see what your system sees your drive as, I can give you the command to mount it in DOSbox.

---

### Post by David4 on 2007-05-08
sorry, where is the file browser?

---

### Post by DarkN00b on 2007-05-08
Assuming you are using Gnome, open your home folder and look on the left side of the window. Double click File System, then open the /media folder. Tell me what is listed inside. 

Alternatively you could open a terminal window and type ```
cd /media
ls
``` and tell me what is listed.

We'll get there in a minute. :)

---

### Post by David4 on 2007-05-08
Wd Usb 2

---

### Post by dannyboy79 on 2007-05-08
> **DarkN00b said:**
> Press <Alt>F2 to bring up the Run Application dialog. Enter the word [COLOR="Blue"]dosbox[/COLOR] into it and hit enter. I have mine configured to automount a virtual c:\ drive, a CD drive and a virutal a:\ drive.

BTW - Version 0.70 has been released at the DOSbox website.

why wouldn't you just add the command to your menu or your desktop so instead of having to first click alt-f2 and then enter dosbox, and then hit enter. all you would have to do is hit the menu item or desktop launcher once. everyone's boat floats differently but I am pointing this out because he specifically asked how to add it to his menu, so let's help him add it so that when he clicks on the menu item for dosbox, it'll do what he wants it to do, whether it to mount a virtual c drive or whatever.

---

### Post by DarkN00b on 2007-05-08
Try typing ```
mount c "/media/Wd Usb 2"
``` into DOSbox.

The quotation marks are important because the path /media/WD Usb2 contains spaces which Linux doesn't like. I did this with one of my flash sticks mounted at /media/Memorex UFD and it worked perfectly. Also, make sure you use the exact capitalization that Ubuntu uses or the drive won't be found.

---

### Post by David4 on 2007-05-08
OK, now I have 
Z:\>mount c "/media/WD USB 2"
Drive C is mounted as local directory /media/WD USB 2/
Z:\>

---

### Post by DarkN00b on 2007-05-08
> **dannyboy79 said:**
> why wouldn't you just add the command to your menu or your desktop so instead of having to first click alt-f2 and then enter dosbox, and then hit enter. all you would have to do is hit the menu item or desktop launcher once. everyone's boat floats differently but I am pointing this out because he specifically asked how to add it to his menu, so let's help him add it so that when he clicks on the menu item for dosbox, it'll do what he wants it to do, whether it to mount a virtual c drive or whatever.

Okay. He could do what I did and place a launcher on one of his panels. There is no need for any command line. The launcher only needs to launch DOSbox. He could then extract the attached file into his home folder and automatically mount the drive when DOSbox is launched.

---

### Post by DarkN00b on 2007-05-08
> **David4 said:**
> OK, now I have 
Z:\>mount c "/media/WD USB 2"
Drive C is mounted as local directory /media/WD USB 2/
Z:\>

Are you familiar with the dos prompt? if so, just type c: and hit enter and you will be taken to your new c:\ drive. You may now launch programs to your heart's content.

---

### Post by David4 on 2007-05-08
I am familiar with dos prompt, however it tells me Drive C is mounted but I get the 
Z:\> prompt and am stuck on it as cannot change dir to the c: I need to enter the dos file.exe 
David

---

### Post by LaRoza on 2007-05-08
Are you trying to "cd c:" or are you typing "c:"?

---

### Post by DarkN00b on 2007-05-08
/\ Exactly. All you should need to do is type c: and hit enter. There is no need for the cd command.

---

### Post by kosmic on 2007-05-08
Yes in dos when you want to change Partitions you just type ( c: ) no need to type (cd) if you use cd c: it will return an error

---

### Post by David4 on 2007-05-08
right, got it, now I have my c: prompt, 
the prgm I try to access is
Ultra9
has an exe file called ultra9.exe
question is how do I go from my c:\> prompt to that file?

---

### Post by DarkN00b on 2007-05-08
You have to change directories to where the file is located. For example if the file is located in a directory called ultra9 then you would type in:

```
cd\ultra9
```

then once you are in the correct directory, you can run your program.

---

### Post by LaRoza on 2007-05-08
To get a list of directories:
```

DIR

```

If you see what you want, type in the name and press enter, if you see the folder its in:

```

cd theFolder

```

If you know the name of a file, this will find it:

```

DIR ultra9.exe

```

You can do it in one step:

```

c:\>folder\subfolder\file.exe

```

I am giving the other commands because you will be using them a lot if you use DOS

---

### Post by anaconda on 2007-05-08
Huh.. you guys are making the use of dosbox really hard..

Feels like I am not using the same program at all. Because I think it is as easy as can be.

I just right-click the exe-file in nautilus and select "open with dosbox" and that is all.. :)

The first time I had to select "open with Other aplication" and "use custom command" and type dosbox on the field. 
the next time you will only need to right-click and select "open with dosbox"

If you use dosbox this way it doesn't matter where the .exe file is. and you wont need to mount anything in the dosbox. The folder where the .exe -file is will be c:

Oh.. and the only other thing you will need to know about dosbos is
Ctrl-F12, which will speed up the emulated processor. You might need to press this quite many times before the game runs fast enough. (depends on the game)
and 
Ctrl-F11 which will slow it down..

---

### Post by David4 on 2007-05-08
just will not work, this file is on
/media/ultra9
but am missing something, as I type
cd/media/ultra9
or 
cd/ultra9
seems to me I am using an incomplete path
David

---

### Post by jjbean on 2007-05-08
This site has shows you how to install a nice GUI for Dosbox.  [COLOR="Red"][UGA]("http://gaming.gwos.org/news.php")[/COLOR]
The site is down right now, our I would give you a direct link to the page. The GUI makes using Dosbox easy as hell.

---

### Post by anaconda on 2007-05-08
I prefer the way I mentioned above, but another easy way is to open a terminal and type:
```
dosbox "/media/usb disk/prince/4D_PRIN.EXE"
```

this would start the prince-game, which I have on my usb disk.. the quates are needed because there is a space in the  "usb disk"

jus change the path in the example to fit your needs.

---

### Post by David4 on 2007-05-08
this may be part of the problem?
finally was able to run the ultra9.exe file BUT
get this error
"This program must be run under Microsoft Windows"
 I am not sure why, when I am in WindowsXP  just switch to Dos command and can run it fine.
David

---

### Post by dannyboy79 on 2007-05-08
> **anaconda said:**
> I prefer the way I mentioned above, but another easy way is to open a terminal and type:
```
dosbox "/media/usb disk/prince/4D_PRIN.EXE"
```

this would start the prince-game, which I have on my usb disk.. the quates are needed because there is a space in the  "usb disk"

jus change the path in the example to fit your needs.

ah man, thank you. I have been trying to tell them to try it this way for the longest, and he could add that as a menu item within his menu. this example should help him understand this a little better. thanks for the input. I also like the nautilus open with, that seems very easy instead of adding a menu item or a launcher somewhere.

---

### Post by jjbean on 2007-05-08
> **dannyboy79 said:**
> ah man, thank you. I have been trying to tell them to try it this way for the longest, and he could add that as a menu item within his menu. this example should help him understand this a little better. thanks for the input. I also like the nautilus open with, that seems very easy instead of adding a menu item or a launcher somewhere.

Thank you to both of you! That is easier than the way I was doing things. I am still new and keep thinking of the Window's way. Sooner our later I will stop ](*,)

Thank you again.

---

### Post by dannyboy79 on 2007-05-08
> **David4 said:**
> this may be part of the problem?
finally was able to run the ultra9.exe file BUT
get this error
"This program must be run under Microsoft Windows"
 I am not sure why, when I am in WindowsXP  just switch to Dos command and can run it fine.
David


try it with wine, it may not be a true dos command. for example, nmap can be run using dos within windows xp but I don't think it's a dos program? not sure about dos and dosbox as I haven't any experience with them, I was only trying to help based on my knowledge of how wine works (emulation just like I thought dosbox was)

---

### Post by David4 on 2007-05-08
T H A N K  
 Y O U  
A L L  
for taking the time 
this was a very intense and rewarding crash course on the use of DOS.
David

---

### Post by David4 on 2007-05-08
Danny, sorry did not see your last post.
I believe  you are correct this program will need wine, looks as DOS, Smells like DOS but somehow needs to work under windows.
That will be another project.
Again
thank you very much
David

---

