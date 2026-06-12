---
title: "Untaring, How to extract an exe, and several other questions"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by nzk on 2006-08-20
Just installed ubuntu (partitioner corruped my windows partition >.<)

I feel like i was dropped off in a city (ubuntu) that speaks a foreign language but there are alot of nice people who help (on irc and here)

Questions:

1.How do I untar? I tried tar xvzf (or something) filename.tar.gz but its always like "cant find file"
2.Why doesnt sudo apt-get ever work? I tried sudo apt-get blender but that didnt work so well
3.How do I extract an exe for the ndiswrapper?
4.For ndiswrapper, should I use my internal wifi card or my pc card wifi card?(well it goes into the side of my laptop) the 2nd one is mucho expensive and very nice, picks up signals down my street :) except power isnt even going to it now, the little lights arent blinking...:(
5.xgl, will that work well on a p4 with ati mobility radeon 9800?
6.Do I need both xgl and compiz or just xgl for the eye candy?
7.Is wine fast? I want to use itunes in it, will that work well? If not then what are some good alternatives?
8.Where can I find good themes for gui? (or will I not need it with xgl?)
9.If after everything I get xgl installed, what is that thing I need for tranparency effects?

Thanks so much in advance, I'm a windows and computer master, just linux isnt my strong point :p

---

### Post by meng on 2006-08-20
1. You have to be in the same directory as the file you are untar-ing. What directory are you in when you type the command, and what directory is the file in?
2. sudo apt-get install blender
3-9. (pass)

---

### Post by nzk on 2006-08-20
Its on the desktop, since firefox puts all the downloads on the desktop

---

### Post by meng on 2006-08-20
And are you untaring from /home/(your username)/Desktop?
You should try
cd Desktop
before untaring

---

### Post by GuitarHero on 2006-08-20
> **nzk said:**
> Just installed ubuntu (partitioner corruped my windows partition >.<)

I feel like i was dropped off in a city (ubuntu) that speaks a foreign language but there are alot of nice people who help (on irc and here)

Questions:

1.How do I untar? I tried tar xvzf (or something) filename.tar.gz but its always like "cant find file"
2.Why doesnt sudo apt-get ever work? I tried sudo apt-get blender but that didnt work so well
3.How do I extract an exe for the ndiswrapper?
4.For ndiswrapper, should I use my internal wifi card or my pc card wifi card?(well it goes into the side of my laptop) the 2nd one is mucho expensive and very nice, picks up signals down my street :) except power isnt even going to it now, the little lights arent blinking...:(
5.xgl, will that work well on a p4 with ati mobility radeon 9800?
6.Do I need both xgl and compiz or just xgl for the eye candy?
7.Is wine fast? I want to use itunes in it, will that work well? If not then what are some good alternatives?
8.Where can I find good themes for gui? (or will I not need it with xgl?)
9.If after everything I get xgl installed, what is that thing I need for tranparency effects?

Thanks so much in advance, I'm a windows and computer master, just linux isnt my strong point :p

3. You don't extract exe's, exe's are program files for windows.  you only want the driver files off of the install cd
4. Use which ever is better, or whichever you have drivers for.
5. Depends how much ram you have,
6. Both
7. Wine doesnt work with itunes i dont think, but fear not there are great alternatives!  Try Amarok, Listen, Gtkpod, Banshee, whichever you like best.
8. gnome-look.org
9. There will be a configuration menu for compiz that lets you edit the effects.

---

### Post by nzk on 2006-08-20
> **GuitarHero said:**
> 3. You don't extract exe's, exe's are program files for windows.  you only want the driver files off of the install cd
4. Use which ever is better, or whichever you have drivers for.
5. Depends how much ram you have,
6. Both
7. Wine doesnt work with itunes i dont think, but fear not there are great alternatives!  Try Amarok, Listen, Gtkpod, Banshee, whichever you like best.
8. gnome-look.org
9. There will be a configuration menu for compiz that lets you edit the effects.

I mean getting an .inf or whatever ndiswrapper uses because all the tuts I read said I can do that, I just dont know how. And I'm about 4,362 miles from my install cd :(

I looked up amarok, and I only found it for mandriva and suse linux, will it work on ubuntu?

---

### Post by GuitarHero on 2006-08-20
Yes its in the repositories.  Just go to Applications> Add/Remove Program.  Search for AmaroK and install it from there, much easier than doing it from source.  Sorry I do not know how to get the .inf from the .exe install file.  Maybe you could install it on a windows box and get the .inf from wherever it installs to?

---

### Post by nalmeth on 2006-08-20
*1.How do I untar? I tried tar xvzf (or something) filename.tar.gz but its always like "cant find file"*
** Right-click the file in the file manager, and you'll see the options you need. **
* 2.Why doesnt sudo apt-get ever work? I tried sudo apt-get blender but that didnt work so well*
** Any output for us? What exactly is going wrong? I would guess your internet connection is the showstopper.**
[I] 3.How do I extract an exe for the ndiswrapper?
[/I]** You need an .inf file, you can probably find one on the card's manufacturer's site. ndis-gtk is a GUI for ndiswrapper, which may make things easier.**
* 4.For ndiswrapper, should I use my internal wifi card or my pc card wifi card?(well it goes into the side of my laptop) the 2nd one is mucho expensive and very nice, picks up signals down my street :smile: except power isnt even going to it now, the little lights arent blinking...:sad:*
** Hmm, this one's up to you, as I don't know what kinds of cards you have. Use what works first, and then get more ambitious, is my advice...**
* 5.xgl, will that work well on a p4 with ati mobility radeon 9800?*
** If your card is supported by the fglrx driver, then probably yes.**
* 6.Do I need both xgl and compiz or just xgl for the eye candy?*
**XGL is what facilitates compiz, I believe. You'll need both AFAIK.**
* 7.Is wine fast? I want to use itunes in it, will that work well? If not then what are some good alternatives?*
** It doesn't work with ipod syncing, if that is your concern. It will work I believe, but you might as well use something native to linux. Amarok is my all-time favorite music player, but for gnome you may want listen, or banshee or something. There are ALOT of alternatives. GTKpod is good for ipod syncing**
* 8.Where can I find good themes for gui? (or will I not need it with xgl?)*
[B][http://gnome-look.org/](http://gnome-look.org/)
I can't remember where to get themes for the compiz window manager. :-k[/B]
* 9.If after everything I get xgl installed, what is that thing I need for tranparency effects?*
** hold alt, and drag the mouse wheel over a window. Or configure all the plugins with the gsetcompiz tool.**

---

### Post by majesticturkey on 2006-08-20
> **nzk said:**
> 
1.How do I untar? I tried tar xvzf (or something) filename.tar.gz but its always like "cant find file"

the command is tar -xvzf. You need the dash.

> 2.Why doesnt sudo apt-get ever work? I tried sudo apt-get blender but that didnt work so well

sudo apt-get install blender. Apt-get has several functions, so you tell it to install blender, as opposed to remove blender.

> 3.How do I extract an exe for the ndiswrapper?

Bit confused here. Linux doesn't have .exe files. If you installed ndiswrapper, the command to use would be...ndiswrapper. Although for Windows converts I recommend getting ndisgtk, which is a GUI. 

> 4.For ndiswrapper, should I use my internal wifi card or my pc card wifi card?(well it goes into the side of my laptop) the 2nd one is mucho expensive and very nice, picks up signals down my street :) except power isnt even going to it now, the little lights arent blinking...:(

Your choice. I'd go with the card, which sounds very nice. All you need is the driver file, which is on a CD that came with the hardware or located in a folder on your Windows partition. You probably could also find it for download somewhere.

> 5.xgl, will that work well on a p4 with ati mobility radeon 9800?

Should.

> 6.Do I need both xgl and compiz or just xgl for the eye candy?

You'll need both. XGL is to Compiz as Xserver is to Metacity. Sorta. Hard to explain simply for me, but XGL does all the nifty stuff, and Compiz displays it for you.

> 7.Is wine fast? I want to use itunes in it, will that work well? If not then what are some good alternatives?

It depends on a lot of stuff, some people have problems. I don't. Wine works almost as fast as natively for me. Don't use iTunes, anyway. I loved it under Windows, but I use Amarok under Gnome (yeah, I know, Amarok is a KDE program). It's far better than iTunes.

> 8.Where can I find good themes for gui? (or will I not need it with xgl?)

[www.gnome-look.org](www.gnome-look.org), [www.kde-look.org](www.kde-look.org). Compiz's decorator, CGWD, comes with a bunch of good themes though.

> 9.If after everything I get xgl installed, what is that thing I need for tranparency effects?

Right click a titlebar, and you can set window transparency. Lots of themes have transparent borders. You can set your terminal window's background to be transparent. Things that normally were "pseudo-transparent" tend to be fully transparent.

> Thanks so much in advance, I'm a windows and computer master, just linux isnt my strong point :p

As you'll probably find out many times in learning Linux/Ubuntu, all that stuff you know about Windows just doesn't carry over. Have a good time, though, and enjoy being able to mess around with the tinker-toys operating system.

---

### Post by mssever on 2006-08-20
> **majesticturkey said:**
> the command is tar -xvzf. You need the dash.
Actually, tar works with or without the hyphen. Sometimes I use tar -xzvf file and sometimes tar xzvf file. Both are equivalent.

---

### Post by mssever on 2006-08-20
> **nzk said:**
> 1.How do I untar? I tried tar xvzf (or something) filename.tar.gz but its always like "cant find file"
In addition to the comments above, tab completion is your friend. Type part of the filename and hit tab. If you've typed enough for it to be unique, bash will automatically fill in the rest of the name, thus eliminating typos.

---

### Post by tuxcantfly on 2006-08-20
about extracting .exe files...

use wine (i'll assume this is a self-extractor)

wine archive.exe

extract it to c:\

it'll be in ~/.wine/drive_c

---

### Post by tuxcantfly on 2006-08-20
as for the untarring, just do yourself a favor and use file-roller (gnome) or ark (kde)

---

### Post by kerry_s on 2006-08-20
#1. just click on it and file-roller will open to extract it.

#2. did you do "sudo apt-get update" first to get a package list

#3. see #1

#4. use which ever one you can get to work

#5. ? ( i don't use that fancy stuff :)  )

#6. see #5

#7. no, not really,depnds on youir hardware

#8. [http://www.gnome-look.org/](http://www.gnome-look.org/)

#9. see #5

---

### Post by encompass on 2006-08-20
Has this person written back?  These are great responses.  I would also comment the he should read a few things about linux... like
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)  Just my 2 cents

---

### Post by nzk on 2006-08-21
> **tuxcantfly said:**
> about extracting .exe files...

use wine (i'll assume this is a self-extractor)

wine archive.exe

extract it to c:\

it'll be in ~/.wine/drive_c

I see no folder named "~"

---

### Post by Gustav on 2006-08-21
> **nzk said:**
> I see no folder named "~"

~ is your home folder (/home/username/) when you start the terminal this is where you are. To get there if you're lost you can just type 'cd'.

---

### Post by encompass on 2006-08-21
there is a cool thing with linux...
try
```
cd ~
```
and it will no matter who you are go to your home directory.
so he told you to goto ~/.wine/blalbla
try it out.

---

