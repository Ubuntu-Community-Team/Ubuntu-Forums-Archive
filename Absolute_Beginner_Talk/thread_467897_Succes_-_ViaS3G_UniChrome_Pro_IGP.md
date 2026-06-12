---
title: "Succes - Via/S3G UniChrome Pro IGP"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by gcos7 on 2007-06-08
:pSUCCESS - I have gotten my Via/S3G UniChrome IGP recognized so I have a higher resolution, gl support, and a 3D driver working!

I wanted to post this because I have seen MANY posts regarding this integrated graphics processor working in Linux, instead of using the "vesa" driver.

My laptop is a Gateway MX3215, but this may work for others as well that use the same integrated graphics processor.

 I did everything on this site:

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

2 notes to the above:

      1)  Since I am running Ubuntu 7.04, I had to do the extra edit as described in a link on this 
           page to comment out part of a C file, then rerun the last 2 items as described

      2) I tried things out with WINE config and also with the Freecell card game, and found
          that my mouse pointer would disappear.  The "problems" section at the end of this
         page mentioned putting "Option  SWCursor  "True" to the device section (I initially
         thought this meant the mouse, but after that failed I realized it actually meant the 
        "Section  Device"  area where the video driver (now "via") is described - add the line
        just prior to the end of that section).

I hope this works for others as well.

Now  2 questions:

    - is there a way to have multiple resolutions availabe?  Trying to change the screen
      resolution via the system/preferences/screen resolution to anything other than the
      default causes the screen to look as if a sync is off somewhere as it ends up mainly
      a bunch of lines where you can sort of see multiple pieces of the desktop all over
      the screen.

    - has anyone had any success at getting Family Tree Maker 10.0 running
      completely with WINE?

---

### Post by Neeks769 on 2007-06-23
hi, I'm trying to get this working, but I'm having a problem.

When i get down to 'svn checkout [http://svn.openchrome.org/svn/trunk](http://svn.openchrome.org/svn/trunk) openchrome', it says the following:


svn: PROPFIND request failed on '/svn/trunk'
svn: PROPFIND of '/svn/trunk': Could not resolve hostname `svn.openchrome.org': No address associated with hostname ([http://svn.openchrome.org](http://svn.openchrome.org))


I don't know what to do. Sorry if i sound like an absolute noob...it's cause i am one :P

---

### Post by gcos7 on 2007-07-03
The only think I can think of to try, is to put  "sudo" in front of everything on that page that doesn't already start with that.  I noticed at the top of the page that it assumes you have administrative privileges.  In Linux, that is normally reserved for the "super user" or "root".  By default, Ubuntu comes with the root user login disabled so that beginners hopefully can't do too much damage to their systems;)  This leaves only "super user" access.  To run a command as the super user, you must prefix it with "sudo"  (i.e., do this as super user).  While their are some commands on the page that don't have the sudo prefix, I just assumed it was needed for everything since it says you need administrative privileges.;)

I hope this works for you!  If not, repost and we'll see if we can get an answer somewhere.  I'm no Linux expert either, so we are both just starting out!:):)

---

### Post by dkaddict on 2007-07-04
Seems to me like you may not have installed all of the dependencies needed to get the svn bit to work. 

If you go here>>>

[http://www.google.com/linux](http://www.google.com/linux)

and enter>>> 

 svn: PROPFIND request failed on '/svn/trunk'
or
svn: PROPFIND of '/svn/trunk': Could not resolve hostname `svn.openchrome.org': No address associated with hostname ([http://svn.openchrome.org](http://svn.openchrome.org))

in the search bar

you will get a load of results.:)

I remember one of my first attempts at installing the driver failing because of my jumping the gun and thus not having the requisite libraries.](*,)

 If you have, on the other hand, done everything correctly and are still having trouble downloading the source code, post a plea for help here and I will send you the openchrome trunk driver(If, of course, you need the 'trunk' driver as opposed to the 'experimental' one needed for the 64 bit K8M890 chip set). Then you can cd to the directory and run ./autogen.sh --prefix=/usr and all that follows.
Hope you get it sorted m8.

 I have used that how2 a few times now (I have a habit of wanting a clean comp so have done many a fresh install) with no probs if I stick to the guide. I have a copy of the trunk driver waiting to be compiled cos I know it works on my machine and will always be able to use it if, say, I do a fresh install but my internet is broken...blahblah blah

peace

dk

---

