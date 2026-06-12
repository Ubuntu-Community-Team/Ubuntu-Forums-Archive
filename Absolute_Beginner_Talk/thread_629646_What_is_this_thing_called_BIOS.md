---
title: "What is this thing called BIOS?"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by rcarter0 on 2007-12-02
I have installed Ubuntu Server 7.04 on my old iBook G3, with the Ubuntu Desktop GUI installed. When I boot, I get a frozen screen with the desktop wallpaper, the tan sunburst background. No response to either the mouse or the keyboard.

I searched the forums and found [this thread]("http://ubuntuforums.org/showthread/php?t=418197") where the user describes the same problem, and says he eventually fixed it by disabling "most of the stuff in the system BIOS".

So: what is (are?) the system BIOS? I suppose I know that whatever it is, it contains stuff, and this stuff can be disabled. And when you disable the right stuff, things magically get better.

So how does one determine what to disable? And then disable it?

And, assuming that this is something that I would do from the command line, how do I get back to a command-line only system when my machine boots to a frozen desktop?

---

### Post by Dr Small on 2007-12-02
The BIOS is the "Basic Input Output System".
It is what tells the system to boot.

You can normally access the BIOS (before the system boots), by pressing Del, Esc, F1 or F2. Refer to your motherboard manual to find out how to access the BIOS for your system.

---

### Post by rcarter0 on 2007-12-02
Um... if a "motherboard manual" is what it sounds like, I'm pretty sure I don't have one. 

Where can I acquire one of these manuals for an old Dual USB G3 iBook?

---

### Post by Flying caveman on 2007-12-02
it took me a minute to google G3 ibook BIOS.  hold down the "c" key while starting up

---

### Post by kellemes on 2007-12-02
I don't know how to access BIOS on a Mac I'm afraid..
I just wonder how disabling stuff in BIOS will help fix your problem..

Can you tell a little more about this issue?
Did you just installed Ubuntu or did it work in the past?
Have you installed a driver for you Graphic-card?
How did you install the GUI, and what have you done to configure Xorg?

Not sure if I can help you since I don't own a Mac but you never know.. :popcorn:

---

### Post by Jerry N on 2007-12-02
Since you have a Macintosh, none of the information about a PC's BIOS will be valid.  Be absolutely certain you know what you are doing before you start changing BIOS settings - it is really easy to render your computer unbootable which would force you to figure what motherboard jumpers to mess with to reset the BIOS back to default parameters.  There is even a possibility of causing physical damage to the computer if you fool around with voltage and clock speed settings.

Jerry

---

### Post by irish_flu on 2007-12-02
Previous posters are correct, your G3 doesn't have the thing that PC users are talking about when they say "BIOS".

It technically does, but it's not accessed by on like it is on a PC, and I'm fairly certain that it wouldn't help you out anyway.

You'll get the best help by asking your question in the Apple PPC forum, as any hardware-related stuff that we're talking about in most of the other forums won't apply to you.

Here's a link to the Apple PPC forum:
[http://ubuntuforums.org/forumdisplay.php?f=133](http://ubuntuforums.org/forumdisplay.php?f=133)

Good luck with your Mac!  If this were Mac OS you were working with, I'd suggest that maybe your PRAM needed "zapped" by holding down command+option+P+R and then starting up your computer, letting it reboot several times.  I'm not sure what to tell you with Linux, though.  I'm sure it's something different....

---

### Post by rcarter0 on 2007-12-02
Replying to kellemes:

I described the situation in [another post]("http://ubuntuforums.org/showthread.php?t=629163") on the Apple PPC Users forum, you can get some more of the backstory there. (So far 20 views, no replies.) 

All I really want is a little LAMP server of my own, as a sandbox for PHP and web application programming. My first attempted installation worked, sort of-- the screen resolution was completely out of whack, but I could use the GUI. That was 7.0.4 desktop, before I realized that I needed the server version if I want to run Apache.

7.10 doesn't play well with PPC macs, so I had to hunt the web for a version of 7.0.4 server for PPC. The one I found installed a CMI-only version of Linux. This seemed to work OK, but I couldn't figure out how to do anything with it; the [How To: LAMP Installation for Noobs]("http://ubuntuforums.org/showthread.php?t=223805") thread and other sources of information I found all did things from a GUI perspective. So I attempted to install the GUI. The first attempt failed, the second one completed its installation but then I got the frozen desktop problem. 


Is it time for me to give up on Ubuntu and look for another way to set up my server?

---

### Post by Dr Small on 2007-12-02
You didn't need to install a server edition just to install Apache. You can use your desktop as a server, or server as a desktop. It just depends on what you want to really do with it. They are both capable of the same things.

Dr Small

---

### Post by rcarter0 on 2007-12-02
Oh. Thanks, that's good to know.

Although I should say, when you know you want a LAMP install, and there's a server version that prominently offers a LAMP option in the installation process and a desktop version that doesn't, it's kinda easy to assume that you want one and not the other.

So about that "depends on what you want to do" qualifier: as I mentioned before, I want to set up a LAMP server that would probably not see a whole lot of traffic, but would allow me to do all the LAMP stuff: serve data over the web, and perform server-side processing that involves PHP and MySQL. Some media, but nothing more than a few MB. It may host a personal website, but primarily it would be a place to play around with different web applications technologies/methods.

Would the desktop version let me do all that?

---

### Post by Dr Small on 2007-12-02
Yes. You can either install of the needed stuff from the repositories (php. apache, mysql, phymyadmin) or install Xampp, which in my opinion is much simpler and faster (which I use) and can be done like this:
[http://php.8ez.com/drsmall/blog/?p=96](http://php.8ez.com/drsmall/blog/?p=96)

---

### Post by rcarter0 on 2007-12-02
Thanks-- I followed the link from your blog to Apache Friends, and their [XAMPP for Linux page]("http://www.apachefriends.org/en/xampp-linux.html") says it's "for x86-compatible processors". 

Since I'm working with a PPC machine, should I forget about XAMPP and just install all the components separately?

---

### Post by Dr Small on 2007-12-02
I don't see where you would have any problem running XAMPP on your Ubuntu Distribution (after all, you most likely install i386 Ubuntu on your system, unless you chose something else), but you can install all of the stuff from the repositories:
[http://php.8ez.com/drsmall/blog/?p=142](http://php.8ez.com/drsmall/blog/?p=142)

One fault with installing from the repositories (as I quickly discovered), was there was no php5-gd2 extension, meaning I couldn't display Php images. But other than that, it worked fine.

Dr Small

---

### Post by rcarter0 on 2007-12-02
OK, now I'm confused. Everything I read indicated that for my particular iBook hardware (CPU: PowerPC 750cx), I should use the PPC version, not the i386... was I misinformed?

---

