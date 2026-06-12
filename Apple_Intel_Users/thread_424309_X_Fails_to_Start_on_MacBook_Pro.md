---
title: "X Fails to Start on MacBook Pro"
date: 2007-04-26
forum: Apple Intel Users
---

### Post by bcr88 on 2007-04-26
Ok, I know other people have already posted about this, but I figured I'd tell my short story.

I played around with Edgy and then Feisty Herd 4 a few months ago, but I ended up deleting it.
So, then I downloaded the 64-bit version of Feisty the day it was released.

As many of you know, X failed to launch. Well, I thought it might have been the 64-bit version, but the same thing happened with the 32-bit version.

I read a post here about installing the fglrx drivers after viewing the output after X fails to start on the live CD. I tried that, but when I did tried to install the drivers, I got a message saying the files were temporarily moved or something (I can't remember exactly what it said, but the error number or something was 302).

Does anyone know what's wrong? I'm anxious to get Feisty installed. I'm sure it should be pretty simple, but I'm not that knowledgeable when it comes to things like this.

Also, would you recommend that I install the 64-bit or 32-bit version?

Thanks for the help!

---

### Post by rscow on 2007-04-26
My recollection:  I installed the 32 bit version on my MBP.

First installed the fglrx driver
Then I ran sudo aticonfig --initial
Then sudo aticonfig --overlay-type=Vx
Then startx

And from then on, I had X

Did you try this?

Roger

---

### Post by rscow on 2007-04-26
I'm no expert or nukyoolar genius, but:

Here are the links that saved my bacon in getting Feisty running on my MBP.  I am really pretty satisfied with how things are going.  It is the best Ubuntu distro I've used so far.  Of course, it SHOULD be .

Anyway, look at these:

[http://www.cs.helsinki.fi/u/jzshen/install_feisty.html](http://www.cs.helsinki.fi/u/jzshen/install_feisty.html)

[http://simon.vanderlinden.eu.org/howtos/macbook-emulate-a-synaptics-touchpad-with-ubuntu-gnulinux/](http://simon.vanderlinden.eu.org/howtos/macbook-emulate-a-synaptics-touchpad-with-ubuntu-gnulinux/)

[http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m](http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m)

The first one is another triple booting HOWTO...but it got my X running.  The second was INVALUABLE in getting my touchpad running.  It works just about perfectly.  I installed qsynaptic, by the way, to use for setting the touchpad variables.  The third was the key to getting Beryl up and running.  Don't forget to add Beryl-Manager in your startup sessions.  

It's amazing.  The volume up and down keys work.  The keyboard backlight works.  The screen brightness works.  If I could get hibernate/sleep to work it would be just about perfect.

Best,

Roger

---

### Post by bcr88 on 2007-04-26
Yeah, I did find the first link there in another thread, and that's what I tried, but when I tried to install the drivers, it said something about the files have been temporarily moved. I can't remember exactly what it said. Maybe I'll try it again in a little bit to see if it happens again and see exactly what the error is.

But thanks for the other links, I'll be sure to check those out once I get Feisty installed!

---

### Post by bcr88 on 2007-04-26
Ok, I tried it again, and here's the error:

**Failed to fetch [http://url-whatever/filename-etc.deb](http://url-whatever/filename-etc.deb)   302 Moved Temporarily   [IP: 91.189.88.40 80]**

Obviously, that's not the exact url and filename, it was much longer. If you need it, ask me. I was also wondering what the IP address was for, and why there was no dot between 40 and 80.

CAN ANYBODY HELP ME!?!?!

Thanks!

---

### Post by ronocdh on 2007-04-27
> **bcr88 said:**
> Ok, I tried it again, and here's the error:

**Failed to fetch [http://url-whatever/filename-etc.deb](http://url-whatever/filename-etc.deb)   302 Moved Temporarily   [IP: 91.189.88.40 80]**

Obviously, that's not the exact url and filename, it was much longer. If you need it, ask me. I was also wondering what the IP address was for, and why there was no dot between 40 and 80.

CAN ANYBODY HELP ME!?!?!

Thanks!
Are you plugged in via DHCP-enabled ethernet? Wireless will not work out of the box; it'll require setup later.

---

### Post by bcr88 on 2007-04-27
yeah, I'm plugged in.

I decided to download the alternate CD to install with, and it worked, of course.

But I installed to a USB hard drive to see if it would work and it doesn't.

But I guess that would be for a different thread.

If I get it to boot, I'll post back and tell if I got X to start.

---

