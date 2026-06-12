---
title: "A good MS Paint-like program?"
date: 2010-07-05
forum: Art &amp; Design
---

### Post by BlazeFire247 on 2010-07-05
Does Ubuntu have a program like Paint available? Or can Paint itself run through Wine?

---

### Post by SmokeyThePanda on 2010-07-05
[http://ubuntuforums.org/showthread.php?t=202729](http://ubuntuforums.org/showthread.php?t=202729)

It would appear to be a tie between tuxpaint and mtpaint. Have your pick. :)

---

### Post by BlazeFire247 on 2010-07-05
@Smokey

I went to the link and I tried gpaint, kolourpaint, and tuxpaint. It seems that I'd like to get KolourPaint, but I think it's for KDE only. I downloaded the "Generic Linux/x86 + KDE3 Binary v3 " one, but it's a .tar.bz2 and I'm not sure how to install it.

---

### Post by teejaybee on 2010-07-05
Is "The GIMP" too difficult for you to use?

It's a great program, but can get a bit tricky if you're only a novice at image manipulation.

---

### Post by BlazeFire247 on 2010-07-05
Actually, I was thinking of a program that could do some spriting/pixel art, and I think that Gimp is far too much for that..

---

### Post by SmokeyThePanda on 2010-07-05
You need to open up the terminal and get into the directory where the file is in. 

```
cd /home/yourusername/whereverthefileis/thefile 
```Then you need to run the following command.

```
 tar jxvf filename.tar.bz2
```

After this, open up the folder and read the README or INSTALL folder, depending on which one it has. Then follow the instructions for installing the program. It's usually something along the lines of ./configure --> make --> make install

I hope this helps.

---

### Post by BlazeFire247 on 2010-07-05
For some reason it won't install, but I found this instead:
[http://ubuntuforums.org/showthread.php?t=1373142](http://ubuntuforums.org/showthread.php?t=1373142)
Thanks for the help, guys!

---

### Post by robert shearer on 2010-07-05
'mypaint'  is worth a look. in the repos for Lucid.

---

### Post by ronnielsen1 on 2010-07-05
> I went to the link and I tried gpaint, kolourpaint, and tuxpaint. It  seems that I'd like to get KolourPaint, but I think it's for KDE only
kolourpaint is a good program. It will work, it will just pull in some kde dependencies with it. 

> Or can Paint itself run through Wine? 	
Actually it will but it's always better to try to go linux native (up to xp anyway, not sure about 7)

Check out the following:

[http://en.wikipedia.org/wiki/Pinta_%28software%29](http://en.wikipedia.org/wiki/Pinta_%28software%29)

[http://www.linux.com/archive/feature/129222](http://www.linux.com/archive/feature/129222)

---

### Post by V for Vincent on 2010-07-05
gnome paint?

[http://www.omgubuntu.co.uk/2010/07/daily-5-5-linux-equivalents-of-windows.html](http://www.omgubuntu.co.uk/2010/07/daily-5-5-linux-equivalents-of-windows.html)

---

### Post by Simian Man on 2010-07-05
I'm working on one called [Congo Paint]("http://code.google.com/p/congo-paint/") actually.  It's nearing the point where I would call it Alpha, and I haven't set it up to be easy to install/use yet.  In a few months it should be good to go though :).

---

### Post by finny388 on 2010-07-06
I've tried a few and settled on kolourpaint.

Works fine in gnome and installs easily from Synaptic.

---

### Post by ronnielsen1 on 2010-07-07
I like kolourpaint best too

---

### Post by hurstja on 2010-11-09
This is for my homies.

[http://www.ubuntugeek.com/pinta-paint-net-clone-for-linux.html](http://www.ubuntugeek.com/pinta-paint-net-clone-for-linux.html)

---

### Post by I'mGeorge on 2010-11-12
Why somebody would like something similar to MS Paint in linux too ?, when there's so many software that already does the basics and even more.

---

### Post by Swagman on 2010-11-13
What was wrong with Krita ?

---

### Post by Scayris on 2010-11-13
Well, you can just use the real paint, since it works perfectly in wine. You can easily install it through winetricks. Assuming you already have wine installed run this...

```
wget http://kegel.com/wine/winetricks && sh winetricks mspaint
```

Still, it looks ugly and doesn't fit in, plus it's usually better to run native apps, so if you find one that does what you need I encourage you to use that instead :p

---

### Post by jomaksmile on 2010-11-14
Actually I was thinking about a program that could do with some spriting / pixel art, and I think The Gimp is simply that too ..

---

### Post by emilywind on 2010-11-14
> **robert shearer said:**
> 'mypaint'  is worth a look. in the repos for Lucid.
Not really. MyPaint is a program aimed at people with graphics tablets, such as professional painters and others who like to paint, rather than people wishing to do simple pixel art or basic image manipulation. Or as they describe it.

"MyPaint is a fast and easy open-source graphics application for digital painters. It lets you focus on the art instead of the program. You work on your canvas with minimum distractions, bringing up the interface only when you need it."
- [http://mypaint.intilinux.com/](http://mypaint.intilinux.com/)

It is a great program and I use it myself, but I would not recommend it unless you have a graphics tablet and want it in order to paint. So in this case, it is out of the scope of what is wanted here. Cheers. :)

---

### Post by jharris1993 on 2013-01-24
> **I'mGeorge said:**
> Why somebody would like something similar to MS Paint in linux too ?, when there's so many software that already does the basics and even more.

Because most of the software I've seen out there is either an Adobe Photoshop, (etc.), wannabe, (too complicated for trivial tasks), or it can't find it's own *** with both hands and a map.

My situation:
I took a screenshot that included a GParted window, (that I wanted to capture), and all I wanted to do was open up the screen-shot, cut the GParted window out of it, open a new "picture", paste the cut image into it, and save it.

(I have to jump through these hoops because the current "take screen shot" application is about as useful as Teats on a Boar Hog.)

In MS Paint, this is trivial.

In Gpaint, I could not even find a "selection" tool that would allow me to select the region I wanted to capture.

My ultimate solution?  I saved the screen-shot to my file server, went to a Windows box, opened it in Paint, and did what I wanted to do.

It took me less time to do that than it took me to find and install Gpaint, try, grow frustrated with, try again, grow frustrated even more, (several more iterations), and then give it up as a bad deal all around.

And not for nothing, I really don't want to waste time effing around with installing, playing with, un-installing, (etc.), every doggone Linux "paint" program in the repos, just to see if it can do a basic image cut-and-paste.

And for the KDE fanboys, I'm not knocking KDE, I'm sure it's a wonderful desktop environment.  However, I'm currently running Gnome, (or whatever Ubuntu calls their desktop in 10.04), and I really don't like trying to install one stinkin' program and have it drag in darn near the entire KDE desktop as dependencies just to run it. . . .

It's like Apple.  You want to hook up an iPhone, or install iTunes, on a Windows box, and it drags in darn near an entire Apple O/S as dependencies.

What say ye?

Jim (JR)

---

### Post by sffvba[e0rt on 2013-01-24
> **jharris1993 said:**
> What say ye?

Jim (JR)

I say old thread is old (and now **closed**).


404

---

### Post by papibe on 2013-01-24
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

