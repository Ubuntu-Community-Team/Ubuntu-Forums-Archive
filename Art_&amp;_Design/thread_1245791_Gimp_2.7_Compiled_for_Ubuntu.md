---
title: "Gimp 2.7 Compiled for Ubuntu"
date: 2009-08-20
forum: Art &amp; Design
---

### Post by gali98 on 2009-08-20
NOTE: As Labello pointed out below, there is a PPA for gimp 2.7. I have not tested it out so you will have to try it for yourself:
[https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn](https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn)

NOTE NOTE:
After posting this, I realized that I should have told you this is compiled on x64. So if you need 32bit use the above link.

Hello all!

    Today I saw that Gimp 2.7 (an unstable release towards 2.8 ) was released a few days ago, and decided to try it out after reading the release notes:
[http://gimp.org/release-notes/gimp-2.7.html](http://gimp.org/release-notes/gimp-2.7.html)

I had a hayday compiling it (Had to also compile some separate libs) so I wanted to save any of you non-compiling ubuntu artists the trouble and give it to you...


The main reason I tried it is because now Gimp supports > rotating brushes and has had additional enhancements to the brush dynamics engine, for example allowing to base dynamics on tilt and dynamically change the aspect ratio of brushes. 
And I tell you, it's pretty stinking sweet... It is nearing the brush dynamics you can do with photoshop. Just hit the release notes link above to see all the new stuff...

Edit: Having Trouble Uploading... Moving to my server for now.
(If I have bandwidth issues I will take it down and move to an uploader that works :) )

[http://theprinceonline.info/gimp-2.7.tar.bz2](http://theprinceonline.info/gimp-2.7.tar.bz2)

MD5:27b9ca103389fe911bb215711f0338fd


Instructions: Download tar.bz file and extract in /opt directory (so it looks like /opt/gimp-2.7/*)
Then download the attached script and take the file extension off (so it is just named gimp-2.7) and make sure it is executable... You can do this by typing in a terminal:
```
chmod +x gimp-2.7
```
in the same directory.

Now all you should have to do is type "gimp-2.7" in a terminal and everything should work.
IF it doesn't, just copy and paste *all* the terminal output, and I will figure it out. (I may have missed a lib... It's easy to do...)
Have fun!


Thanks,
Kory

---

### Post by Labello on 2009-08-21
Hi,

nice work, but there is already a PPA for this purpose:

[https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn](https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn)

It should contain builds for jaunty and karmic

---

### Post by coldReactive on 2009-08-21
x64 GIMP is unstable too, and I know how unstable it is (menus might not show grayed out items.)

Thanks but, I'd rather stay with stability.

---

### Post by gali98 on 2009-08-21
@labello
    Are you serious? Ugh. Dumb... lol I guess I could have done a bit more searching ;)
Thanks... But I'll leave this up anywho...
Kory

---

