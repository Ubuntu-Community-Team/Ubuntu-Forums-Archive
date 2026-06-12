---
title: "[SOLVED] How to install a program"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by The Hunt For Ida Wave on 2008-02-23
Hi, I've just downloaded Visualboy Advance 1.7.2 for linux.
Can anyone tell me how to install it?
The emulator can be downloaded from [here.]("http://linux.softpedia.com/progDownload/Visualboy-Advance-Download-3469.html")
Thanks in advance.

---

### Post by taurus on 2008-02-23
Visualboy Advance is in the repos unless you want to build it from source.

```
sudo apt-get update
sudo apt-get install visualboyadvance visualboyadvance-gtk
```

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by The Hunt For Ida Wave on 2008-02-23
I'm already using VBA Express, but wanted to switch to an emulator that supports cheat functions. Visualboy Advance 1.7.2 supports this which is why I'm trying to use that one.

---

### Post by taurus on 2008-02-23
I assume you have downloaded it and saved it to ~/Desktop.  Open a terminal and run

```
cd ~/Desktop
tar xvzf VisualBoyAdvance-src-1.7.2.tar.gz 
cd VisualBoyAdvance-1.7.2
sudo apt-get update
sudo apt-get install build-essential checkinstall
./configure 
make
sudo checkinstall
```

---

### Post by The Hunt For Ida Wave on 2008-02-23
Thanks for the reply again. When I use the ./configure command I get this error:


configure: error: *** Cannot compile without zlib.

---

### Post by taurus on 2008-02-23
Here is what I think you should do.  Install the latest version from the repos.

```

sudo apt-get update
sudo apt-get install visualboyadvance visualboyadvance-gtk

```
That would probably install all the necessary dependencies for it.  Then, see if you can build it from source this time.  You can remove those two files from synaptic later if you wish.

Otherwise, try

```
sudo apt-get update
sudo apt-get build-dep visualboyadvance
```

---

### Post by Martje_001 on 2008-02-23
> **The Hunt For Ida Wave said:**
> configure: error: *** Cannot compile without zlib.
```
sudo apt-get install zlib1g-dev
```

---

### Post by The Hunt For Ida Wave on 2008-02-23
Done everything now. How do I run the app?

---

### Post by Martje_001 on 2008-02-24
ALT+F2 --> /usr/bin/gvba

May I ask why you didn't install the program with synaptic?

---

### Post by uberlube on 2008-02-24
Nice avatar Martje_001, I love the wallpaper you took it from :)

Sorry to change subject.

---

### Post by Martje_001 on 2008-02-24
Hehe :)

---

### Post by uberlube on 2008-02-24
Too bad you couldn't fit in the black sheep as well.

---

### Post by The Hunt For Ida Wave on 2008-02-24
> **Martje_001 said:**
> ALT+F2 --> /usr/bin/gvba

May I ask why you didn't install the program with synaptic? 

Thanks, but that didn't work.
And I don't know how to. :confused:

---

### Post by The Hunt For Ida Wave on 2008-02-24
The deb file isn't installing. Being unfamiliar with creating debs, I accidently changed some of the settings in the terminal while it was compiling, so I thought it best to re-create it, which I did and tried to overwrite the previous install. It says it can't because there's already a version there, used synaptic to try and find it, but I've removed everything I can see with "visualboy" in it. Still no success.

---

### Post by The Hunt For Ida Wave on 2008-02-24
[IMG]http://img297.imageshack.us/img297/1116/screenshotgdebigtkvj1.png[/IMG]

:confused:

---

### Post by Martje_001 on 2008-02-24
> **The Hunt For Ida Wave said:**
> Thanks, but that didn't work.
And I don't know how to. :confused:
Start Synaptic, and press search. Enter the name of the program, and double click the search results. Then press apply, and voila!

---

### Post by The Hunt For Ida Wave on 2008-02-24
Thanks. Any idea what I should search for to completely remove any VBA emulator files I have? This will allow me to install it again via the deb file, and hopefully, will mean I can run it.

---

### Post by Martje_001 on 2008-02-24
Search for VBA in 'name and description'.

---

### Post by Martje_001 on 2008-02-24
Btw: Maby you can install the .deb package with the force argument on the command line.

---

### Post by Steveway on 2008-02-24
Based on that Screenshot, I would search for a package with the name: 2

---

### Post by The Hunt For Ida Wave on 2008-02-24
> **Steveway said:**
> Based on that Screenshot, I would search for a package with the name: 2

Thanks, this worked. I can't believe I didn't think of that. :confused: I was thinking along the lines of Martje_001, that it would still be called VBA, even though I accidently renamed it as as I compiled it.
Now I've installed the deb again, so how do I run it?

---

### Post by Martje_001 on 2008-02-24
First you have to install a front-end for it ;)

Try installing visualboyadvance-gtk or vbaexpress.

---

### Post by The Hunt For Ida Wave on 2008-02-24
Thanks for the quick response. :KS
I've installed visualboy-gtk. Now what?

---

### Post by teh'p3nsi0n3r on 2008-02-24
ive done everything and have the visualboyadvance latest version installed and the visualboyadvance-gtk frontend installed, how do i go about running it now?

---

### Post by Martje_001 on 2008-02-24
ALT+F2 --> /usr/bin/gvba

I misread in the previous post ;)

---

### Post by teh'p3nsi0n3r on 2008-02-24
thanks got that and vbaexpress working now too :)

---

### Post by The Hunt For Ida Wave on 2008-02-24
That's it. Though it doesn't have cheat functions as suggested [_here_]("http://linux.softpedia.com/get/System/Emulators/Visualboy-Advance-3469.shtml") but I suppose for our purposes, the thread is solved anyway. Thanks for all help given.

---

