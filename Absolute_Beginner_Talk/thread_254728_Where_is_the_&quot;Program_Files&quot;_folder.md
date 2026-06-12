---
title: "Where is the &quot;Program Files&quot; folder?"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by locoHost on 2006-09-10
I can't seem to find where some programs are installed. They seem to go all over the place in various nested folders. Isn't there the Linux folder equivalent of "Program Files"?

Thanks for your help guys :-)

---

### Post by jordanmthomas on 2006-09-10
*/usr/share* has folders like Program Files would
You can find (most) of the programs in */usr/bin*

---

### Post by bodhi.zazen on 2006-09-10
No, programs are in various locations as you have found. They are organized more along the lines of administration or system programs and user programs.

---

### Post by Omnios on 2006-09-10
This is some heavy reading for Linux filesystems.
[http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html)

---

### Post by BlacKat_K on 2006-09-10
Hmm so how should i find a program that lets say doesnt show up in "aplications" or in "system"?Just search it up by its name?Thats not a very good solution to me to be honest...

---

### Post by locoHost on 2006-09-10
If I download and install a program, how would I pick a folder in which to install it? I'm trying to stay organized :-)

---

### Post by Omnios on 2006-09-10
> **locoHost said:**
> If I download and install a program, how would I pick a folder in which to install it? I'm trying to stay organized :-)

 Hi synaptic programs and .debs install with sudo dpkg and it automaticly installs files to the proper files, This also occurs with alien etc. Also when you install a tarball it also installs the files to the proper directory. Althogh there seems to be some games that are just untared or install in the home directory.

---

### Post by bodhi.zazen on 2006-09-10
> **BlacKat_K said:**
> Hmm so how should i find a program that lets say doesnt show up in "aplications" or in "system"?Just search it up by its name?Thats not a very good solution to me to be honest...

LOL ! :lol:

```
which <program name>
```
Also see my next post.

---

### Post by Requiem on 2006-09-10
Goes like this
basic/core/old programs go in /bin
critical security programs go in /sbin
everything else goes in /usr/bin
but you will find only executable files here, images, icons and other program parts go into
/usr/share
This is probably what you want, looking into program resources, /usr/bin is much less interesting

---

### Post by BlacKat_K on 2006-09-10
Talking about games,i installed Battle for Wesnoth twice and it wouldnt make a sortcut in Games so i couldnt find it to play it.Which is kinda why i'm following this thread :D

---

### Post by bodhi.zazen on 2006-09-10
> **locoHost said:**
> If I download and install a program, how would I pick a folder in which to install it? I'm trying to stay organized :-)

You do not get to pick (actually that is only partially true).

Use Syanaptic to "stay organized".

If you install from source, you will need to worry.

In that case, make a directory in /home/user_name "src"
```
mkdir ~/src
```
Download and unpack all source code here. Each program will have a directory (after unpacking) program-x.y.z. cd into that directory;

./configure; make; sudo checkinstall (Please use checkinstall rather then make install if at all possible).

YOU WILL NEED TO SAVE THESE DIRECTORIES. Thus the directory ~/src.

(~ is short hand for your home folder, works at the cli as well).

---

### Post by bodhi.zazen on 2006-09-10
> **BlacKat_K said:**
> Talking about games,i installed Battle for Wesnoth twice and it wouldnt make a sortcut in Games so i couldnt find it to play it.Which is kinda why i'm following this thread :D

Games are different.

---

### Post by Tomosaur on 2006-09-10
Linux splits up application files into different directories. From a Windows point of view, this can be confusing, but you'll get used to it. It makes finding what you're after a lot easier. Once you download and install a program, you will GENERALLY be able to use it by just typing something in the terminal, but what you type will depend on several things:
1) Where the file installed to
2) What it's called
3) Whether it's in your PATH,

'Installation' is not the same as 'decompression', which will generally just put all of the files into one folder, similar to windows. Installation will break up different files and put them into different directories. Documentation goes into /usr/share/doc/<program>/ for example, while binaries / executables will go into /usr/bin or just /bin/.

It will take some getting used to, but it does make sense and it is better (in my opinion) in the long run.

---

### Post by Lakefall on 2006-09-10
> **BlacKat_K said:**
> Talking about games,i installed Battle for Wesnoth twice and it wouldnt make a sortcut in Games so i couldnt find it to play it.
How did you install it? If you used synaptic (recommended), it should appear in Games. Otherwise try typing "which wesnoth" to the command line. It should tell you where the binary or script to run the thing is. (Just typing "wesnoth" should start the game.) If it doesn't say anything, you have put it in some weird place. :p

---

### Post by locoHost on 2006-09-11
> **Requiem said:**
> Goes like this
basic/core/old programs go in /bin
critical security programs go in /sbin
everything else goes in /usr/bin
but you will find only executable files here, images, icons and other program parts go into
/usr/share
This is probably what you want, looking into program resources, /usr/bin is much less interesting

Yes that -is- what I was looking for. Thanks! :)

---

### Post by Metacarpal on 2006-09-11
> **BlacKat_K said:**
> Talking about games,i installed Battle for Wesnoth twice and it wouldnt make a sortcut in Games so i couldnt find it to play it.Which is kinda why i'm following this thread :D

Hmm.  I installed Wesnoth not long ago and got a shortcut.  Maybe yours just isn't showing?  Go into the Alacarte menu editor and look at the games menu selections.  If you see Wesnoth there, but the box isn't checked, then check the box.  Hopefully that'll fix it...

---

### Post by Brunellus on 2006-09-11
> **Metacarpal said:**
> Hmm.  I installed Wesnoth not long ago and got a shortcut.  Maybe yours just isn't showing?  Go into the Alacarte menu editor and look at the games menu selections.  If you see Wesnoth there, but the box isn't checked, then check the box.  Hopefully that'll fix it...
quibble:  Don't use "shortcut."  It's a bad word, and often causes confusion, since Microsoft has used it interchangably to refer to:

* program launchers
* URLs and/or Bookmarked URLs
* hyperlinks 
* quasi-softlinks

IN this case, we're talking about a "launcher."  

As far as I'm aware, the version of Wesnoth presently in the repositories should also install the relevant launcher.

---

### Post by anaconda on 2006-09-11
> **Lakefall said:**
> How did you install it? If you used synaptic (recommended), it should appear in Games. Otherwise try typing "which wesnoth" to the command line. It should tell you where the binary or script to run the thing is. (Just typing "wesnoth" should start the game.) If it doesn't say anything, you have put it in some weird place. :p

Yes. just type the name of the program in terminal and it should start. (usually the same name that was in synaptic or apr-get)
And once you know how to start the game you can add it to yoy games menu by using "/accessories/Alacarte Menu Editor" Just select Games, and then click File from top left corner and select "New entry" and type the command which worked in terminal to the "Command:" line. Then you can give it any name you want..and select whichever icon you want..

Supricingly many games dont add themselwes to the menu..

---

