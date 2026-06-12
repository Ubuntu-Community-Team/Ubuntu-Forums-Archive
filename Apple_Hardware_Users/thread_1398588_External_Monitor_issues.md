---
title: "External Monitor issues"
date: 2010-02-04
forum: Apple Hardware Users
---

### Post by Jdutch101 on 2010-02-04
Hello, I am running Karmic on a first generation macbook (2006) and I'm curious about something. I have a 23" external monitor that I would like to be able to use, as well as my laptop monitor at the same time. I can get them to work under the "mirrored" configuration at low resolution 1080x(whatever the smallest one is). But when I uncheck "mirror" and then hit 'Apply', both screens go black, no image is displayed on either one and that's on the lowest resolution settings! Once the time delay counts down, I get back to the previous settings. What I'd like to do is have both screens running at their native resolution, side by side, so that I have two "desktop"s to work with. 

I read something about not being able to have Compiz running when the displays get to a certain size, and that's not a problem for me. I don't need fancy animations. I just want that set up to work and not have my computer crash every time I try to set it up this way. Perhaps my graphics chipset can't handle this, in which case could somebody tell  me that so I can stop trying to fix it? I also read that in order to do this, you have to modify an xorg.confi file, but I don't really know what that does, and I don't want to screw up my system by making any changes I don't quite understand.
 
I suppose the main problem is that I haven't found a guide to fix this in Karmic (lots in 8.01), but I'm not sure if it's similar or not. And I'm a n00b when it comes to computer programming of really any sort. (I know about four terminal commands). That being said, I'd like to learn, and if you can't provide me with a solution to my problem, perhaps you can point me to a site which will explain some more basic elements of programming, so that I may study at my leisure. 

Thanks in advance!

---

### Post by rogue_0111 on 2010-02-04
I use "lxrandr" for dual screens. Easy to set up and use.

To install:
apt-get install lxrandr

To use:
Open a terminal and type: lxrandr

A nice GUI pops up. Click the check box for the external screen and choose a resolution. Hit OK.

That easy. 
To end dual screen session, close the terminal.

---

### Post by Jdutch101 on 2010-02-05
Thanks, I'll give that a shot when I get home. I appreciate the response!

---

