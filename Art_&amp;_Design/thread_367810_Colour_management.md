---
title: "Colour management"
date: 2007-02-22
forum: Art &amp; Design
---

### Post by chaosmedia on 2007-02-22
Hi,
I'm pretty new to Ubuntu (and Linux in general) and have a few questions regarding colour management. I just started to get to grips (a little at least) with it all in Windows and then I switched to Ubuntu to make everything more complicated.. ;-)

I have a premade ICC profile, which I created on my dual-boot Windows installation using a Greag-Macbeth Eye-One Display 2, which i put in /usr/share/color/icc. The question I have is which the best way to load it into the LUT would be? Currently I downloaded xcalib and run the following as a startup program in my Gnome session:

   xcalib -d :0 -s 0 -v /usr/share/color/icc/Monitor_2007-02-10_1.icc

There's just so many ways to do things (like using LProf), that I ge confused if I'm either not doing it the best way or if I'm simply doing it wrong.. :confused: 

Also, I downloaded the ICC profiles for Scribus and I think I've setup everything correctly in there, but I was also under the impression that Inkscape would support colour management but I couldn't find any settings for choosing a profile. Same thing about Xara Xtreme..

Cheers,
Henrik

---

### Post by tiggs_the_cat on 2007-02-26
Hello,

I can't give you an answer but I'd be interested in this too, so I'm bumping this thread up. :D

---

### Post by mixersoft on 2007-09-08
same problem. bump.

---

### Post by gigake on 2007-09-10
bump

---

### Post by jcornuz on 2007-09-11
OK, I'll try to give an answer :)

I do photography under linux (see my site down there) and I managed a satisfying workflow.

1) create a monitor profile (under winXP, but some hardware is also supported by Linux, AFAIK).
2) load it with xcalib (I have a script which I run if needed so I can check that the data is indeed loaded; there is a command to remove any LUT information, check xcalib --help).
3) load the same profile in your application, (gimp 2.4rc should work, I use cinepaint); chose your editing profile (sRGB or AdobeRGB).

You have a working color managed display.

Printing is for the next lesson :)

Take care,

Joel

---

### Post by chaosmedia on 2007-09-13
Woah.. I wrote this post a long time ago; didn't think it'd be updated again.. ;)

Joel, thanks for your information. The way I do it is pretty much the same as you are (although the applications I use are mainly Bibble & Raw Therapee among others).

As Joel wrote there's three steps involved:

1) Create a monitor profile
2) Load the profile's LUT
3) Use the profile in a colour aware application

For 1 pretty much the only option for a while has been to dual boot an XP installation and create the profile using whatever software in Windows (unless you have old and/or expensive hardware), and then copy (or mount the Windows partitions) the profile to Linux. However, nowdays Argyll ([www.argyllcms.com](www.argyllcms.com)) supports the Gretag-Macbeth EyeOne (which I use) so you can create the profiles without booting to XP. I haven't experimented much with this yet (I've only used it on a beta-stage), but if you read the Argyll mailing-lists people are having good results with it.

For 2 you can either use xcalib as I used to do (and Joel does), or Argyll (dispwin). Xcalib has the extra feature that you can easily unload the LUT, but I prefer to use Argyll because Graeme (the author) seems to be the KING when it comes to Linux colour management.. ;) It's simply a matter of taste. Put the call to xcalib or dispwin in a startup script or in a session command.

Number 3 is easy; just make sure the apps you use are colour aware and make it use you steaming fresh profile (you usually have to restart the app after you've changed the profile).

---

### Post by exaudio on 2007-10-25
I want to have a calibrated display in Ubuntu. I used a Spyder2 to calibrate my display from my Win XP partition. Spyder2express (2.3.3-1) produced a color profile called "Spyder2express.icm". I copied that file into my Ubuntu partition, but xcalib wouldn't load it.

Will xcalib read both icc and icm files?
Is a ".icm" file the same as a ".icc" file? 
If not, how do I convert a ".icc" file so I can load it with xcalib in Ubuntu?

thanks.
--

---

### Post by imopen on 2007-10-25
Excuse me, maybe I go partially off topic, but I have a problem.

I have my monitor calibrated with right profile, profile loaded with xcalib.

When I return back from a screensaver I lost every settings of profile, it seems that settings are overwritten or unloaded. :(

I have to relaunch the script manually.

Do you know if there is a way to prevent screensaver from unload xcalib settings, or to relaunch xcalib automatically when screensaver exit?

Thank you in advance.

---

### Post by Curtiss on 2007-10-25
Heres my way the poor mans way. I just go here [http://www.normankoren.com/makingfineprints1A.html#Monitor_test_pattern]("http://www.normankoren.com/makingfineprints1A.html#Monitor_test_pattern")
and use the gamma charts to calibrate my monitor.

What I do is contrast to 100 % then back down the brightness till you get it where you want using the gamma charts. If needed you can further tweak the setting using the gamma command in a terminal window.

This has work good for me. I have most of my printing down at Costco in the US 8X12 or smaller and the prints have been a very close match to my monitor.

I also make sure my files are embedded with the srgb profile.

I also have a HP 8750 and get very good results I let the printer handle the color management.

Note I use a CRT and not a LCD.

I did try using a profile created by adobe gamma from XP for my monitor but didnt really see much of a difference.

---

### Post by cornelis1 on 2007-10-28
> **imopen said:**
> Excuse me, maybe I go partially off topic, but I have a problem.

I have my monitor calibrated with right profile, profile loaded with xcalib.

When I return back from a screensaver I lost every settings of profile, it seems that settings are overwritten or unloaded. :(

I have to relaunch the script manually.

Do you know if there is a way to prevent screensaver from unload xcalib settings, or to relaunch xcalib automatically when screensaver exit?

Thank you in advance.

I had the same problem with a script I use to load the settings for my monitor, produced with a program called GAMMApage. Loading the script with a .xinitrc-file as discribed [here]("https://help.ubuntu.com/community/CustomXSession") solved it.

---

### Post by jcornuz on 2007-10-29
Hi there,

Just for the record, I have now started a blog on Linux Photography - covering subject like workflow, color management, RAW conversion, software availability, and so on.

It is not complete yet, but getting there. Have a look and check the table of contents for an overview of the entries...

[jcornuz.wordpress.com]("http://jcornuz.wordpress.com")

Take care,

Joel

---

### Post by sruckh on 2007-10-30
I have the same issue with xcalib and no solution.  I do not believe adding anything to the .xinitrc file will make a difference.  The problem is not getting it to launch when the window manager loads.  The problem is that the settings are lost when returning from screensaver, powersave, etc.

I have added the script to my session Startup.  System->Preferences->Session and it loads fine on initial launch, but as the original poster mentioned, the calibration is lost once you return from screen saver.

Is there a script to add the xcalib call so that it is launched when returning from the screen saver?

Thanks.

---

### Post by cornelis1 on 2007-10-31
> **sruckh said:**
> I have the same issue with xcalib and no solution.  I do not believe adding anything to the .xinitrc file will make a difference.  The problem is not getting it to launch when the window manager loads.  The problem is that the settings are lost when returning from screensaver, powersave, etc.

I have added the script to my session Startup.  System->Preferences->Session and it loads fine on initial launch, but as the original poster mentioned, the calibration is lost once you return from screen saver.

Is there a script to add the xcalib call so that it is launched when returning from the screen saver?

Thanks.

Have you actually tried the method I described in my previous post? Just out of curiosity I tried it with an xcalib script (which I normally don't use for lack of a descent icc-profile for my monitor). With this script I experience the same problem as you if I load it through my Session-startup (losing settings after screensaver etc.) Adding it to my .xinitrc-file really does the trick (don't ask me why it works, it just does, at least for me).

---

### Post by Dutch_Wolf on 2007-11-09
The problem of the screensaver overwriting the LUTs and gamma values is known a quick search in the gnome screensaver bug tracking systems show these 

[Bug 342850](http://bugzilla.gnome.org/show_bug.cgi?id=342850)
[Bug 469516](http://bugzilla.gnome.org/show_bug.cgi?id=469516)

Hope this helps.

---

### Post by jcornuz on 2007-11-10
Sefan Döhla, the author of xcalib, blogged about the issue. Did you check it?

[http://colorhacks.blogspot.com/2007/10/xcalib-and-linux-screen-savers.html](http://colorhacks.blogspot.com/2007/10/xcalib-and-linux-screen-savers.html)

Take care,

Joel

---

### Post by jespdj on 2007-11-27
> **jcornuz said:**
> 3) load the same profile in your application, (gimp 2.4rc should work, I use cinepaint); chose your editing profile (sRGB or AdobeRGB).
Note that color management in GIMP 2.4 is very limited and that GIMP 2.4 still contains a lot of code that is hard-coded for sRGB.

GIMP 2.4 will simply not work correctly if you set your editing profile to anything else than sRGB.

See for example [GIMP bug #499794](http://bugzilla.gnome.org/show_bug.cgi?id=499794).

---

### Post by Elle Stone on 2008-01-14
I just installed Argyll.  Actually I installed it twice, once from source following steps on JCornuz' blog (thank you Joel, I love your blog) and once again from binary.  I put the "from source" installation at /usr/local/src/argyllcms and the "from binary" installation at /usr/local/argyll.  The two installs are very different.  They both work (sort of, see below), but the "from source" installation has many more subfolders and seems to have more functionality.

See [http://www.freelists.org/archives/argyllcms/10-2007/msg00031.html](http://www.freelists.org/archives/argyllcms/10-2007/msg00031.html)
for both source and binary download.

See JCornuz blog: [http://jcornuz.wordpress.com/2007/11/16/spyder-the-good-and-the-ugly/](http://jcornuz.wordpress.com/2007/11/16/spyder-the-good-and-the-ugly/)
and also [http://www.argyllcms.com/](http://www.argyllcms.com/) online documentation for tips on how to install and use.  Not for the faint of heart, especially if like me you are a newbie to Linux.  

As mentioned on Joel's site, xicc was a problem when installing from source.  I ended up using the i386 version (my computer is amd64 and my ubuntu version is likewise 64-bit, but apparently Argyll is still adapting to 64-bits) as described here:

[http://www.freelists.org/archives/argyllcms/01-2008/msg00079.html](http://www.freelists.org/archives/argyllcms/01-2008/msg00079.html)

but don't really know if above step was necessary, as the whole "jam" thing had me puzzled and I went through a lot of gyrations trying to get a clean install.  My first "sh makeall.ksh" resulted in a long list of complaints.  My last "sh makeall.ksh" ouput was very short and only reported success.  

Some stumbling blocks and my solutions, so far:

My monitor profiling device is a Spyder 2.  To use the Spyder, you have to run the following command, quoted from the Argyll documentation [http://www.argyllcms.com/doc7/spyd2en.html](http://www.argyllcms.com/doc7/spyd2en.html):

spyd2en [-v] inputfile
 -v level      Verbose
 creates spyd2PLD.bin from vendor install files

Clear as mud, eh?  Well, being a linux newbie, I just confidently typed "spyd2en into my terminal and expected magic to happen.  It didn't.  What I got was 
bash: spy2den: command not found
which kinda sounds like maybe the installation failed.  

After much headbashing, I copied CVSpyder.dll from my old windows installation of the Spyder software, to /usr/local/argyll and typed the following at the command line:

sudo /usr/local/argyll/bin/spyd2en -v /usr/local/argyll/CVSpyder.dll

resulting in:
Size of input file '/usr/local/argyll/CVSpyder.dll' is 73728 bytes
Located firmware in driver file
Path to executables is assumed to be '/usr/local/argyll/bin/'
About to write binary '/usr/local/argyll/bin/spyd2PLD.bin'
Binary '/usr/local/argyll/bin/spyd2PLD.bin' sucessfully written

I repeated the above steps with the "from source" installation, fwiw.

Two things going on here so far.  One, neither source nor binary installation magically added any PATH information so that ubuntu knows where to look for the bare command.  And two, the "spyd2en" is not a good command for finding out if the argyll installation is actually working unless you know exactly what to type.  Try "dispwin" instead: nice squares of color get displayed on the computer screen (says the official documentation: By default dispwin will put a test window on the selected display, and display six test colors, before darkening  then brightening the screen by loading video LUT values, restore the original values and then exit).  If you use the installation from source, you get more squares and some beeps; installation from binary gives fewer squares and no beeps.  My beeps don't actually make any noise, though.  

How to get the path set so you don't have to keep typing the entire path into the terminal: there's probably better ways, but I edited /etc/environment and added ":/usr/local/src/argyllcms/bin" to the very end of the PATH statement.

then rebooted the computer.  Note that I used the "from source" installation here, as it has more functionality (or so it seems) and requires more typing.  If I want to use the "from binary" installation, I'll just type the whole path at the command line.

Figuring out how to set a permanent path took this linux newbie a couple of days of searching around the forums and the internet.  Which is the main reason for this post - to save a fellow photographer the hair-tearing I went through.

Alas I still haven't succeeded in profiling my monitor under linux.  See my next post for details.  Maybe someone (oh, I really hope so) has a solution and will share.

Elle

---

### Post by _obelix_ on 2008-03-26
Hi,

i have buy a Spyder2express and it works fine. To avoid the gnome-screensaver bug i use a little start script (loaded with Gnome autostart):

I must still change the location of dispwin and the profile.

```
#!/bin/bash
killall gnome-screensaver
/usr/local/src/argyllcms/bin/dispwin /usr/local/src/argyllcms/bin/benq_fp91g.cal
gnome-screensaver
```

This script kill the gnome-screensaver, load the dispwin Profile and then start the gnome-screensaver. Now gnome-screensaver not reset the dispwin calibration.

I read, the gnome-screensaver bug is fixed, but i don't know when it published. By then, the little script works fine on my PC and Notebook.

regards

obelix

---

### Post by imopen on 2008-04-14
> **cornelis1 said:**
> Have you actually tried the method I described in my previous post? Just out of curiosity I tried it with an xcalib script (which I normally don't use for lack of a descent icc-profile for my monitor). With this script I experience the same problem as you if I load it through my Session-startup (losing settings after screensaver etc.) Adding it to my .xinitrc-file really does the trick (don't ask me why it works, it just does, at least for me).

sorry for the very late answer, but i forgot this topic :lolflag:

yes, your tips works, using .xinitrc the screensaver doesn't reser the LUT loaded with xcalib

thank you very much ;)

---

### Post by kahuuna on 2008-08-10
> **cornelis1 said:**
> Have you actually tried the method I described in my previous post? Just out of curiosity I tried it with an xcalib script (which I normally don't use for lack of a descent icc-profile for my monitor). With this script I experience the same problem as you if I load it through my Session-startup (losing settings after screensaver etc.) Adding it to my .xinitrc-file really does the trick (don't ask me why it works, it just does, at least for me).

> **imopen said:**
> sorry for the very late answer, but i forgot this topic :lolflag:

yes, your tips works, using .xinitrc the screensaver doesn't reser the LUT loaded with xcalib

thank you very much ;)

What did you put in your .xinitrc? When I tried this for xcalib, it didn't work after gnome-screensaver:

Either
```

#!/bin/bash
xcalib /usr/share/color/icc/226BWSpyder2-B73C72.icm &

```

Or

```

#!/bin/bash
killall gnome-screensaver
xcalib /usr/share/color/icc/226BWSpyder2-B73C72.icm &
gnome-screensaver

```

edit:

Nevermind, I got it to work by removing the "&" sign at the end. Confusion to say the least?

---

### Post by shelyronald on 2010-05-22
I have the same issue.

Is there a script that is called when returning from screen saver where we could insert the call to xcalib?

---

