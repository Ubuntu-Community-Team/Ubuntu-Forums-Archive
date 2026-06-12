---
title: "Problems with Totem"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by ifross on 2008-01-29
I've got a strange problem, my Totem movie player seems to be stuck in a strange mode... It is like it is in fullscreen mode but the file menu is at the top and the seeker bar is at the bottom.

The problem is, I cannot get out of this mode. Nothing happens when I click on "exit fullscreen" and the option is grayed out in the menu.

I've tried the metacity --replace fix for the fullscreen bug posted on the forums before but it didn't work. Also I've tried reinstalling totem (and purging it aswell).

I know it will be something trivial but I'm at a complete loss!

I'll upload a screenshot, if that will help...
[ATTACH]58022[/ATTACH]
Thanks

---

### Post by Ex-windows on 2008-01-29
Wow that is too wierd.. Have you tried posting this or similar on the Multimedia and Video Board?
This does not sound like typical Totem problems.
Here is the main page for Totem maybe there is a bug filed already and if not you could post it there.
[http://www.gnome.org/projects/totem/](http://www.gnome.org/projects/totem/)

Sorry I couldn't be more help. 
I'll try a few more searches and if I come up with anything I'll repost.

Quick Edit.
Which Version ubuuntu? 
Are you using gstreamer or xine.
DO you have all the extra codecs etc

---

### Post by ifross on 2008-01-30
Im running totem-gstreamer(i think) on Gutsy, with the following gstreamer packages installed:
gstreamer0.10-alsa
gstreamer0.10-esd
gstreamer0.10-ffmpeg
gstreamer0.10-gnomevfs
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-multiverse
gstreamer0.10-tools
gstreamer0.10-x

---

### Post by Ex-windows on 2008-01-30
It is my understanding that by default totem uses the basic gstreaner(s) and you can add the extra gstreamer packages via synaptic. I never could get totem to work with my dvd's so I went to the xine. I honestly dont know if that will help but you could try it. But you should first make sure your list of gstreamer packages are all on that list your posted so that if it doesn't work you can re install them. I say this cus when i add the xine packages in the command line I notice that it says it is removing the gstreamer package. Also I am taking it that everything worked ok prior to this happening??
This is the code IF you want to try it

sudo apt-get install totem-xine libxine-extracodecs 

AGAIN  I really dont know if this will change anything or not.
 I tried doing some searches the other nitte but I couldn't find anything related to this.
Did you try the Gutsy bug reports page?
Hopefully we can get this solved for you....

Here is main gutsy page
[https://help.ubuntu.com/](https://help.ubuntu.com/)

Here is the Lauchpad link to chweck for bugs and/or list yours

[https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

---

### Post by stchman on 2008-01-30
> **ifross said:**
> I've got a strange problem, my Totem movie player seems to be stuck in a strange mode... It is like it is in fullscreen mode but the file menu is at the top and the seeker bar is at the bottom.

The problem is, I cannot get out of this mode. Nothing happens when I click on "exit fullscreen" and the option is grayed out in the menu.

I've tried the metacity --replace fix for the fullscreen bug posted on the forums before but it didn't work. Also I've tried reinstalling totem (and purging it aswell).

I know it will be something trivial but I'm at a complete loss!

I'll upload a screenshot, if that will help...
[ATTACH]58022[/ATTACH]
Thanks

I have never had much luck with Totem.  I prefer to use VLC for my video media.

---

### Post by ifross on 2008-02-04
I've decided to switch to VLC, I find it has many more options... Is it possible to set it as the default app when I double click on video files?

EDIT:
Nvm, quick search told me the answer... Thanks for your help :)

---

### Post by chris86wm on 2008-03-20
i have this same problem. does anyone have a solution?

EDIT: I figured it out. You have to turn off compiz temporarily, then resize totem, and then re-enable compiz.

---

