---
title: "Can I get some help in theme creation"
date: 2006-05-18
forum: Art &amp; Design
---

### Post by indraveni on 2006-05-18
Hello,

 I am a newbie to this forum.. I want to learn how we can create our own theme and make it  a default theme when we install our CD. Actually we are working for one of the distribution which is debian based. Alll the pacakges used are debian pacakges. 
 I have seen that Ubuntu is also using debian packages. So there is a theme called Human in Ubuntu which is the default theme. 

 Can any one tell me how I  can create a theme and make it the default theme for my OS please.... 

 I am in a very urgent need of it. 

Help Please

Regards
KIV

---

### Post by viciouslime on 2006-05-18
I am also interested in how to make my own themes for GNOME but I can't find a guide anywhere and don't know where to begin. Anyone know of one...?

---

### Post by indraveni on 2006-05-18
Hi,

 Not sure but you can find out a good tutorial for creating a gnome theme in the following link

 [http://live.gnome.org/GnomeArt/Tutorials](http://live.gnome.org/GnomeArt/Tutorials)

 But I want to know how to make it default

---

### Post by bvc on 2006-05-18
[http://benjamin.sipsolutions.net/GTK-Themeing](http://benjamin.sipsolutions.net/GTK-Themeing)

if you really want to dig into pixmap themes, check the eXperience engine
[http://kwh.kernow-gb.com/~bvc/wp/?p=18](http://kwh.kernow-gb.com/~bvc/wp/?p=18)

Don't know if this will give you any hints
[http://mandrivausers.org/index.php?showtopic=10855&hl=](http://mandrivausers.org/index.php?showtopic=10855&hl=)

and /usr/share/gconf/default.path says
> ######################
# 1. Forced settings #
######################

# Settings forced by the local administrator
xml:readonly:/etc/gconf/gconf.xml.mandatory

# Other forced sources imagined by the local administrator
include /etc/gconf/2/local-mandatory.path


#######################
# 2. User Preferences #
#######################

# Sabayon mandatory path
include "$(HOME)/.gconf.path.mandatory"

# Other sources imagined by the user
include "$(HOME)/.gconf.path"

# The default storage location, ~/.gconf
# This should be the only readwrite source
xml:readwrite:$(HOME)/.gconf

# Sabayon optional path
include "$(HOME)/.gconf.path.defaults"


######################
# 3. System defaults #
######################

# Other default sources imagined by the local administrator
include /etc/gconf/2/local-defaults.path

# System administrator's defaults. This source also serves as a legacy
# source for packages not using a recent dh_gconf, or for applications
# installed by hand.
xml:readonly:/etc/gconf/gconf.xml.defaults

# Debian branding, including CDD or packaged branding
xml:readonly:/var/lib/gconf/debian.defaults

# Upstream application defaults
xml:readonly:/var/lib/gconf/defaults


---

### Post by bvc on 2006-05-19
**_d3a comparison_** using [gtkperf]("http://gtkperf.sourceforge.net/index.php?page=main")
d3a-eXperience (experience) 16.47
eXperience (experience) 27.41
d3a (pixbuf) 28.56

---

### Post by PingunZ on 2006-05-20
You can join [Ubuntu Art ]("http://https://wiki.ubuntu.com/ArtworkTeam?action=show&redirect=ArtTeam")

[And here are some good howto's for artwork ;)]("http://http://live.gnome.org/GnomeArt_2fTutorials")

Grtz PingunZ

---

### Post by ComplexNumber on 2006-05-20
> **PingunZ]You can join [Ubuntu Art ]("http://https://wiki.ubuntu.com/ArtworkTeam?action=show&redirect=ArtTeam")

[URL="http://http://live.gnome.org/GnomeArt_2fTutorials"]And here are some good howto's for artwork  said:**
> 

Grtz PingunZ why does your link send me to microsofts home page? :confused:. thats the last place that i want to visit.

EDIT. i know why. its because you have put "http" in twice so that it looks like this:
[http://http//live.gnome.org/GnomeArt_2fTutorials]("http://http//live.gnome.org/GnomeArt_2fTutorials")
what you've done is that you've appended the absolute path to that site to the "http:" thats already written in the text box when you click on the 'Insert Link' button.

besides, the correct link to that site has already been given in post 3 of this thread :)

---

### Post by userundefine on 2006-05-20
But still... why does that go to Microsoft?  Really bizarre.  Anyway, thanks for the link.

---

### Post by bvc on 2006-05-21
concerning making a theme default, there might be something here
[http://live.gnome.org/GnomeLiveCd](http://live.gnome.org/GnomeLiveCd)
[http://live.gnome.org/GnomeLiveCd/HowTo](http://live.gnome.org/GnomeLiveCd/HowTo)

---

### Post by viciouslime on 2006-05-21
It goes to microsoft because it just does a google search for http and goes to the first result. Try it, type "http" in the address bar....[oops, isn't address bar it's name in IE? <ducks to avoid multitude of projectiles thrown in my direction by ubuntu users for mentioning IE>] Anyway, it'll go to the m$ site as, for whatever reason, that is the first result when searching for http.

---

### Post by PingunZ on 2006-05-22
WOOOW LOL the link to ubuntu art team is ( not microsoft ;) ) is: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-art](https://lists.ubuntu.com/mailman/listinfo/ubuntu-art)

Grtz PingunZ

---

### Post by indraveni on 2006-06-02
Can I know where ubuntu placed the Human gnome theme i.e in which package and where did they modify the source to make it the default theme for ubuntu after installation. 

 This answer may help me enough..

 Please Help Me..........

---

### Post by PingunZ on 2006-06-02
To see your theme :: System => Preferences => Theme
Location Of your theme :: usr/share/theme
icons :: usr/share/icons 
...
Want something else ??

Grtz PingunZ

---

### Post by indraveni on 2006-06-03
As I already mentioned that we are working for a distro based on debian packages. we are modifying debian pacakges and adding into our distro. So now i want to add our new theme to this distro and make it the default theme after installation.. So for this I want to know which deb package I need to edit and how can I make my theme as default. 

I know that I need to add my new theme in the gnome-themes pacakge but how to make it default theme for our distro I dint understand. 

As Ubuntu is using Human gnome theme as their default theme. I want to know how Ubuntu developers are doing this work so I can also follow the same steps.. In which pacakge they are adding this Human theme and how it is reflected as the default theme as we install Ubuntu.

Help Please

---

### Post by bvc on 2006-06-03
This was answered in the forum section in the last week or two. I think the Search function stinks so I'm not going to try and find the thread, but it is there....somewhere.

---

### Post by Zyphrexi on 2006-06-04
If only making themes was as easy as inkscape... sigh.

I'm surprised no one has made that jump actually... we'd get a lot of high quality artwork. Forgive me if "IT DOESN'T WORK LIKE THAT!"

---

### Post by bvc on 2006-06-04
It is as easy, and I don't think we'd get any more high quality artwork, for that reason. Those that don't want to code can email art to someone that does. E17 does that, or at least offers, but that's because making an E17 theme is insane. Gtk is easy. If someone can make the art, they have enough snap to grab someone elses theme and replace the images with their own. Easy.

---

### Post by Zyphrexi on 2006-06-05
I've taken a look at it, it's confusing to me. I don't think it's that easy. I'd like a gui.

EDIT: also the tutorials don't make sense to me.

---

### Post by bvc on 2006-06-05
you don't need a tutorial to tell you to open a theme, get the button image size, make your button and put it in place of the template theme button, repeat for the rest of the images, have a new theme created by you giving credit to the original code author. It is...that easy ;) 

There's not much in the way of right and wrong code, just missing code and usability functions, so just make sure to use a theme that has the functions you want as a template.

I started with a mac theme port (bbx mercury) and used one of roberto's themes as a template.

It's only hard when you start trying to do what hasn't been done to make a gtk theme better and more useable.

---

### Post by Zyphrexi on 2006-06-05
I had copied the 'human' theme folder from /usr/share/themes to my $HOME/.themes folder and change the name to human-custom so I wouldn't get it confused. I tried altering the color of something, using colorscheme to get the hex value. Unfortunately I'm not sure what most of it means, I suppose I could always by trial and error replace each hex value, but that seems an inefficient way to learn. By the way, I managed to make a package of colorscheme, though it wasn't exactly what I thought it would be. I'm not sure exactly how this works, but I *believe* that there hasn't been a package made yet, and i'd be more than happy to share.

---

### Post by bvc on 2006-06-05
I'm sure there's probably a better way to learn the basics but, really, after a theme or 2 it should kinda click.
fg it foreground test
bg is background
base is beneeth the background?
text is text..entry, docs etc

NORMAL is normal
PRELIGHT is pre....you get it.

Pick another theme than Human. Its config is strange because of the manipulation that needed to be done with the different shades of orange. It's not necessary to be done that way. It cuts down a few lines of code but is harder for someone w/o experience to follow.

I'd love to see your color scheme and I'm sure others would too.

---

### Post by Zyphrexi on 2006-06-06
well it's not my program, I didn't make it, just packaged it, so I don't know if I have to get permission or whatever. Personally i'm not too impressed with the program, it really doesn't help set up colorschemes. I was thinking it might be like kde's colorscheme thingamajiggy, where you could alter the colors and create your own color scheme. If I knew more about programming I'd love to do just that, a theme-making (altering) program for gnome where you could select the color you desire from a color chooser. Most themes are fine the way they are, but a while back I saw an ubuntulooks package that had a variety of colorations, like 10 or so. While that's a very cool package, it doesn't have the (nearly) infinite combinations a program that i'm describing would.
> 
Pick another theme than Human. Its config is strange because of the manipulation that needed to be done with the different shades of orange. It's not necessary to be done that way. It cuts down a few lines of code but is harder for someone w/o experience to follow.


yeah i was wondering about that.

---

