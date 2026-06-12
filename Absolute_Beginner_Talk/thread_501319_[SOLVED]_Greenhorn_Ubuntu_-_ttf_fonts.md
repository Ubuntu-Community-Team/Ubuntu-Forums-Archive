---
title: "[SOLVED] Greenhorn Ubuntu - ttf fonts"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Andavane on 2007-07-15
Dear Team

I am my third day into Ubuntu 7.04 "Feisty Fawn" and am very pleased with how things have gone thus far.

Unfortunately I need to use Windows for inter co-operation with colleagues, as I need to share the folder with all my main sub-folders with my colleague. I do this by using a synchronization program in Windows which matches up an exact copy of this folder. My colleague on Vista then uses these files and we can both view on separate PC's

In the set-up listed below, this Main Folder is stored in "Hard Drive 0", in a partition which has been formatted with FAT32. (I got used to Open Office for over a year, to smooth this planned transition).

One problem I have found is that all the fonts are different; it seems strange as i have various templates set-up in Open Office (ttf fonts).  Is it possible for me to retain ttf fonts in Ubuntu?

Kind Regards

John

many thanks for all help already extended.


[color=brown]IBM Think-Centre A-50 : 40 Gb

Hard Drive 0) Windows XP-Pro
Hard Drive 1) Ubuntu 7.0.4 &#8220;Feisty Fawn&#8221;, : 110 Gb[/color]

---

### Post by dptxp on 2007-07-15
I think that you open Nautilas in terminal and copy fonts from Windows to the fonts folder.

---

### Post by ron999 on 2007-07-15
Hi
This is the method I was taught.
There's a folder in the system at usr/share/fonts which holds folders of fonts.
You should create another folder in there called myfonts (for example).
Then copy and paste any fonts you like into this new folder.
Then issue this command into a terminal:-
**sudo fc-cache -f**
Then your new fonts will be available to use.
8)

---

### Post by Andavane on 2007-07-15
> There's a folder in the system at usr/share/fonts which holds folders of fonts.
You should create another folder in there called myfonts (for example).
Then copy and paste any fonts you like into this new folder.
Then issue this command into a terminal:-
**sudo fc-cache -f**
Then your new fonts will be available to use.

Thank you very much.

I am very much afraid that my horns are so green that I do not know how to "go into a terminal". :mad:

But I am a willing learner :-)

Thank you for your patience in this... 

Kind regards

John

---

### Post by ron999 on 2007-07-15
To get at a terminal.
Click on 'Applications' at top of screen.
Then click 'Accessories'.
Then click 'Terminal'. - it's icon is a small tv set.

---

### Post by Andavane on 2007-07-15
Much obliged

       /\

---

### Post by Andavane on 2007-07-20
> **ron999 said:**
> Hi
This is the method I was taught.
There's a folder in the system at usr/share/fonts which holds folders of fonts.
You should create another folder in there called myfonts (for example).
Then copy and paste any fonts you like into this new folder.
Then issue this command into a terminal:-
**sudo fc-cache -f**
Then your new fonts will be available to use.
8)
Hello.
I'm not allowed into the usr folder.
When I R/click on permissions in properties it tells me:
"You are not the owner, so you can't change permissions".
Everything is greyed out, and I can't get much sense out of "Help".
The object of this exercise is to have the fonts I use in Windows, working in Ubuntu;
Looking forward to finding out what to do.
Regards
John

---

### Post by testube_babies on 2007-07-20
This page should hopefully explain it:

[http://www.smorgasbord.net/2007/06/29/installing-windows-ttf-true-type-fonts-in-linux/](http://www.smorgasbord.net/2007/06/29/installing-windows-ttf-true-type-fonts-in-linux/)


Just change "/home/user/Desktop/*.ttf" to "/[path to your Windows font folder]/*.ttf"

---

### Post by Andavane on 2007-07-20
Thank you for the link.
The fonts are now ready in a folder on the desktop.
An extract from the page you quoted:
> Just download the fonts you want from free online web sites and archives (listed below), if necessary - unzip them to the desktop or another directory of your choice.

Then create a directory for your new fonts where the fonts are stored on your system. This is the location in Ubuntu Linux - your Linux distribution may be similar:
The "Create Folder" Option in
/usr/share/fonts
is greyed out.
When R/clicking on the "fonts" folder, I am again told that I am not the owner, and I do not have permission. 
kind regards
John

---

### Post by testube_babies on 2007-07-20
The command "sudo mkdir /usr/share/fonts/myfonts" makes the directory in /usr/share/fonts.  It doesn't say so in the tutorial, but this command should be issued in a terminal.  The menu option is greyed out normally because you need root permissions to edit it.  Sudo gives you these permissions.

For the same reason, copying to that folder will not work!  So, to get root permissions, you have to use sudo again:  "sudo cp ~/Desktop/[font folder]/*.ttf /usr/share/fonts/myfonts" to copy all of the fonts from [font folder] on your desktop to the correct folder.

Then you just need to update the font cache, which is done with "sudo fc-cache -f"

---

### Post by gn2 on 2007-07-20
Just cheat and get extra fonts through [www.getautomatix.com](www.getautomatix.com) it saves all the mucking about.

If you experience any difficulty with Automatix (unlikely) it has it's own support forum.

---

### Post by Andavane on 2007-07-20
Thank you.
When I typed in:

sudo mkdir/usr/share/fonts/myfonts

it asked for my password.

When I typed it in, the cursor seemed to move in a funny way.
Then it said:

sudo: mkdir/usr/share/fonts/myfonts: command not found


Regards

John

---

### Post by testube_babies on 2007-07-20
I've had nothing but problems with Automatix.  It messes up dependancies and permissions; when it comes time to update your system nothing works anymore.  Just my experience, though, since plenty of users couldn't live without it.

Here's the official Automatix spiel from the Ubuntu Guide, which pretty much sums it up for me:
"Automatix2 is a proprietary script that tries to install some software, and often fails and breaks systems. The Ubuntu community doesn't provide support for it, and we strongly discourage its use. Problems caused by Automatix are often hard to track and solve, and it might sometimes be easier to install a fresh copy of Ubuntu."

-------------------------------------------------------------------------------------------------------------------------------

On a different note, if you really want to be able to use root permissions in nautilus, you can run it with "gksudo nautilus".  Just be careful; you could potentially ruin your system if you move/change the wrong file.

---

### Post by testube_babies on 2007-07-20
> **Andavane said:**
> Thank you.
When I typed in:

sudo mkdir/usr/share/fonts/myfonts

it asked for my password.

When I typed it in, the cursor seemed to move in a funny way.
Then it said:

sudo: mkdir/usr/share/fonts/myfonts: command not found


Regards

John

There has to be a space between mkdir and /usr/share/fonts/myfonts

---

### Post by gn2 on 2007-07-20
> **testube_babies said:**
> I've had nothing but problems with Automatix. 

My experiences are quite the reverse, it has never given me a single problem on either my desktop PC or laptop.

It is excellent in my opinion, but I accept that others may not be so lucky with it as I have been.

---

### Post by Andavane on 2007-07-20
Dear Sir
When I type in:

 suido cp~/Desktop/fonts_I_use/*.ttf/usr/share/fonts/myfonts
 I am again getting
"command not found"

Regards

John

---

### Post by testube_babies on 2007-07-20
> **Andavane said:**
> 
 suido cp~/Desktop/fonts_I_use/*.ttf/usr/share/fonts/myfonts

:) Mind the spaces.
```
sudo cp ~/Desktop/fonts_I_use/*.ttf /usr/share/fonts/myfonts
```

There should be a space after cp and a space after *.ttf

Similarly,```
sudo fc-cache -f
```

Also note that you can highlight (select) the command text and then middle-click in the terminal for a quick copy-and-paste.

---

### Post by testube_babies on 2007-07-20
Here's a good guide on basic terminal syntax (highly recommended and slightly overwhelming):
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

---

### Post by Andavane on 2007-07-20
Thank you Sir
When I type as above (being very careful with all the spaces) I get:

sudo cp ~/Desktop/fonts_I_use/*.ttf /usr/share/fonts/myfonts
cp: cannot stat `/home/andavane/Desktop/fonts_I_use/*.ttf': No such file or directory

I will go to read the thread you suggest, but my head is hurting a bit from this. (I am nearly 58 years old - sorry!)

Regards

John

---

### Post by testube_babies on 2007-07-20
> **Andavane said:**
> sudo cp ~/Desktop/fonts_I_use/*.ttf /usr/share/fonts/myfonts
cp: cannot stat `/home/andavane/Desktop/fonts_I_use/*.ttf': No such file or directory

Well, there are a few more simple problems we can run into here:

1)  Are all of the fonts actually in the fonts_I_use folder or are they in subdirectories?
2)  Do they all have .ttf extensions?  Note that Linux is case-sensitive, so TTF is different than ttf.

I suspect Windows renames installed fonts to TTF...this would change the command to
```
sudo cp ~/Desktop/fonts_I_use/*.TTF /usr/share/fonts/myfonts
```

Also, I'm not sure you caught my late edit on an above post:
you can highlight (select) the command text and then middle-click in the terminal for a quick copy-and-paste.

---

### Post by testube_babies on 2007-07-20
Or, if you get sick of all this nonsense, you can just copy EVERYTHING from the fonts_I_use folder into the system fonts folder and be done with it:
```
sudo cp ~/Desktop/fonts_I_use/* /usr/share/fonts/myfonts
```

---

### Post by graigsmith on 2007-07-20
that method is good for fonts you can use with every user. but if you just want to add a few fonts to your own user account.

open your home folder in nautilus, and use the key combo ctrl-h, to show hidden files. 

you should be able to see a folder called .fonts   the . in front of it makes it hidden.  if you dont have this folder, just make a new folder called ".fonts"  then drop whatever font you want to use right in there. and it should work.

---

### Post by Andavane on 2007-07-20
> 
I suspect Windows renames installed fonts to TTF...this would change the command to
Code:

sudo cp ~/Desktop/fonts_I_use/*.TTF /usr/share/fonts/myfonts

Also, I'm not sure you caught my late edit on an above post:
you can highlight (select) the command text and then middle-click in the terminal for a quick copy-and-paste.
__________________

Thank you. I had indeed missed it.
And I did "middle-clicking" for the first time!

However (to quote from the command terminal) I got this:

[color=blue]andavane@andavane-ibm:~$ sudo cp ~/Desktop/fonts_I_use/*.TTF /usr/share/fonts/myfonts
Password:
cp: cannot stat `/home/andavane/Desktop/fonts_I_use/*.TTF': No such file or directory[/color]

btw two of the fonts were *.TTF so I removed them.

I can try one more thing tonight. I may have a read on the terminal thingie, and then I think, some sleep and tackle it again tomorrow.

I feel I have learned today.

---

### Post by testube_babies on 2007-07-20
Alright, I think this should be the definitive end of this problem.

First, let's undo everything we've done so far, to start fresh.  These commands will delete /usr/share/fonts/myfonts and all of the fonts in your font folder on your desktop:```
rm ~/Desktop/fonts_I_use/*
sudo rm -Rf /usr/share/fonts/myfonts
```

Next, copy all of the Windows fonts you want to use into the fonts_I_use folder on your desktop.  You can copy any fonts you want, regardless of the file extension (ttf vs. TTF).

Now, create the myfonts folder and move all of the fonts from fonts_I_use to myfonts:```
sudo mkdir /usr/share/fonts/myfonts
sudo mv ~/Desktop/fonts_I_use/* /usr/share/fonts/myfonts
```

Then, update the font cache:```
sudo fc-cache -f
```

Now fire up OpenOffice.org Writer, and you should hopefully be able to use your Windows fonts.  You can also delete the fonts_I_use folder (which should be empty).

---

### Post by Andavane on 2007-07-20
> 
Code:

rm ~/Desktop/fonts_I_use/*
sudo rm -Rf /usr/share/fonts/myfonts

Next, copy all of the Windows fonts you want to use into the fonts_I_use folder on your desktop. You can copy any fonts you want, regardless of the file extension (ttf vs. TTF).

Now, create the myfonts folder and move all of the fonts from fonts_I_use to myfonts:
Code:

sudo mkdir /usr/share/fonts/myfonts
sudo mv ~/Desktop/fonts_I_use/* /usr/share/fonts/myfonts

Then, update the font cache:
Code:

sudo fc-cache -f

Now fire up OpenOffice.org Writer, and you should....

OK Sir thank you very much.
Eyelids are now drooping, so will undertake this first thing tomorrow morning.
Hopefully this will be a resolution to the problem;
I'll report back on the outcome.
Good night...
kind regards
John

---

### Post by Andavane on 2007-07-21
> **testube_babies said:**
> Alright, I think this should be the definitive end of this problem.

First, let's undo everything we've done so far, to start fresh.  These commands will delete /usr/share/fonts/myfonts and all of the fonts in your font folder on your desktop:```
rm ~/Desktop/fonts_I_use/*
sudo rm -Rf /usr/share/fonts/myfonts
```

Next, copy all of the Windows fonts you want to use into the fonts_I_use folder on your desktop.  You can copy any fonts you want, regardless of the file extension (ttf vs. TTF).

Now, create the myfonts folder and move all of the fonts from fonts_I_use to myfonts:```
sudo mkdir /usr/share/fonts/myfonts
sudo mv ~/Desktop/fonts_I_use/* /usr/share/fonts/myfonts
```

Then, update the font cache:```
sudo fc-cache -f
```

Now fire up OpenOffice.org Writer, and you should hopefully be able to use your Windows fonts.  You can also delete the fonts_I_use folder (which should be empty).

...The definitive end indeed. Very grateful. Two points:
1) When I typed it in, it would not allow (sorry I lost the message as system froze up afterwards)
2) When I highlighted what you wrote and then middle-clicked it into the command line, it all worked just fine.

Ergo, there must be something wrong with my typing (even though I was as careful as possible.
I wonder if the error was the two separate lines, viz:

```
rm ~/Desktop/fonts_I_use/*
sudo rm -Rf /usr/share/fonts/myfonts
```

Can you tell me what I was doing wrong?
Kind regards
John

---

### Post by testube_babies on 2007-07-21
I'm not sure...

Two lines implies that you can do one command after the other (ie, hit 'Enter' after each line).  When you select and middle click, the terminal automatically parses the newline and hits Enter for you.  Maybe this is what happened?

Well, at any rate, I'm glad you've solved your problem.  See you around,
testube

---

### Post by Andavane on 2007-07-22
You have baptised me 
Thanks
John                 :-({|=

---

### Post by pushkarajapte on 2007-07-26
Hi,
I am another greenhorn who has moved to LInux after wandering in and out of windows for more than a decade. I am pleased to be part of the Ubuntu community. I have also been trying to install the ttf fonts.
It worked till I could copy the ttf fonts in the myfonts folder. But after the last command (that is, sudo fc-cache -f) I get the following message.

Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed

Please help,
Thanx

---

