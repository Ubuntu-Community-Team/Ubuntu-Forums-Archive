---
title: "How do i install this?"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by BusDriverBloke on 2007-11-23
I've been trying to install the application below for a couple of days but i just can't work out how to do it. It's an uploading application to program DreamBox cable and satellite receivers via RS232 and LAN. Please help as i used the windows version all the time and i miss it loads.
[URL="http://ghost.dream-multimedia-tv.de/DreamUP/DreamUP_Linux_1_3_beta"]
http://ghost.dream-multimedia-tv.de/DreamUP/DreamUP_Linux_1_3_beta[/URL]

---

### Post by Paul820 on 2007-11-23
If it's on your desktop, from the terminal:
> cd ~/Desktop
sudo chmod +x DreamUP_Linux_1_3_beta

---

### Post by Jense on 2007-11-23
have you tried this?

[http://www.dream-multimedia-tv.de/board/thread.php?threadid=2813](http://www.dream-multimedia-tv.de/board/thread.php?threadid=2813)

---

### Post by spiderbatdad on 2007-11-23
that's a bin file. I've installed a few but it's been awhile. something like cd into the directory where the file is and type ./filename

there might be more to it than that. you should be able to extract the archives by right clicking on the file and look for an install or readme file with instruction on how to install it...sometimes there are things like ./autogen.sh or something like that.
sorry for poor help, but maybe someone with more expertise will notice your post

---

### Post by BusDriverBloke on 2007-11-23
cd ~/Desktop
sudo chmod +x DreamUP_Linux_1_3_beta 

I've just tried the commands above and nothing happened all the instructions on the Dream Multimedia website are in German so i can't understand them.

Simon

---

### Post by spiderbatdad on 2007-11-23
> **Paul820 said:**
> If it's on your desktop, from the terminal:

sudo chmod a+x .........
to make it executable. then ./filename

---

### Post by Paul820 on 2007-11-23
> **spiderbatdad said:**
> sudo chmod a+x .........
to make it executable. then ./filename

Sorry, i forgot to put the instruction to run the file :lolflag:
> ./DreamUP_Linux_1_3_beta

---

### Post by spiderbatdad on 2007-11-23
you wrote chmod +x also. does that work without the a?

---

### Post by Paul820 on 2007-11-23
> **spiderbatdad said:**
> you wrote chmod +x also. does that work without the a?

Yes.

---

### Post by BusDriverBloke on 2007-11-23
I feel like i'm starting to get somewhere but i get the following messages. Just been on package manager and libglib-1.2 in installed



simon@simon-laptop:~/Desktop$ sudo chmod a+x DreamUP_Linux_1_3_beta
simon@simon-laptop:~/Desktop$ ./DreamUP_Linux_1_3_beta
./DreamUP_Linux_1_3_beta: error while loading shared libraries: libglib-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by spiderbatdad on 2007-11-23
did you find the instructions particular to this package yet?

---

### Post by BusDriverBloke on 2007-11-23
No there only in German.

---

### Post by spiderbatdad on 2007-11-23
google the package and translate the page. find out where it came from or something...try right clicking the package itself and extracting it to find a readme or install file. you really should have instructions particular to any package you install

---

### Post by BusDriverBloke on 2007-11-23
I tried to translate in Babelfish but it makes no sense at all. i might have to give up on this one.

---

### Post by spiderbatdad on 2007-11-23
can you post a link to the page?

---

### Post by BusDriverBloke on 2007-11-23
This is it

[http://dmmtv.de/board/thread.php?threadid=2813]("http://dmmtv.de/board/thread.php?threadid=2813")

---

### Post by spiderbatdad on 2007-11-23
try this:
[http://www.dream-multimedia-tv.de/board/thread.php?threadid=2814&sid=f3af6abc11866bfeb1deb84403c77f07](http://www.dream-multimedia-tv.de/board/thread.php?threadid=2814&sid=f3af6abc11866bfeb1deb84403c77f07)

also says you need a deb packge.
For Debian an "apt-get install libgdk-pixbuf" should install all needed packages.

I would sudo apt-get install libgdk-pixbuf

then try ./thenameofthefileagain.bin

---

### Post by spiderbatdad on 2007-11-23
like so
;

---

### Post by gupta_sumesh63 on 2007-11-24
Try with sudo.
$ sudo ./dream.........
It should work then.

---

