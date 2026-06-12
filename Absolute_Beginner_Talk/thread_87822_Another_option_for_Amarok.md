---
title: "Another option for Amarok?"
date: 2005-11-08
forum: Absolute Beginner Talk
---

### Post by jrincon87 on 2005-11-08
Hey.
I started using Amarok and I think it's the best music player I've ever seen for Linux. The problem is that I used to be on WinXp. So the half of my music is in wma format. But I couldn't play no wma file in Amarok. I went to the KDE page and the instructions to make the Amarok recognize the wma files is patching the Taglib. But I have no idea in how to rebuild some program with a patch included. Any body knows how to do this? Or maybe some program with most of the features of Amarok? (Have Breezy with Gnome).
Thanks.

---

### Post by i3dmaster on 2005-11-08
You posted in a wrong place.

**Edit**: I moved it. In the future, if you notice someone posted in the wrong place, report the post instead of writing a post like this. --aysiu

---

### Post by aysiu on 2005-11-08
These links may help you:
[http://www.linuxforums.org/forum/topic-57225.html](http://www.linuxforums.org/forum/topic-57225.html)
[http://www.linuxforums.org/forum/post-312362.html](http://www.linuxforums.org/forum/post-312362.html)

Did you know you can use AmaroK in Gnome, though? KDE apps work in Gnome. They may [act quirky in some ways](http://www.ubuntuforums.org/showthread.php?t=59132), but they work.

---

### Post by 23meg on 2005-11-08
I think there's nothing quite as advanced as amarok. As a GTK alternative you may want to look into Banshee, which isn't quite close in terms of features.

---

### Post by jrincon87 on 2005-11-09
I KNOW I can use Amarok in Gnome. I'm using it right now. That's why I say is the best player for Linux i've EVER seen. I know XMMS and Totem and Mplayer, but they lack of all the features Amarok has. So I was wondering how I could patch Amarok to work fine with wma's, or if there's a program as advanced as AmaroK.
I'm gonna try Banshee by now.
Thanks 23meg.

---

### Post by 23meg on 2005-11-09
No problem. Also note that the version of Banshee in the repositories isn't quite up to date; you should be able to find info on how to compile the latest version if you do a forum search.

---

### Post by BLTicklemonster on 2005-11-09
So if he lived where it wasn't illegal to install the swodniw codecs, would installing them make the music play?

---

### Post by 23meg on 2005-11-09
[QUOTE=BLTicklemonster]So if he lived where it wasn't illegal to install the swodniw codecs, would installing them make the music play?[/QUOTE]

Sorry I don't quite follow this.

BLTicklemonster, it seems a deb package of the latest banshee was posted in [this thread]("http://www.ubuntuforums.org/showthread.php?t=85015").

---

### Post by BLTicklemonster on 2005-11-10
It seems the windows codecs aren't legal to install in some places, right? 

And amoroK is absolutely awesome. I checked it out yesterday morning. I love being able to look up lyrics and info on the artists while listening to a song.

Thanks for the link.

---

### Post by BLTicklemonster on 2005-11-10
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

is enabled, yet I get 

bill@ubuntumonster:~$ $ sudo apt-get install banshee
bash: $: command not found

after updating

---

### Post by Pablo_Escobar on 2005-11-10
BLTicklemonster
You've enabled the source repository, you need to enable the binary repository (src stands for source):

Try this one :)

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

---

### Post by jrincon87 on 2005-11-11
I tried Banshee and it's good but it doesn't compare to AmaroK. I'd like to continue using AmaroK without having to rerip all of my music that's in wma format. So, anybody knows how to rebuild the Taglib library with the patch offered by KDE? Or, anybody knows a plugin I can download for AmaroK to make it work properly with wma's? BLTicklemonster, what are those swodniw codecs you're talking about, and where can I download them from?

---

### Post by Jussi Kukkonen on 2005-11-11
As far as I know Amarok does play wma, you just have to use xine or arts-engine. However, you can't add them to your library (because of the taglib problem), you need to use the files-tab to select stuff into playlist. Yeah, it goes against the whole idea of amarok, I know.

By the way, you don't have to patch the code yourself, there is a patched source release: [http://www.cs.berkeley.edu/~ushankar/taglib-wma/#mozTocId883978](http://www.cs.berkeley.edu/~ushankar/taglib-wma/#mozTocId883978)
Only supports reading the tags so far.

---

### Post by mlomker on 2005-11-11
[QUOTE=BLTicklemonster]bash: $: command not found
[/QUOTE]

You seem to be typing in the $ sign, but that's just the prompt.

---

### Post by jrincon87 on 2005-11-11
> By the way, you don't have to patch the code yourself, there is a patched source release: [http://www.cs.berkeley.edu/~ushankar...mozTocId883978](http://www.cs.berkeley.edu/~ushankar...mozTocId883978)
Only supports reading the tags so far.
I downloaded the file but the terminal prints the following:
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
/bin/sh: /home/jrincon87/Mis: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Why is that?
Also, I had forgotten to ask why is the AmaroK's volume so low in comparision to the other programs like the system sounds, XMMS, Rhythmbox, etc.? (I'm using the Xine engine, if that serves).
Thanks.

---

### Post by Jussi Kukkonen on 2005-11-14
Did you do *sudo apt-get install build-essential* to install your development environment?

I don't have the volume problem you describe.

---

### Post by jrincon87 on 2005-11-14
I installed the build-essential but when I did the "make", and after a lot of things, this is the last thing that appeared:
/bin/sh ../../../libtool --silent --tag=CXX --mode=link g++  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wno-non-virtual-dtor -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common   -o libid3v2.la   id3v2framefactory.lo id3v2synchdata.lo id3v2tag.lo id3v2header.lo id3v2frame.lo id3v2footer.lo id3v2extendedheader.lo ./frames/libframes.la
ar: /home/jrincon87/Mis: No such file or directory
make[5]: *** [libid3v2.la] Error 9
make[5]: Leaving directory `/home/jrincon87/Mis descargas/taglib-1.4/taglib/mpeg/id3v2'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/jrincon87/Mis descargas/taglib-1.4/taglib/mpeg/id3v2'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/jrincon87/Mis descargas/taglib-1.4/taglib/mpeg'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jrincon87/Mis descargas/taglib-1.4/taglib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jrincon87/Mis descargas/taglib-1.4'
make: *** [all] Error 2

What am I lacking of?

---

### Post by timczer on 2005-11-15
There is a script that will convert wma files to mp3's.  I wish I could remember where I got it from to credit the author.  You place it in the nautilus-scripts folder in .gnome2 in your home directory.  Right click the wma and choose scripts and "wma to mp3" script.  It will convert every wma in the folder to an mp3.

---

### Post by jrincon87 on 2005-11-15
> There is a script that will convert wma files to mp3's. I wish I could remember where I got it from to credit the author. You place it in the nautilus-scripts folder in .gnome2 in your home directory. Right click the wma and choose scripts and "wma to mp3" script. It will convert every wma in the folder to an mp3.

I don't like those scripts. The resulting file's quality is pretty bad. Those scripts, convert the file to wav and then compress it into the format of your choise and the quality of your choise. So that, the file would be compressed twice (one, the original file, two, the resulting file).

---

### Post by BLTicklemonster on 2005-11-15
[QUOTE=BLTicklemonster]deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

is enabled, yet I get 

bill@ubuntumonster:~$ $ sudo apt-get install banshee
bash: $: command not found

after updating[/QUOTE]



WTH? I'll try it again, I don't remember typing a $.

---

### Post by Jussi Kukkonen on 2005-11-15
Your compile directory seems to be */home/jrincon87/Mis descargas/*, right?

Then, in the output:
*/bin/sh: /home/jrincon87/Mis: No such file or directory*
...there's your problem: Makefile doesn't like spaces in the directory name. Rename the directory.

---

### Post by jrincon87 on 2005-11-22
I decided to re-rip all my music in ogg format. Now the issue is that it seems to me that AmaroK "eats" a lot of system resources. It's pretty heavy. I think it'd work better on KDE, I haven't tested it yet. I'm really in love with AmaroK. I tried out Banshee but the version in the repositories isn't quite up to date, and I don't really feel like wanting to compile the 0.9.12 (??) version which I've heard, doesn't come with a HUGE improvement over 0.9.7. And I found Banshee a nice program but it sincerely doesn't compare with AmaroK. Does somebody know if it's worth compiling the 0.9.12 version of Banshee?
What I'm really looking for is a program with a good interface (like AmaroK, Juk style), art cover support, tag editor bundled, and more 'gnomeish', so that it won't use so many system resources. 
Anyway features like the OSD thing that appears at the top of your screen with the track information and the album cover everytime it changes a song, are EXTREMELY good. :( 
(I'm even considering using Kubuntu to have that gorgeous program working smoother, haha).

---

### Post by Jussi Kukkonen on 2005-11-27
What kind of problems are you having? My 400MHz Pentium with 128 MB of memory functions as a combined fileserver / folding@home-cruncher / amarok-jukebox very well -- The last time I rebooted was when Hoary came out...

[EDIT: I'm using xfce]

---

### Post by jrincon87 on 2005-11-27
I have an AMD Athlon 3400+, 256MB Ram, and I still think that AmaroK is pretty heavy. The load time takes too much and suddenly you have like no free Ram when you look at the *free* printout, specially when you have Firefox opened too.

---

