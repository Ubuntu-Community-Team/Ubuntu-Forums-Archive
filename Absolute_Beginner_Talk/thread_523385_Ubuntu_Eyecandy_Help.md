---
title: "Ubuntu Eyecandy Help"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-08-11
I'd like to install some eye candy on Ubuntu.....
Now since I am running Ubuntu in Virtual Box I serious doubt
that Beryl is an option. I've seen people have Clear Desktop
bars that look like glass and very nice looking desktop icons
with a nice background..... How hard is something like this
to install and where can I get these type of desktops.... 
Is this something that won't be to hard to do?

Just would like to get rid of the old blan desktop
I like the Linux ride so far.  Very stable......

Something like this would be nice

[IMG]http://img137.imageshack.us/img137/9913/1desktop20070724brg7.jpg[/IMG]

Thanks

---

### Post by p_quarles on 2007-08-11
"Clear desktop bars" could mean a couple things. If you mean the panels, you can easily make those semi-transparent. Just right-click on an empty portion of the panel you want to change. Select "properties," then click on the "background" tab. Select "solid color" for background, and then you will get a slider which allows you to set the transparency/opacity of the panel. 

There's also a nice desktop theme for Gnome which gives you semi-transparent bars on your application windows. It's called SphereCrystal. To get it, you will need to install the following:
```
sudo apt-get install gnome-themes-extras
```

To use non-standard icons, you just need to create a new desktop launcher. Right-click on the desktop, select "create launcher," and then click the button that says "no icon." There are a number of default options, but you can browse for any appropriate image that's on your system.

---

### Post by Orbital75 on 2007-08-11
Yeah, the Glass or Crystal like Transparent desktop bars is what I'm looking for....

Not sure if your familiar with mac ( os X ) but would Linux have anything that rotates
the icons on the desktop panel as you touch them?

---

### Post by p_quarles on 2007-08-11
> Not sure if your familiar with mac ( os X ) but would Linux have anything that rotates the icons on the desktop panel as you touch them?
That sounds like something that could probably be done with Compiz-Fusion, but I don't use that (and won't, until it's stable), but aside from that I don't think there's anything like that.

---

### Post by Orbital75 on 2007-08-11
p_quarles, 
   thanks for your help. I agree I don't want anything that's not stable.
I've heard that they may have Compiz-Fusion ready for the next release
of Ubuntu.

I changed the desktop bars like you suggested, it looks really nice.
Thanks, I didn't know you could do.  

Ah, is there a safe linux site where you can download more desktop themes.
I used apt-get to grab the Gnome extras and there ok but would like something
a tad bit flasher.  I love apt-get, very easy to use.

---

### Post by fickendichdu on 2007-08-11
[Gnome look]("http://www.gnome-look.org/")  They have quite a few here to look at.

---

### Post by p_quarles on 2007-08-11
[http://www.gnome-look.org/](http://www.gnome-look.org/)

^^^beat me to it :)

---

### Post by Orbital75 on 2007-08-11
fickendichdu,
That site seems to be what I'm after.
Now, I'm using what ever Ubuntu comes with
so I'm not really sure what I need.  I know I 
can't use Beryl ( I'm using a VM ) so do I 
look at Meta City or GDM themes?
does GDM mean Gnome?

---

### Post by p_quarles on 2007-08-11
Metacity is the window manager that comes with Gnome, so yes, look for themes that work with that.

---

### Post by fickendichdu on 2007-08-11
If you are looking for dock software check this post out.
[http://www.kiba-dock.org/]("http://www.kiba-dock.org/")

---

### Post by Zylar on 2007-08-12
GDM themes will change your login screen theme, fyi.

---

### Post by Orbital75 on 2007-08-12
> **Zylar said:**
> GDM themes will change your login screen theme, fyi.

Ah...... that's neat.  I'm learning that Linux is so much more customizable than Windows.
I remember something called ThemeXP that would do the same but of course it was
a third party app that wasn't free.

Well, since I am using a Virtual Machine to run Ubuntu 7.04, what would you recommend
for some eye candy?  It's to my under standing that VirtualBox or maybe any
Virtual Machine doesn't support 3D.  In this sense I believe Beryl and Compiz is out.
I'd like something like the photo I posted in my 1st post.  I'm thinking that photo is
running beryl though.  Isn't the little Red Diamond icon in the system tray a Beryl
program?

---

