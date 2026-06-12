---
title: "Resolution Scaling help.."
date: 2005-09-05
forum: Apple PPC Users
---

### Post by Eleaf on 2005-09-05
Hello!  I'm running a 500 mhz iBook with ubuntu quite fine.. = )..

It is running at 1024x768 fine however I am unable to set it to a lower resolution.  The resolutions are all there in xorg.  However, when I go to select the lower resolution, I just get a scaled desktop and then a bunch of lines and random stuff on the other part..  This is really bad for playing games that run in full screen and scale down the monitor as for i can only see the left 1/4 of the screen or so...  It works fine full sized though.

Does anybody know how I can get these lower resolutions working?  It would be great help!  =-)

---

### Post by Eleaf on 2005-09-16
Can anybody help me here?

---

### Post by RHTopics on 2005-09-18
I don't have an iBook, so take this information with that in mind.

Check out [http://penguinppc.org/~benh/](http://penguinppc.org/~benh/) 

Although this is an old web page, it may be still relevent to your situation.

I am assuming your are trying change the resolution on your LCD screen, not to an attached external CRT.  Below is a quote from this web page that may give you an option to use an external CRT.

 "It is possible to use all of the chip supported resolutions on the VGA output, but you should make sure you disable the LCD if you are in anything but 1024x768-60. I'm not sure if you may damage your LCD by doing so but it looks unsafe. I'll try to figure out a way to let aty128fb know about the LCD size and automatically switch it off on unsupported resolutions.
 
Additionally, you can pass aty128fb two parameters on the kernel command line, for example:

video=aty128fb:crt:1,lcd:0

Will boot the kernel with display on the VGA output only."

---

### Post by oswaldkelso on 2005-09-19
[QUOTE=Eleaf]Can anybody help me here?[/QUOTE]

I have the same problem here is the answer I think though Ive not tried it myself.

[http://ubuntuforums.org/archive/index.php/t-21481.html](http://ubuntuforums.org/archive/index.php/t-21481.html)

---

