---
title: "[SOLVED] nvidia-settings doesn't recognize the existance of the nvidia driver."
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Sarteck on 2007-12-01
Let me begin at the beginning...  When I first installed Gutsy a while back, I used Envy to install my nVidia driver.  Everything went smoothly--I was really impressed!  Much better than the stuff I had to muck around with while on Feisty.

Recently, I've been noticing a diagonal "line" across the screen from the upper left to the lower right while I watch videos (and it doesn't matter which player I use, so I assumed it must be the video card settings).  I do a quick Google search, and it mentions something about an overlay type being "xv" instead of "opengl" for ATI cards.  Although I don't have an ATI card, I figure maybe there's something like that for nVidia cards, so I try to check it out by running "nvidia-settings".

Unfortunately, I get an error telling me, "**You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.**"

This is weird, because I -know- I am using the NVIDIA X driver.  I see the little nVidia screen with it's logo pop up every time I boot up my computer.  It's in my xorg.conf, too.  Finally, I'm running at 1680 x 1050, something I could not for the life of me get to work **without** having the NVIDIA X driver installed.



Now, last week I was trying out Compiz-Fusion, and though I liked it, decided that it was more hassle than it was worth to get the thing tweaked just right, so I removed it.  This is the only thing I can think of that might possibly have had something to do with my current problem.

I've tried doing as it says, running "**sudo nvidia-xconfig**" and restarting X, but it doesn't seem to change anything.



Any help is appreciated.

---

### Post by jken146 on 2007-12-02
I get the same error even though I am using the nvidia driver for sure.  Seems like a bug.

---

### Post by alienexplorers on 2007-12-02
You are running nvidia-glx-new.  This has the nvidia-settings program within it.

---

### Post by Sarteck on 2007-12-03
> **alienexplorers said:**
> You are running nvidia-glx-new.  This has the nvidia-settings program within it.So, er...  This might sound dumb, but how do we modify our nvidia-settings, then?  Sorry, I don't know a thing about graphics cards.

---

### Post by Sarteck on 2007-12-03
So I did some more searching and *finally* found an answer that worked for me!

See, when I was setting up Compiz-Fusion, I was following a guide that told me I had to install **xserver-xgl** as well.  Installing this, though, made it so that I wasn't really using the nVidia binary driver, I suppose.

after I **sudo apt-get remove xserver-xgl** and restart my X server, I have no problems.  :)  I can modify my settings via "nvidia-settings", AND there is no problem with that diagonal strobing line I mentioned.  glxgears reports twice the FPS that it was reporting before I got rid of that xserver-xgl, too, so I guess that's my regular FPS and the XGL was cutting it in half.

If anyone else has xserver-xgl installed, you may want to get rid of it.  I don't know how it will affect compiz-fusion. seeing as how I got rid of that already.

---

### Post by mdh on 2007-12-07
@Sarteck: A huge thanks. I have been bitten badly every time I try to wade into the compiz/beryl world. I had been frustrated trying to get the original binary driver from nvidia getting loaded and almost gave up on it... your suggestion on removing xserver-glx fixed the problem. Thanks! again

---

### Post by Sarteck on 2007-12-07
Kickasskewl!  :)  I'm glad this thread was able to help someone else out.

---

### Post by Borgeh on 2008-03-13
Hi,

I just want to thank you for helping me solving this. As you can see from the huge amount of posts (this single one), I actually made this user just to post a question about this. It seems my google searches weren't good enough, the moment I had typed in the title for my post this equal reply came up. Great system, so kudos also to the forum itself. 

I had installed via envy a number of times, I had used 'dpkg-reconfigure xserver-xorg', edited lots iof files... yet no solution to the last step, namely actually running the damned river! 

Now onwards, to compiz-fusion. So still some ways to go...
with regards,

Borge

---

### Post by rubbrduck on 2008-03-26
Thank you so very much. I was going to do something very bad. :-)
You really helped and you should be very proud of yourself, mate

---

