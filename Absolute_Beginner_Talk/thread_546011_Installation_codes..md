---
title: "Installation codes."
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by T4K3Z0U on 2007-09-08
Can I please get some codes for installing the following:

Skype
Bitcomet or any other good torrent.

Is intervideo windvd compatible with linux?

and limewire code please.

Also is there a page that shows exactly what software can be installed and its codes???

Cheers everyone.

---

### Post by Vadi on 2007-09-08
Try Applications - Add/Remove, and search for that there. If the programs are in the repositories (ie, you can install them with "sudo apt-get install <program>"), they'll definitely show up there.

Usually you'll find the "code" on the official site of the program though.

---

### Post by por100pre1 on 2007-09-08
Add [Medibuntu]("http://www.medibuntu.org/repository.php") repository, then;

```
sudo apt-get install skype
```

No need to use WinDVD, do [this]("http://ubuntuforums.org/showthread.php?t=413624").

---

### Post by T4K3Z0U on 2007-09-08
> **Vadi said:**
> 
Usually you'll find the "code" on the official site of the program though.

I didn't know that. Its my first week of Ubuntu-ing

> **por100pre1 said:**
> Add [Medibuntu]("http://www.medibuntu.org/repository.php") repository, then;

```
sudo apt-get install skype
```

No need to use WinDVD, do [this]("http://ubuntuforums.org/showthread.php?t=413624").

I think I may have installed mediubuntu, not 100% sure though.

Oh I meant windvd creator, I love that burning software.

---

### Post by por100pre1 on 2007-09-08
> **T4K3Z0U said:**
> Oh I meant windvd creator, I love that burning software.

For editing try Kino or [Cinelerra]("http://www.kiberpipa.org/~gandalf/ubuntu/README"):

```
sudo apt-get install kino
```

For burning k3b, brasero, or gnomebaker will do the job:

```
sudo apt-get install k3b brasero gnomebaker
```

(I'm assuming you have the Medibuntu repository already added.)

---

### Post by T4K3Z0U on 2007-09-08
> **por100pre1 said:**
> Add [Medibuntu]("http://www.medibuntu.org/repository.php") repository, then;

```
sudo apt-get install skype
```

No need to use WinDVD, do [this]("http://ubuntuforums.org/showthread.php?t=413624").

I got this message.

[IMG]http://i33.photobucket.com/albums/d51/kiwi_samurai/Screenshot-t4k3z0uTAKEZOU-1-1.png[/IMG]

Nothing happens when I attempt to run that code manually. Or am I meant to enter that code into terminal?

Nope need superuser privileges to run that in terminal.

---

### Post by por100pre1 on 2007-09-08
Try it this way:

```
sudo dpkg --configure -a
```

---

### Post by T4K3Z0U on 2007-09-08
> **por100pre1 said:**
> Try it this way:

```
sudo dpkg --configure -a
```

aha, I didn't type sudo. This is somewhat frustrating. However I feel happy like I'm a computer nerd who knows what he's doing when typing in terminal. :)

---

### Post by Arwen on 2007-09-08
Nothing happens when you type the command "dpkg --configure  -a" in terminal?You see bash or nothing or errors?

---

### Post by T4K3Z0U on 2007-09-08
Fixed but couldn't find package skype. :(

---

### Post by Jense on 2007-09-08
try installing skype via automatix2. 
for automatix2 instructions check here

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

if you are new to ubuntu automatix is great cause it does a whole lot of things for you that would require much commandline action. helped me a lot

---

### Post by por100pre1 on 2007-09-08
> **T4K3Z0U said:**
> aha, I didn't type sudo. This is somewhat frustrating. However I feel happy like I'm a computer nerd who knows what he's doing when typing in terminal. :)

Good to know you are having fun so far. Learning CLI is really rewarding. :)

---

### Post by por100pre1 on 2007-09-08
> **T4K3Z0U said:**
> Fixed but couldn't find package skype. :(

Ignore that advice about Automatix:

If you added Medibuntu repo do this:

```
sudo apt-get update
```

and try again.

---

### Post by Vadi on 2007-09-08
I'll second the 'ignore Automatix'...

---

### Post by T4K3Z0U on 2007-09-08
> **por100pre1 said:**
> . Learning CLI is really rewarding. :)

CLI :confused:

> **por100pre1 said:**
> Ignore that advice about Automatix:

If you added Medibuntu repo do this:

```
sudo apt-get update
```

and try again.

Medibuntu doesn't install or load properly.

I love this screenshot feature, apparently it can be done on windows but I never worked it out.
[IMG]http://i33.photobucket.com/albums/d51/kiwi_samurai/Screenshot-t4k3z0uTAKEZOU-2-1.png[/IMG]

---

### Post by Arwen on 2007-09-08
Or you can download skype from here->[http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/)

---

### Post by schorsch on 2007-09-08
... it is called "medibuntu" not "mediubuntu" so the entry in "/etc/apt/sources.list" has to look like "packages.medibuntu.org". Please edit the file via
```
gksu gedit /etc/apt/sources.list
```

---

### Post by por100pre1 on 2007-09-08
Schorsch is right! Do so then do this:


```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

```
sudo apt-get update
```

---

### Post by T4K3Z0U on 2007-09-08
> **schorsch said:**
> ... it is called "medibuntu" not "mediubuntu" so the entry in "/etc/apt/sources.list" has to look like "packages.medibuntu.org". Please edit the file via
```
gksu gedit /etc/apt/sources.list
```

Oh that was just a typo by me. I'm 1/2 asleep, its 0100 here.
It says "packages.medibuntu.org/ feist free non-free"

---

### Post by por100pre1 on 2007-09-08
> **T4K3Z0U said:**
> Oh that was just a typo by me. I'm 1/2 asleep, its 0100 here.

You can go to sleep and come back in the morning if you need to. :)

---

### Post by T4K3Z0U on 2007-09-08
> **por100pre1 said:**
> Schorsch is right! Do so then do this:


```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

[COLOR="DarkSlateBlue"]That said "OK"[/COLOR]

```
sudo apt-get update
```

[COLOR="DarkSlateBlue"]this gave me same message as displayed in the screen shot.[/COLOR]

---

### Post by por100pre1 on 2007-09-08
Let's see what you got:

```
cat /etc/apt/sources.list
```

and post the results... :-k

---

### Post by T4K3Z0U on 2007-09-08
> **por100pre1 said:**
> You can go to sleep and come back in the morning if you need to. :)

Nah I can't sleep, too excited. Plus Di Vinci never slept, he said it was a waste of time. ;)

I hate this working in silence thing to. I wish there was a program to override DRM or a program to change wma into supported format.

---

### Post by por100pre1 on 2007-09-08
> **T4K3Z0U said:**
> Nah I can't sleep, too excited. Plus Di Vinci never slept, he said it was a waste of time. ;)

I hate this working in silence thing to. I wish there was a program to override DRM or a program to change wma into supported format.

Look at Schorsch's post and be sure to replace mediubuntu with medibuntu.

---

### Post by T4K3Z0U on 2007-09-08
> **por100pre1 said:**
> Let's see what you got:

```
cat /etc/apt/sources.list
```

and post the results... :-k

[IMG]http://i33.photobucket.com/albums/d51/kiwi_samurai/Screenshot-t4k3z0uTAKEZOU-2-2.png[/IMG]
[IMG]http://i33.photobucket.com/albums/d51/kiwi_samurai/Screenshot-t4k3z0uTAKEZOU-3-1.png[/IMG]

This is what I got.

---

### Post by T4K3Z0U on 2007-09-08
> **por100pre1 said:**
> Look at Schorsch's post and be sure to replace mediubuntu with medibuntu.

My bad. I thought it was something I wrote in a post not in the script.

---

### Post by por100pre1 on 2007-09-08
Please copy and paste the whole results of:

```
cat /etc/apt/sources.list
```

don't use images, I don't see whole text that way.

---

### Post by por100pre1 on 2007-09-08
> **T4K3Z0U said:**
> My bad. I thought it was something I wrote in a post not in the script.

Ok, it seems you got it, good. :)

---

### Post by schorsch on 2007-09-08
I guess the important part of the sources.list is still missing. If you are posting large outputs you should not post a screenshot of the terminal window with half of the information but use the "CODE" flags. In the editor, second line of icons, the third from the right .... there is a "#" sign. After pressing this you get "[ CODE ]  [ /CODE ]". Put the output in the middle of them.
But there is still a typo in your sources list:
```
gksu gedit /etc/apt/sources.list
```
and change "mediubuntu" to "medibuntu"

---

### Post by T4K3Z0U on 2007-09-08
> **por100pre1 said:**
> Please copy and paste the whole results of:

```
cat /etc/apt/sources.list
```

don't use images, I don't see whole text that way.

The images are the full text, I made sure nothing was cut out nor repeated. 

> **schorsch said:**
> I guess the important part of the sources.list is still missing. If you are posting large outputs you should not post a screenshot of the terminal window with half of the information but use the "CODE" flags. In the editor, second line of icons, the third from the right .... there is a "#" sign. After pressing this you get "[ CODE ]  [ /CODE ]". Put the output in the middle of them.
But there is still a typo in your sources list:
```
gksu gedit /etc/apt/sources.list
```
and change "mediubuntu" to "medibuntu"

It won't let me copy the text and you must be kidding if you think I'm gunna re-type all that. ;)  But as mentioned above they are good screen shots.

Mediubuntu since changed thanks.

ETA: I just noticed I posted the pics the wrong way round. Bottom one should be on top and vice versa.

---

### Post by schorsch on 2007-09-08
> **T4K3Z0U said:**
> It won't let me copy the text and you must be kidding if you think I'm gunna re-type all that. ;)  But as mentioned above they are good screen shots.

Noone wants you to type the whole text. Under X just highlight the text you want to copy with the mouse and the pressed left button. To insert text navigate your mouse to the right place and press the middle button/scrollwheel or both buttons if you have just a two button mouse.

---

### Post by tcoffeep on 2007-09-08
Frostwire is good, and better than Limewire.

[http://www.frostwire.com](http://www.frostwire.com)

Deluge is a good torrent downloader.

[http://www.deluge-torrent.org](http://www.deluge-torrent.org)

---

### Post by Vadi on 2007-09-08
Select the text, right click, Copy, is also another option.

---

### Post by T4K3Z0U on 2007-09-09
So to make sure I have a basic understanding of ubuntu now. If I D/L something and want to install it I gotta go to terminal and type. "sudo apt-get install <program>" and everything should go fine?

---

### Post by Vadi on 2007-09-09
Sorta.

Take a look at this page ([http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)), see if you can find your mistake - if no, I'll explain it to you :)

---

