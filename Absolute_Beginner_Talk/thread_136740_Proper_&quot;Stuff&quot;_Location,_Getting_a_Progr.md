---
title: "Proper &quot;Stuff&quot; Location, Getting a Program"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by Skizzler on 2006-02-26
Hey all, a few questions, I'm moving to Ubuntu on my laptop as my primary OS and there are some items I'm unsure about.  Basically it's where those who are Linux-knowledgeable put their stuff.  I tend to try to be organized and put things in a more or less logically "proper" place, but due to my noobitude I need some help finding these proper places, if they exist.

1.  Wallpapers. I used to dump them all in windows/web/wallpaper, is there a "good" place to put them on Ubuntu?  Right now in my home folder I've made a wallpaper folder.

2.  Code Control.  I'd like to set up and learn to use a revision control system as I start working on some larger projects for school classes and personal use.  I am running Automatix so it seems like I won't be able to use Synaptic to find and install this program.  I'm pretty sure I'm not supposed to run Synaptic with Automatix installed, since it's an "important note" on top of the Automatix thread.  Is there an apt-get way to install RCS?  If not, and I have  to manually install a package, where should I put it?  (Also, is there a good way to find out what programs I can apt-get if I don't know they're out there in easy-to-get form?)

3.  Code.  Is there a proper place to put the code directory for the projects I will be working with?  It seems like most stuff would go fine with its own directory in the 'home' directory for my user, but who knows, coding projects might be different?

---

### Post by senning on 2006-02-26
Since it doesn't look like GNOME autodetects wallpapers in any folder that's user writable, it shouldn't matter where you put them.  You can always just drag your image files on to the desktop background preferences window, and let it take care of itself.

2. I think that it means you shouldn't run automatic and synaptic *simultaneously*, not that you can install using both at different times.  Are you actually working with GNU RCS, though?  I don't know about these things, but I thought CVS and Bazaar were the new hotness.  If you are using RCS, though, then "sudo apt-get install rcs" should work fine.  You can find what's available in the ubuntu repositories through synaptic, of course, or packages.ubuntu.com.

3.  Again, totally up to you.

---

