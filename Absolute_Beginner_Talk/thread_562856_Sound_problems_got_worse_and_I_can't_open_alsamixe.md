---
title: "Sound problems got worse and I can't open alsamixer, HELP!!!!!!"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by Tangerina on 2007-09-29
So, I posted before because my computer speakers worked fine but I couldn't get headphones or microphones to work. I wrote to a friend and he taught me to get to the alsamixer through the terminal and I messed with the settings and fixed everything and finally it all worked! 

BUT! Last night we were going to hook my laptop up to a projector to watch a movie, and normally you press Fn+F4 to get the comp to recognize the projector, but it wasn't working with mine so my professor pressed Fn+ all the other F buttons (Fn+F1, Fn+F2, Fn+F3) multiple times to try to get it to do something. It still didn't work so they decided to use someone else's computer.

I turned my computer off and next time I turned it on I tried to play some music and it came out of the computer speakers so quietly I could barely hear it. I went into the normal volume controls and everything was set where it should be and it said that volume was at 100%. So I though, oh well, now I know how to use the alsamixer, so I pressed Alt+F2 and typed gnome-terminal into the Run Application thing, and then when the terminal came up I typed alsamixer, like I had done before, but this time it said:

alsamixer: function snd_mixer_load failed: Invalid argument.

So basically I'm thinking that when my prof pressed all my Fn buttons a million times it messed with something, and now I basically have almost no sound from the speakers, no sound from headphones, and I'm locked out of the alsamixer. I'm really not sure where to go from here. If you help me I'll love you forever, I had 3 tantalizing hours where my sound worked and now my problems are even worse.

---

### Post by Daveth on 2007-09-29
all the posts I have just checked on this point to a re-installation of ALSA as being a workable, if inelegant, solution to this problem.
The back end of this

[http://ubuntuforums.org/showthread.php?t=181186](http://ubuntuforums.org/showthread.php?t=181186)

points to sourcing the new version, though you might just as well get the standard one out of the Synaptic repository if it worked before. It seems so widespread I do not think we can blame your professor for all the problems!

---

### Post by Tangerina on 2007-09-29
Thanks!!! I'll look into this but might be bugging you again if it is over my head. People are awesomely helpful here.

---

### Post by Tangerina on 2007-09-29
So, I clicked on the link and downloaded the drivers and extracted the files so now I have a folder called alsa drivers but now what? This is the info from that other thread but I'm way too green to know what it means.

wget [ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2)
tar -xvf alsa-driver-1.0.14.tar.bz2
cd alsa-driver-1.0.14
./configure --with-cards=all --with-card-options=all
sudo make
sudo make install

---

### Post by Tangerina on 2007-09-29
PS Anyone want to walk me through step by step how to reinstall the alsamixer?

---

### Post by Tangerina on 2007-09-29
PPS What's synaptic repository? (Someone else set up my OS, shhhhh.)

---

### Post by Daveth on 2007-09-29
sorry- System/admin/Synaptic package manager, then enter your password,
then with the search icon at the top, search for  alsa. then add alsa-base back into your system. I think this is all you should need, unless someone else knows better.

Synaptic is where most of your programs will come from, so worth exploring a bit.

---

### Post by Tangerina on 2007-09-29
D'oh! I tried that (thanks for the tip, BTW, I'm glad I know about how to load that stuff now) but it didn't make a difference when I tried to access the alsamixer through the terminal, it still says "invalid argument." I tried rebooting and it didn't help. :(

Any further suggestions? Anything I should do with this folder of alsamixer drivers I downloaded?

Should I load any of the other alsa packages?

Whoever helps me fix my problem will have good karma forever, because I'm studying abroad away from computer nerds and I'm the nerdiest person here and I'm in way over my head. Thanks for all the helps so far.

---

### Post by Daveth on 2007-09-29
um, annoying. Does this spec match your own?

[http://www.burghardt.pl/wiki/articles/installing_and_using_debian_on_acer_aspire_5102wlmi](http://www.burghardt.pl/wiki/articles/installing_and_using_debian_on_acer_aspire_5102wlmi)

if so then the sound fix there which realised the same alsa error looks the way to go. The 

/var/lib/alsa/asound.state is not owned by you, but by root so you need sudo in front of your command in the terminal. So, open Nautilus and get down to /var/ lib/alsa/asound.state,then we need to rename it

```
sudo mv asound.state  sound.state
```

then paste each of the other commands into the terminal one after the other. To make the new /root/asound.state file, I think we need to do within the /root folder (so get there), then

```
sudo touch asound.state
```

then copy and paste the contents of that long link into the empty asound.state file. Then stick the last line into a terminal and pray:)

Alternatively, to completely upgrade alsa, paste each of those commands in the previouis link into a terminal, starting at the cd alsa-driver bit, i.e. you are running that command on that file, if you see what I mean.

I'm not too hot at terminal work, so if anyone wants to correct this, please please do- then we can all improve.

---

### Post by Tangerina on 2007-09-30
Thanks so much. I tried what you said about just typing in all the commands in the previous post because I wasn't sure how to do the other stuff you mentioned (I'm learning more each day, though!) and this is what happened. I'm still getting "Invalid agrument." Your other suggestions sound good but I'm not sure where to enter that stuff, but I'll mess around with it.



emo@emo-laptop:~$ cd alsa-driver-1.0.14
emo@emo-laptop:~/alsa-driver-1.0.14$ ./configure --with-cards=all --with-card-options=all
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
emo@emo-laptop:~/alsa-driver-1.0.14$ sudo make
make all-deps
make[1]: Entering directory `/home/emo/alsa-driver-1.0.14'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/home/emo/alsa-driver-1.0.14'

Please, run the configure script as first...

emo@emo-laptop:~/alsa-driver-1.0.14$ sudo make install
if [ -L /include/sound ]; then \
                rm -f /include/sound; \
                ln -sf /home/emo/alsa-driver-1.0.14/include/sound /include/sound; \
        else \
                rm -rf /include/sound; \
                install -d -m 755 -g root -o root /include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /include/sound; \
                done \
        fi
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1
emo@emo-laptop:~/alsa-driver-1.0.14$

---

### Post by Tangerina on 2007-09-30
So, my computer is a Toshiba and I think it has different hardware than the Acer in that post, but the same stuff might work?? I got as far as finding the folder /var/ lib/alsa/asound.state, but I'm not sure how to rename it or where to write that code. Also not sure which "other commands" you mean or how to copy code into the root folder, since there is nothing in my folder called root. Other than that, I think I get it. I'm learning.... sigh.

---

### Post by Tangerina on 2007-09-30
PS I installed GNOME ALSA Mixer just through the regular Add/Remove thing and it says it is added, and then I try to open it by clicking on the logo and a box appears at the bottom of the screen saying "Starting Gnome Alsamixer" but nothing actually happens or starts.

---

### Post by Tangerina on 2007-10-01
bumpity bump bump

I'm getting desparate :(

---

### Post by maryjanua on 2007-10-01
dunno if this helps cos im a newbie but i had to recompile my alsa to get it working

---

### Post by Daveth on 2007-10-02
yes, it looks like alsamixer is stuffed if you cannot just load it from Synaptic ! 

All the code before, and the code you need to add from the site I gave a few posts back (the "other commands") need to be added into a terminal - you can cut and paste commands into terminals quite happily. However, that task is complex if you work through that post. You tried loading up the alsa source code (the stuff you downloaded before) but we failed on that- I have never compiled anything so cannot spot the error in the message, but I guess the compiler was missing something for it to build alsa properly.

We need more skill here - hey guys help out!

---

