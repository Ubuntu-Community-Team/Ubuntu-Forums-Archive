---
title: "I cant execute EPSXE emulator :S"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by lordpuppet on 2007-11-15
Hi, I dont know why i cant execute epsxe,

I downloaded and extracted, comes in a .zip file and doesnt need any installation, works just double clicking the "epsxe" file, but when i do it, nothing happens.

From a terminal, i enter the folder where the file is and type " ./epsxe " but nothing happens, not even an error. 

In properties says wine emulator as the aplication that opens the file.

What can i do?

---

### Post by NightCrawler03X on 2007-11-15
Since you tried running it from a terminal and it didn't run nor give errors, I know for a fact that you are running Ubuntu 7.10 Gutsy.

The epsxe executable is upx compressed. You need to decompress it:
```

sudo apt-get install upx-ucl
cd <location to directory that has your epsxe executable in it>
upx -d epsxe

```
By doing this, we are getting the "real" binary, rather than the compressed one.
After that, you can run epsxe without problems, it will load.

```

./epsxe

```

---

### Post by lordpuppet on 2007-11-15
It Worked!!!!

Thankyou!!

I didnt knew that. :)

Thank you again!

---

### Post by lordpuppet on 2007-11-15
I have another problem. This time is a problem in configuration.

It says I dont have the bios file, but i do... and i set correctly the path, look in the pic:

[[IMG]http://img522.imageshack.us/img522/4857/ddgf5.th.jpg[/IMG]](http://img522.imageshack.us/my.php?image=ddgf5.jpg)

The path i put is 
```
/usr/local/games/epsxe/bios/SCPH1001.BIN
```

---

### Post by NightCrawler03X on 2007-11-15
Your bios image' file permission and ownership policies are wrong:
```

sudo chmod 755 scph1001.bin
sudo chown your_user_name scph1001.bin

```
Tell me what that does in regards to your problem.

---

### Post by lordpuppet on 2007-11-15
Thanks, it was the permission wrong.

Thank you, god!

---

### Post by redleafong on 2007-11-16
I came accross this thread and it is just what i need!

Thanks NightCrawler03X!

---

### Post by NightCrawler03X on 2007-11-16
Hmm, thanks for the complements :D

It's nice to hear that I'm appreciated.

---

### Post by disturbedite on 2007-11-16
i'd like to recommend pSX.  ubuntu packages are available here:  
[http://packages.dfreer.org](http://packages.dfreer.org)

its the best playstation emulator imo and other ppl's opinion too.  its the newest (although that doesn't make it the best) ps emulator.  one of the things that makes it the best imo is that it requires no plugins!

homepage is here if you want more info:
[http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/)

---

### Post by NightCrawler03X on 2007-11-16
Yes, pSXfin is definitely superior. Though I help people with ePSXe, I actually use pSXfin.

It's much more accurate, and faster too (on the graphical side of things, because graphics are rendered by the CPU, rather than the graphics card; all the graphics card does is draw the images to screen.).

It also has better compatability, and the developers are still actively working on it, so eventually, it may be the best PSX emulator there is!

The only thing it misses is the graphical enhancements, but the projects main aim is to emulate the console as accurately as possible (heck, it even emulates the colour dithering scheme used on real PSX units), so I won't complain here.

Just one thing if you peeps plan on using it:

```

sudo apt-get install libgtkglext1

```

It won't run without this library installed.

---

