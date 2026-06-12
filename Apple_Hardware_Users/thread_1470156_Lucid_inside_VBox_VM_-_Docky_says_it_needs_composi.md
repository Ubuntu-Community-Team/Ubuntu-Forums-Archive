---
title: "Lucid inside VBox VM - Docky says it needs compositing and other general problems"
date: 2010-05-02
forum: Apple Hardware Users
---

### Post by DarkestRitual on 2010-05-02
So I've got Lucid Lynx 64 bit installed inside of a VirtualBox VM. Guest additions are successfully installed, so I'm running in 1280x800 on my 2GHz Core 2 Duo aluminum MacBook. My VM has 2GB of RAM dedicated to it, along with 128MB of VRAM.

I'm definitely a Linux newb. I've been a MacHead since I was 4 years old and my dad brought home his old SE when he was getting his doctorate in 89/90. I'm playing around in Ubuntu for several reasons. Mainly, 1) I am looking to advance my knowledge of alternative OSes so I can continue to recommend non-microsoft alternatives. 2) It gives me a safe environment to learn how to UNIX script without trashing my main OS, Snow Leopard.

So, I don't mind the GNOME panel at the bottom of the window, but I would like to install a dock of sorts too, either pinned to the bottom or along the left side of the screen. Now, in my exploits last night, I found GLX-Dock (formerly known as Cairo Dock) and Docky were the two most recommended. I tried to install both. I installed GLX Dock first, and found that holy crap a lot of razzle dazzle is enabled by default. I could turn most of it off, but I couldn't find how to make the zoom with mouse hover-over inactive. Also, I couldn't figure out why, but there was this hideously large black bar covering the entire bottom 150 pixels of my screen. It looked horrendous.

Nix that, install Docky. I get an error message saying "Docky requires compositing to work properly. Please enable compositing, and restart Docky." Now, as far as I can find... I need to use Compiz to enable compositing? As far as I can tell, I have compositing enabled... why am I getting this error message, and why am I getting the same hideous black background stretching across the bottom 150 pixels or so of my screen?

Thanks for understanding my newbish nature. I want to learn though, I promise... and I learn quickly.

---

### Post by fabounet on 2010-05-03
I think you can't get compositing work in VM box;
that said, Cairo-Dock has a non-compositing mode (fake transparency), activatable in "System".
(PS : please use the latest version of the dock, the default theme is much more clean now ;-) )
[http://www.glx-dock.org/ww_page.php?p=From%20the%20repository&lang=en]("http://www.glx-dock.org/ww_page.php?p=From%20the%20repository&lang=en")

---

### Post by Troublegum on 2010-05-03
> **fabounet said:**
> I think you can't get compositing work in VM box;


VirtualBox best feature is that you can :)
You need at least VirtualBox 2.2 or highter, then you can activate 3D effects in your VM. Turn off your VM, edit the display settings in VirtualBox and activate the 3D Acceleration. 

Then start your VM. You need the guest additions (you already have these). 
Then in your ubuntu guest, go to the menu system->settings->appearance->visual effects. Activate the effects and close and restart docky.
See screenshot.
[[IMG]http://img685.imageshack.us/img685/4804/compizinsidevirtualbox.th.jpg[/IMG]](http://img685.imageshack.us/img685/4804/compizinsidevirtualbox.jpg)

It's not the fastest, but for testing its great.

---

### Post by DarkestRitual on 2010-05-03
> **Troublegum said:**
> VirtualBox best feature is that you can :)
You need at least VirtualBox 2.2 or highter, then you can activate 3D effects in your VM. Turn off your VM, edit the display settings in VirtualBox and activate the 3D Acceleration. 

Then start your VM. You need the guest additions (you already have these). 
Then in your ubuntu guest, go to the menu system->settings->appearance->visual effects. Activate the effects and close and restart docky.
See screenshot.
[[IMG]http://img685.imageshack.us/img685/4804/compizinsidevirtualbox.th.jpg[/IMG]](http://img685.imageshack.us/img685/4804/compizinsidevirtualbox.jpg)

It's not the fastest, but for testing its great.

Excellent, thank you both. Got Docky working and it seems to use a more straight forward setup than glx-dock did. Anyway, works well! I'll be back for more help I'm sure, as I learn more and more what I am doing. :)

---

### Post by unntrlaffinity on 2010-05-04
You can also use Metacity's compositing, which I've found to be a little less demanding of system resources than Compiz.  The easiest way is to install Ubuntu Tweak and check the box that says Metacity compositing.  Then you can turn off Compiz and all the other eye candy if you want things to be a bit more zippy.  The more difficult way is via the command line:

gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true

That's a double dash before "type".

And to turn it off:

gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool false

I personally prefer Docky and Gnome-Do as a one-two OS management punch, but I've recently tried to simplify my desktop by having one hidden bottom panel for switching windows if I don't want to alt-tab, and a hidden top panel for navigating the OS when I can't remember the Gnome-Do way to perform a task.

---

### Post by Cerin on 2010-12-11
> **unntrlaffinity said:**
> You can also use Metacity's compositing...

Absolutely brilliant. I have an ancient piece-of-crap ATI card that Compiz has never supported very well, so I had no hope of getting compositing working that way. But switching that flag solved the problem. Thanks.

---

