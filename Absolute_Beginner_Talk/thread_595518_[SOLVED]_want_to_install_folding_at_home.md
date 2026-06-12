---
title: "[SOLVED] want to install folding at home"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by bigmonmulgrew on 2007-10-28
Hi how do I get folding at home working, 

How do I install the liknux version, or is it best to use the windows version through wine

---

### Post by Maestro23 on 2007-10-28
> **bigmonmulgrew said:**
> Hi how do I get folding at home working, 

How do I install the liknux version, or is it best to use the windows version through wine

Don't use it myself, but you should be able to download it from their site.  Probably to your Desktop. 

Then right-click on it, Properites, give yourself execution permissions. Try to run it.

*As always, follow the documentation. :smile:

---

### Post by craigyjack on 2007-10-29
its real easy.

download the linux executable, something like FAH504-Linux.exe from folding@home website.

now, youll prob want to create a folder somewhere for your folding@home stuff because it will create several files when you run it. create a fodler in nautilus or do in terminal
```
mkdir ~/Folding@Home
``` 

Move the FAH504-Linux.exe you downloaded into your folder. right click on the file and click properties, go to Permissions tab. make sure that "Allow executing file as program" is checked. (you could chmod the file, but i find graphical way easier for me.)

now open a terminal if you havent yet.
change to folding@home directory
```
cd ~/Folding@Home
```
and then run the executable
```
./FAH504-Linux.exe
```

:)
-Craig

---

### Post by meindian523 on 2007-10-29
> **craigyjack said:**
> 
and then run the executable
```
./FAH504-Linux.exe
```



Linux executable==exe??What's the world coming to?

---

### Post by hyper_ch on 2007-10-29
> **meindian523 said:**
> Linux executable==exe??What's the world coming to?

What's wrong with that? whether a file is executable in linux does not depend on the file extension but on it's properites... but giving an .exe extension to an executable file isn't that far stretched ;)

---

### Post by bigmonmulgrew on 2007-10-29
cheers I now have it working. Oh and thank you for showing me a graphical way most linux users spout off terminal commands as if theyre nothing. To a recent windows convert a gui is a big thing and a terminal is very scary. If I hadnt used DOS when I was a kid I probably would have got stuck with linux scared with then command line.

By the way I assume every time I want to run it I have to enter the command
```
./FAH504-Linux.exe

```

Is there a way to get an icon to automatically open a terminal and run this to make it quicker and easier.

---

### Post by hyper_ch on 2007-10-29
a GUI-way is most often less preferrably as there is no single GUI in linux but multiple...you know, you have ubuntu (gnome), kubuntu (kde), xubuntu (xfce) as distros and there are more (E17, fluxbox, ....)

Furthermore it takes longer to describe something in a GUI:

Open that, change tab, click on that button, select that, tick that checkbox there, go back again, do this, go there, make that

When you get a command for the CLI then it's just copy and paste and it is gui independend and quick. No need for pages and pages of explanations and stuff... no need to adjust it to different guis... just plain old copy'n'paste.

---

### Post by bigmonmulgrew on 2007-10-29
yes I agree the cli is more efficient. But I am trying to convert my dad and the terminal brings him out in a cold sweat, hence whenever I ask for something on the forum I also ask for a gui way too. Its a bother for you guys I know but for ubuntu to really take over windows then it needs to be installable and usable by people like my dad who have no one at hand to support them. My dad has me to show him things and hes eager to learn . For some if they are eager or not to learn they are put off by such an unfamiliar way of doing things.

Personally I like to see more info too. The GUI for F@H in windows gives you much more information than the terminal version is giving me now. I'm not too bothered about watching the model but I do like seeing the rest of the info.

Anyway I have found a way. Just discovered how to make a launcher. Cheers for your help

---

### Post by hyper_ch on 2007-10-29
> **bigmonmulgrew said:**
> but for ubuntu to really take over windows
Do we want that?

> **bigmonmulgrew said:**
> For some if they are eager or not to learn they are put off by such an unfamiliar way of doing things.
Unfamiliarity doesn't mean more complicated. Actually it's quite the opposite with the CLI... once you know how to open the terminal and copy'n'paste into it then you just need to wait for someone giving you the right command. That does actually make it a lot simpler then navigating through hundreds of different menus ;)

---

### Post by bigmonmulgrew on 2007-10-29
personally I prefer cli unless the gui displays more info as many do. When installing the cli is easier IF you know the command. To people moving from a completely GUI based (at the user level anyway) OS to one that makes frequent use of the command line is very intimidating. I think for those of us who grew up with cli or have the technical understanding to adapt to one then moving to using one regularly is a small step. To someone who has grown up with windows and become dependent on a  GUI then it will be much harder. 
My dad is an experiment really on how someone with almost no knowledge of a computer will handle ubuntu. Like your typical dell customer.

His current opinion is that for web browsing there is absolutely no difference at all.
His particular installation experience was very difficult as we've had problems dual booting his raid array.
I'm gonna give him a few weeks to get used to it like it took with XP and then see how he feels.

---

### Post by craigyjack on 2007-10-29
> **bigmonmulgrew said:**
> cheers I now have it working. Oh and thank you for showing me a graphical way most linux users spout off terminal commands as if theyre nothing. To a recent windows convert a gui is a big thing and a terminal is very scary. If I hadnt used DOS when I was a kid I probably would have got stuck with linux scared with then command line.

By the way I assume every time I want to run it I have to enter the command
```
./FAH504-Linux.exe

```

Is there a way to get an icon to automatically open a terminal and run this to make it quicker and easier.

Your welcome. 
In reply to everybody else, I went about graphical way with the permissions because i forget chmod ways sometimes. I like the CLI, but i like GUI too. sometimes GUI is just easier, but i def appreciate the CLI and its easy-to-decribe ways. (dont freak guys, most of my instructions were in CLI lol, only chmod did i go graphical and thats because i forgot the CLI for it) and anyways, my goal was to help this guy out, so dont freak about it. i helped him out and thats what the forums are about.

o hey,. also, what did you do to get the launcher to open a terminal and execute the commands itself. i tried making an "application in terminal" launcher with "cd ~/Folding@Home && ./FAH504-Linux.exe" but that didnt work. could you tell me how to make a launcher that will open a terminal, cahnge directory, and execute the program automatically.

I also wouldnt mind a GUI for the linux folding@home client. the CLI is okay, but after seeing the windows, mac, and PS3 gui's for folding@home, those look great and would love to see that on linux.

[Quote=meindian523]
Linux executable==exe??What's the world coming to?
[/Quote]

dude, stop freaking out. you do realize its just an extension, which doesnt mean anything really except to help the user identify it. Folding@home project is the one that stuck the extension on there, not me; it downloaded that way. but i see nothing wrong with it, its just an extension, and if it helps identify it there is nothing wrong with that. i dont think its anything to freak out. you should know that the extension is negligible in linux. so there is no big deal about it. PLUS, uhm executable, first there letters=exe, so that extension isnt very bad, its a self-explanatory extension that helps the user. be nice and realize its good to help users out. [and if you dont like the exetension, then remove it and dont whine. its easy to remove the extension, i kept it in post because thats how it dlded from fold@home website)

---

### Post by meindian523 on 2007-10-29
> **craigyjack said:**
> 
dude, stop freaking out. you do realize its just an extension, which doesnt mean anything really except to help the user identify it. Folding@home project is the one that stuck the extension on there, not me; it downloaded that way. but i see nothing wrong with it, its just an extension, and if it helps identify it there is nothing wrong with that. i dont think its anything to freak out. you should know that the extension is negligible in linux. so there is no big deal about it. PLUS, uhm executable, first there letters=exe, so that extension isnt very bad, its a self-explanatory extension that helps the user. be nice and realize its good to help users out. [and if you dont like the exetension, then remove it and dont whine. its easy to remove the extension, i kept it in post because thats how it dlded from fold@home website)

Hey cool down,dude,I'm not freakin out nor am I whining,I'm sorry if the tone of the post suggested that...and I've nothin against helping the users(otherwise I wouldn't have those beans which I have)......if the tone suggested that....consider the post as withdrawn......:)

---

### Post by craigyjack on 2007-10-29
ok. sorry i kinda freaked too lol. didnt mean to get riled up, it just kinda happened lol. :)

---

### Post by meindian523 on 2007-10-29
> **craigyjack said:**
> ok. sorry i kinda freaked too lol. didnt mean to get riled up, it just kinda happened lol. :)

oh well,happens.....

---

### Post by bigmonmulgrew on 2007-10-29
ok all I did was right click on desktop and click on create launcher.

First option is run as application or as application in terminal. select terminal. Second is name, whatever you like. third is the command just click browse and locate the f@h .exe file.
The downside is that the files associated with it appear in your home directory and not where your F@H executable is. 

I then dropped this icon next to the firefox icon at the top and job done. next time I leave my comp on downloading 1 click to run much easier.

I suspect that in the box where you input your commands you could start by cding into the F@H directory and then run it. But I'm not familiar enough with the command line to do this. I've not used a command line since I was 6 till this month and that was MS DOS

I'm in windows at the min as I'm streaming to my 360 but will have a play tommorrow

---

### Post by craigyjack on 2007-10-30
ok well i already edited this once, but for some reason it didnt accept it, and now i gotta retype this grr.

i realized that i could just make a little bash script to run folding@home client, with one click.

create a new file, put it whereever you want (i put in it my foldingathome folder)
here is the what the file should have:
```

#!/bin/bash
cd ~/Folding@Home
./FAH504-Linux.exe
```

change the directory and executabel to whatever its called on your computer

now create a launcher, "application in terminal", and locate the script fle you just made.

all done. now we get a launcher that will open folding@home with one click, and the files will still be saved your folding@home directory.
-craig

---

### Post by craigyjack on 2007-10-30
uhm, how do you delete a post? i didnt mean to post this post.

---

### Post by bigmonmulgrew on 2007-10-31
lol cheers for the above will give it a try

---

