---
title: "Right, resolution still buggy"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Cilionelle on 2007-06-11
Hi all!  Still working on the kinks in my 845 Intel chipset.  Downloaded and run 915resolution (tho I might have done it wrong, I'll admit), have edited xorg.conf manually and have typed "dpkg-reconfigure xserver-xorg" many a time, to the point where my xorg.conf file *only* lists 1024x768 as possible resolution, no matter what mode.  I guess I would like to know where to now?  Is there a window manager other than X that I could try?  The X.org website says (basically) "Sorry, you're screwed", so that kinda put me off!

---

### Post by reidms on 2007-06-11
try running this to auto configure it

X -configure

---

### Post by Cilionelle on 2007-06-11
I got:

Fatal server error:
Server is already active for display 0
   If this server is no longer running, remove /tmp/.X0-lock and start again.

Should I quit X to run the -configure bit?

---

### Post by Nikron on 2007-06-11
> **Cilionelle said:**
> I got:

Fatal server error:
Server is already active for display 0
   If this server is no longer running, remove /tmp/.X0-lock and start again.

Should I quit X to run the -configure bit?

yes, kill X,  drop into  a tty, configure X, and then startx

---

### Post by Cilionelle on 2007-06-11
Due to the fact that the screen is so small, I can't see all the options... how do I get it to display one screen at a time?  (Like the -w option in DOS? I think...)

---

### Post by Cilionelle on 2007-06-11
Woe!  Woe!  Is there anyone who can answer?  Woe!

---

### Post by floke on 2007-06-11
You could try X-configure by booting in recovery mode, so that it doesn't start in the first place?

---

### Post by Cilionelle on 2007-06-11
My problem is more that I can't see the words, as there are only so many lines to the page.  How can I see the lines one page at a time, or one screen at a time or *x* number of lines at a time?

---

### Post by Cilionelle on 2007-06-11
Bumpo!

---

### Post by Cilionelle on 2007-06-11
Anyone?  Don't tell me there is no option for reading all the lines that flash past in the terminal window?

---

### Post by DBStevens on 2007-06-12
cat verylongfiletext file | more 

or 

more verylongtextfile will do the listing a screen at a time.

I found several mentions of a patch to change the memory allocation for your system.   Seems that the max memory is 1 Meg without the patch so there is no way to get 24 bit at the resolution you are trying for.

You might want to start here [http://ubuntuforums.org/showthread.php?t=94452]("http://ubuntuforums.org/showthread.php?t=94452")

---

### Post by Cilionelle on 2007-06-12
Thanks DBStevens.  Just wondering how I get the BIOS patch to run on Ubuntu, since it's a Windows .exe file.  Ta!

---

### Post by DBStevens on 2007-06-12
[http://www.chzsoft.com.ar/855patch.html]("http://www.chzsoft.com.ar/855patch.html")

There is light at the end you just have to follow all of the darn links.

---

### Post by Cilionelle on 2007-06-13
The .deb package link is down; how do I install it from the .tar.gz file?

---

### Post by DBStevens on 2007-06-13
Depends on what is in the tar.gz and what has to be done to get it to be activated.  I don't know.  I don't have the correct platform to really try it.   If I did have your computer I'd have already done it ;-) .

---

### Post by Nikron on 2007-06-13
Yeah you can use either flow control or by routing the output to a program like 'less'

In example, ```
 command here | less 
```

---

### Post by Cilionelle on 2007-06-13
The .tar.gz file is the source for the patch, and there are several files inside:
    [B]845patch.c
    makefile[/B]
    **/lrmi-0.8** with
        [B]lrmi.h
        lrmi.c
        makefile
        makefile.bsd
        vbe.h
        vbetest.c[/B]

---

### Post by Cilionelle on 2007-06-13
Can anyone tell me how to get this done?  I just want my full screen back *sobs uncontrollably*

---

### Post by DBStevens on 2007-06-13
Bad, bad, very bad,  no documentation in the tarball, but hey do you have the GNU C compiler on your system?

Normally a 

./configure

followed  by 

make

followed by

make install 

would do the trick for getting it compiled and placed where it needs to be as for integrating it with the start up processing (it has to be executed prior to the X server starting) I haven't a clue.  I have no documentation in the tarball to go on so I'd have to look everything over.

But then it isn't a web site (there is a web design book that is built on the "Don't make me think" model) so maybe some thinking along with a bit of reading and research is called for.

Hints:

1. Exercise your Google Fu.    Maybe there is another site that explains how to do it.

2. Did the author provide instructions on his web page dealing with the patch?

3. This party has a recommendation [Alien coming to a partial rescue ;-)]("http://www.linuxquestions.org/hcl/showproduct.php/product/2066/sort/2/cat/all/page/1")

---

### Post by DBStevens on 2007-06-13
Nikron,

Flow control, I couldn't hit the keys fast enough on my system, I'm slow and the system isn't.

One can also redirect the output to a file and open that file in an editor like say vi which beats the daylights out of that also ran emacs thing.

With that remark I put on my 'bestoes lined ceramic tiled armour and make a quick exit ;-) .

---

### Post by Cilionelle on 2007-06-14
Ack!  So close!  I actually got it to display at 1024x768... for a few moments, then restarted the computer and lost it - am now sitting with it telling me that it failed to start the X server.  And I can't read the text properly because it is trying to display it, at 1024x768 and about 2x the size, in a 640x480 window...  AAAGGGHHH!!! Is there an end to the torture?!

I suppose I better let you know what I did: first, downloaded and installed Alien (beautiful little program, really!) and converted the 845patch*.rpm file to a .deb file.  Running the patch, I changed the Video BIOS to 65536KB, or 64MB, which it is capable of.  I then did "sudo dpkg-reconfigure xserver-xorg" and pressed enter for the default settings until video memory, which I entered "65536" (KBs).  I then restarted X, got the 1024x768 login screen, logged in to have it change to 640x480 (shock horror!), then went to Screen Resolution and TA DA! there it was, the sacred 1024x768 option!  I skipped for joy to tell/show my wife, and she said, "You're sure?  You might wanna restart it, just to be sure..."  Like Adam with Eve, I took her advice, and despite that tantalising moment where I thought I shouldn't, I succumbed and bit deeply into the fruit... hence the situation outlined in the paragraph above...

---

### Post by Cilionelle on 2007-06-15
Well, the good news is I was able to set it up again, after a little strain and repetition.  I don't think the 845patch has a permanent effect... how do I run the patch as a part of my start up?

---

### Post by DBStevens on 2007-06-15
I think there may instructions as part of those links I provided.   The other thing is that the xorg.conf has to also have the memory information you used when you ran the patch.  I assume that since you were able to see the correct resolution on your monitor that you already did that part.

You are correct the change isn't permanent, you need a Bios upgrade as part of "properly"  correcting the issue.

In the mean time you could put the command to execute the patch inside the X server startup, or setup your own script to execute the command and using the init script call that script at the proper point in the start up sequnece.

Stick with it and it will get there.

Torture no, just simple sadistic pleasure  ;-) .

---

