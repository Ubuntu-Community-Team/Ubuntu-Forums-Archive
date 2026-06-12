---
title: "Error - Problem with gnuplot"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by b0rre on 2008-02-12
Hi!

I've just installed gnuplot with: sudo apt-get install gnuplot. But when i start gnuplot i get the following error:

borre@borre-desktop:~$ gnuplot

gnuplot: unable to open display ''
gnuplot: X11 aborted.

What am i doing wrong? I'm currently on a SSH connection to my server (if that matters).

Thanks in advance:=)

---

### Post by b0rre on 2008-02-12
Bump :P

I appreciate if someone can help me out as i've been googling for a solution many hours now.. :KS

---

### Post by buntu_Geek on 2008-02-12
You should install OCTAVE to use the GNUplot package....
Octave use it to plot graphs....

Octave is what is the equivalent of MATLAB in Linux..

---

### Post by herger on 2008-02-12
Hi all!
I have the same problem and I could'nt find any solution in all the internet.
I used to run Gnuplot under Fedora without any Octave installed.
I don't know what could be the cause, I installed gnuplot with Synaptic then disinstalled and reinstalled by compiling the package.
Besides this, there is the auto-completion problem, that MAYBE can be solved by 

./configure --with-readline=gnu

Anyway, I can't see any plot at all, the x11 terminal doesn't work at all........
Anyone could help, please??
Thanks and regards

Herger

---

### Post by herger on 2008-02-12
As I was saying before...
I installed octave and nothing at all.....

The terminal set by default is always 'unknown'
and if I put set term x11 it says 

unknown or ambiguous terminal type; type just 'set terminal' for a list

Any idea? Thanks 

H

---

### Post by tgalati4 on 2008-02-12
If you are in an ssh session, then you would need:

ssh -2 -Y you@yourmachine

The -2 and -Y sets up the proper X Windows environment to display x-applications in your local X session.

---

### Post by b0rre on 2008-02-12
Dunno, i'm stuck as well :( I dont think octave is required? The reason i want to use gnuplot is to plot some graphs from a data file (derived from a script) :)

---

### Post by b0rre on 2008-02-12
> **tgalati4 said:**
> If you are in an ssh session, then you would need:

ssh -2 -Y you@yourmachine

The -2 and -Y sets up the proper X Windows environment to display x-applications in your local X session.

Hi!

I'm currently running Putty from a windows machine. How can this be accomplished here?

---

### Post by Jimcanoa on 2008-02-12
Oh, if you're using putty that complicates things. I'm not sure you will be able to do X11 forwarding at all with putty. You would need to have a X11 server installed on your computer, which I'm not sure you can do that in windows, in any case if it's possible I think it would be by installing cygwin, google that and you might find what you're looking for.

There is an easier solution though, download a virtual machine software, such as virtualbox, install linux and use it from there.

You could also tell gnuplot to create png's and copy them to your windows machine, using winscp for instance.

EDIT:
After some research I have to say I was wrong, in fact you can do X11 forwarding with putty: Putty Configuration -> Connection -> SSH -> Enable X11 forwarding. You need to have an X11 server installed on your machine for it to work, cygwin should work, but it's massive, the author of this guide: [http://solaris.reys.net/english/2006/04/x11_forwarding]("http://solaris.reys.net/english/2006/04/x11_forwarding") suggests using [Xming]("http://freedesktop.org/wiki/Xming") which is more light-weight.

---

### Post by herger on 2008-02-12
Hello
Excuse me, but my problem is more basical, I suppose.
I am NOT in a ssh session: i have some data on my pc and i would like to plot them.
Gnuplot x11 terminal doesn't work (with Gutsy)
What can I do?
Thanks and regards

Herger

---

### Post by b0rre on 2008-02-12
Hi!


Thanks for looking into it Jimcanoa, i'll check it out! I'll try the Cygwin approach first, then the second solution ^^ Thanks again! :)

---

### Post by herger on 2008-02-12
Sorry, I have problems with my connection and I don't know if my previous message was posted

Hello
Excuse me, but my problem is more basical than b0rre's, I suppose.
I am not in a ssh session and I do not use putty: i have some data on my pc and i would like to plot them.
Gnuplot x11 terminal doesn't work (with Gutsy)
What can I do?
Thanks and regards

Herger

---

### Post by Jimcanoa on 2008-02-12
herger:
I'm sorry I don't quite understand what your problem is, could you paste us the error it gives you?

thanks

---

### Post by herger on 2008-02-12
Hi! Thanks for Your reply.
When I start Gnuplot it says

Terminal type set to 'unknown'
gnuplot> 

If I try to plot any kind of data, it gives out no errors, but doesn't plot anything.
If I put

set term x11

it says
gnuplot> set term x11
                  ^
         unknown or ambiguous terminal type; type just 'set terminal' for a list

To plot something, I have to plot it in .eps and post-process it in gnome...
What can I do?
I am in "local" session: the data are on my pc and I am running gnuplot on it alone.

Thanks

H

---

### Post by Jimcanoa on 2008-02-12
what is the output of:
env | grep TERM
?

---

### Post by herger on 2008-02-12
Here it is

$ env | grep TERM

TERM=xterm
COLORTERM=gnome-terminal

---

### Post by drsaamah on 2008-02-12
im not quite sure what the problem is but... are you sure you should be setting the terminal type to x11?  if you're running on a linux (which is seems you are from your "env |grep TERM" output, you should be setting the terminal type to "xterm".
EDIT: My bad, I guess it automatically sets to x11 on xterm. It seems to be working for me.  Anyone else have an idea?

---

### Post by herger on 2008-02-12
Hi! Thanks.
Unfortunately it says

gnuplot> set term xterm
                  ^
         unknown or ambiguous terminal type; type just 'set terminal' for a list

I tried to install the gnuplot-x11 package manually, but it depends on gnuplot-nox it says....
I don't know what to do...
Thanks

H

---

### Post by Jimcanoa on 2008-02-12
How have you installed gnuplot? with apt-get? If you have compiled it maybe you haven't enabled x11 support... in gnuplot, does x11 appear in the list after doing 'set term'?

---

### Post by herger on 2008-02-12
No, x11 doesn't appear in the set term menu....
I installed gnuplot first with synaptic.
Then there was the tab-completion problem: so I had to re-install gnuplot manually doing

./configure --with-readline=gnu
make
sudo make install

I solved the completion problem, but I can't see anything in real time when I do plot or splot: as i said before, I have to plot figures in eps and then see them OUT of gnuplot with
display figure.eps

Thanks

H

---

### Post by Jimcanoa on 2008-02-12
Ok, I'm pretty sure it's sth related with not enabling X11 support when compiling. I think you should uninstall the program and recompile after doing some research on how to enable X11.

Nevertheless, instead of compiling it I would download the binary with apt-get. 

To remove the program you should cd to the dir where you did the make, and type ```
sudo make clean
``` (it's usually that, if that doesn't work try reading INSTALL or looking inside Makefile).

To install gnuplot with apt-get, do:

```
sudo apt-get install gnuplot
```
I'm sure that 10 seconds after hitting enter you will have a fully functional gnuplot!

good luck!

---

### Post by herger on 2008-02-12
Hi... I did it: i made sudo make clean in the directory i compiled before...
It said a lot of things, like when compiling (so I think, it should have worked).
Then I re-installed with apt-get.
I still have auto-completion with tab, but no images appear and the default temrinal is still 'unknown' and the x11 is not in the chances....
Thanks

H

---

### Post by Jimcanoa on 2008-02-12
What is the output of "echo $DISPLAY" ?
is it ":0"?
if it isn't try doing ```
export DISPLAY=:0
```

---

### Post by Jimcanoa on 2008-02-12
and the output of ```
gnuplot -V
```?

---

### Post by herger on 2008-02-13
Hi! Here I am.
The output for echo $DISPLAY was
$ echo $DISPLAY
:0.0

I did
$ export DISPLAY=:0
$ echo $DISPLAY
:0

I run gnuplot but always no plot at all and default terinal 'unknown' (with no possibility to set term x11).

The answer of gnuplot -V is

gnuplot -V
gnuplot 4.2 patchlevel 2

Thanks and regards

Herger

---

### Post by herger on 2008-02-13
Hello everybody.
I solved the x11 problem like this

- went into synaptic and uninstalled everything concerned with gnuplot
- in the shell I saw if there was anything else still related to gnuplot by means of
   whereis gnuplot
   I had still something (due to previous other installations) and I removed  
   /usr/local/bin/gnuplot
- I re-installed gnuplot through synaptic.
Now the x11 terminal works fine, **BUT there tab-completion problem has re-emerged**!!!!!!!!!!! :confused: :mad:
Between the two I choose to keep on working without TAB, for the moment...
I will keep on working to solve the completion problem.

Thanks to all for Your kind and precious help and the best regards

Herger

**NOTE**: I tired to recompile gnuplot starting from the source package with 
./configure --with-readline=gnu
make
sudo make install
the tab-completion works **BUT the x11 terminal doesn't work this way**

---

### Post by Jimcanoa on 2008-02-13
Hi herger,
I'm glad you finally managed to get gnuplot to work with X11! I believe that if the tab-completion doesn't work with the debian package it's because the package wasn't compiled with the readline option... So basically what you should do is keep compiling it for yourself until you get X11 working.

Now, if the tab-completion of gnuplot consists only of completing filenames there is a workaround: you could use rlwrap:

```

$ sudo apt-get update
$ sudo apt-get install rlwrap
$ echo "alias gnuplot='rlwrap -a -c gnuplot'" >> ~/.bashrc
$ source ~/.bashrc

```
After that gnuplot should complete filenames... If you still miss command-completion in gnuplot (I haven't used it, so I don't know if it has it) you should keep on working on the manual compilation ;) 

Let us know if this minor tweak works out, and if you stumble upon a better solution!

---

### Post by Jimcanoa on 2008-02-13
Quick question, could you run ./configure once more and paste the last part of the output, that is: 
```

gnuplot will be compiled with the following terminals:

  Standalone terminals: yes (always builtin)
    (aed512, aed767, aifm, bitgraph, cgm, corel, dumb, dxf, eepic, emf, emtex,
    epslatex, epson_180dpi, epson_60dpi, epson_lx800, fig, gpic, hp2623A,
    hp2648, hp500c, hpdj, hpgl, hpljii, hppj, imagen, kc_tek40xx, km_tek40xx,
    latex, metafont, metapost, mif, pbm, postscript, pslatex, nec_cp6, okidata,
    pcl5, pstex, pstricks, qms, regis, selanar, svg, starc, tandy_60dpi,
    tek40xx, tek410x, texdraw, tgif, tkcanvas, tpic, vttek)
  x11/xlib terminal: yes (with mouse support)
    (with multi-byte fonts)
    (with binary polygon protocol (EXPERIMENTAL))
  jpeg terminal: yes
  gif terminal: yes (with animated gif)
  png terminal: yes
    (jpeg, gif and png terminals can use TTF fonts)
  pdf terminal: no (requires libpdf)
  plot library terminal: no (use --with-plot to enable, requires GNU plotutils
...

```

As you can see, in my box, it says it will be compiled with x11/xlib terminal support... what does yours say?

---

### Post by Jimcanoa on 2008-02-13
I forgot to say that for me it works perfectly after doing a manual compilation: x11 support and tab-completion.
Altho I have to say, I'm not in Ubuntu, I'm in arch linux, that's why I'm asking...

---

