---
title: "new ubuntu (fluxbuntu) user..."
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by rious on 2006-12-17
I can't seem to figure out where the application files are for almost anything.
a quick example:
I want to simply extract a tarball with a couple of clicks.
I cant find the application file for cpio or really any of the extractors I have installed, So I can't   set any file associations "Set Run Action" in my rightclick menu. 
It also doesn't want to work from the console (any of the 3 that come with it) maybe I'm doing it wrong, but $ tar -x <filepath/filename> should do it right?
I think if I can get this figured out, I should be on my way to getting the rest, but I have been reading all morning and can't seem to find what I'm doing wrong.
I had just begun to feel slightly comfortable in normal ubuntu, enough so at least, that anything I wanted to do could be accomplished within a reasonable newb like timeframe with the mountains of available reference. Then I heard about fluxbuntu. When I heard fluxbuntu was "highly customizable" I didn't think I would need to set such rudimentary tasks... Is this the beginning of a mountain or did I just hit a learning curve?

---

### Post by ola on 2006-12-17
Hi,

Normally your the executable files for your applications are located in the /bin directory (for example cpio are).

To find files I use the command "locate" in a terminal (in the case of cpio you write locate cpio). Locate usually gives you a lot of hits but if you try to find the one in your /bin folder you can use that.

To use the commandline to extract the file; yourfile.tar you use tar -xvvf.tar. Look at the examples in the man-page for tar. It says:

EXAMPLES
       tar -xvvf foo.tar
              extract foo.tar

       tar -xvvzf foo.tar.gz
              extract gzipped foo.tar.gz

       tar -cvvf foo.tar foo/
              tar contents of folder foo in foo.tar

By running fluxubuntu you can probably learn a lot so if that's what you are after you are totally right! But if you just want to use your computer I would have gone with Ubuntu or Kubuntu. But it's good to try any other versions as well... You can also use Ubuntu and install fluxbox (or some other window manager) which will let you choose if you want to use Gnome or Fluxbox when you log in.. That could be a way of letting you have both.

Hope it helps! Good luck!

Best regards,

Ola

---

### Post by wrycatcher on 2006-12-21
Will going with Fluxbox windows manager on Ubuntu be roughly equivalent to using Fluxbuntu, or is there a more dramatic difference between the two?  I currently use xfce windows manager with Ubuntu Edgy---which is basically **Xbuntu**.  My other system (older Pentium 333) *might* end up being my Fluxbuntu experiment...

---

### Post by wrycatcher on 2006-12-21
Unbeknownst to me, someone had answered this very question!  [http://www.ubuntuforums.org/showthread.php?p=1912479#post1912479](http://www.ubuntuforums.org/showthread.php?p=1912479#post1912479)

---

