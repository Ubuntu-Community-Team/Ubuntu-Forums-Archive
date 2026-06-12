---
title: "Installing Gnome Themes"
date: 2006-09-21
forum: Art &amp; Design
---

### Post by buzlink on 2006-09-21
How do I go about installing Gnome Themes?
I downloaded, [Alphacube Metacity]("http://www.gnome-look.org/content/show.php?content=29791") and used Theme Preferences under System menu to install the themes that I had extracted to my desktop.  The theme is not appearing the list of available themes.
Did I download the incorrect theme file?
What should I be using, and what else can I change other then my Gnome themes?
Thanks!

---

### Post by bvc on 2006-09-21
you can't use the theme manager once you have extracted the pkg. The theme manager only except compressed archives with one theme in each archive. An archive with multiple theme must be extracted to .themes. Either make each of them tar.gz's and use the theme manager, manually put them in .themes, are re-extract the archives individual themes into .themes

---

### Post by buzlink on 2006-09-22
> **bvc said:**
> you can't use the theme manager once you have extracted the pkg. The theme manager only except compressed archives with one theme in each archive. An archive with multiple theme must be extracted to .themes. Either make each of them tar.gz's and use the theme manager, manually put them in .themes, are re-extract the archives individual themes into .themes
I've tried this a few times with no luck.
Not sure what I"m missing.  Are there any websites with detailed instructions how to do so in Ubunutu?

Thanks

---

### Post by bvc on 2006-09-23
[http://art.gnome.org/faq.php](http://art.gnome.org/faq.php)

I redownloaded the package. Each theme is already an archive, so you should just drag and drop each archive to the theme manager. I do not use this method and haven't for years. It used to be very buggy and it is now just a habbit for me to extract them to .themes with file-roller.

---

### Post by buzlink on 2006-09-23
Is the dir, /usr/shared/themes or /usr/shared/.themes ? (not on my Ubuntu system, so I'm not sure if those are exact.)

Should I be using GTK, Metacity or both?

Thanks

---

### Post by bvc on 2006-09-24
/usr/shared/themes

gtk is the application buttons etc.... (Controls)
metacity is just the window border (Window Border)

so you use both

icons are installed in .icons or /usr/share/icons

---

### Post by unfknblvbl on 2006-09-25
When i first installed a theme it didn't show up, until i realised that you needed to change theme settings, and then you can select it in theme settings. What this does is customize your currently selected theme to change window outline,icon and application styles.
Once you have modified, your theme will be set to custom or modified or something like that.

---

### Post by JGuru on 2006-09-30
Install the package **gnome-art**.

$ **sudo apt-get install gnome-art**

 Load GnomeArt application & choose application icons, Window borders etc.,
 It will automatically download all the Themes available. What's more,
 you can preview a theme, install it if you like!!
 It's so easy!!!

---

### Post by chirayu on 2006-10-16
Nice its exactly what I have been looking for. I am a new linux desktop user never had to work with gnome but I am starting to like it.

---

### Post by ShadowVlican on 2006-10-27
> **JGuru said:**
> Install the package **gnome-art**.

$ **sudo apt-get install gnome-art**

 Load GnomeArt application & choose application icons, Window borders etc.,
 It will automatically download all the Themes available. What's more,
 you can preview a theme, install it if you like!!
 It's so easy!!!
ok... so from my default ubuntu 6.06 installation, i added all the repositories in that package manager thing

found gnome-art.... installed it along with whatever the package manager needed

so far so good... so i run the GNOME ART program from system>preferences>art manager

then art>desktop themes>windows border

it starts to load a whole bunch of borders... that's good...

now when i try to install one... it just brings me to the "theme preferences" that comes with ubuntu, and i can't find the one i wanted to install...

as you can tell... i'm a linux noob ](*,) 
even after reading the gnome-art faq, i still have no idea what the difference between theme engines, Window Border themes, and Application themes...... 

cuz in windows, a visual style is a visual style... once your UXTheme is patched, you can double-click a visual style to use it ](*,)

---

### Post by ShadowVlican on 2006-10-27
nvm... i found out some unexpected as usual

turns out the gnome-art program DOES install those "windows border" and "application" crap, but it's not actually a whole THEME, so i had to click "theme details" to get to those

i'm gonna look around [http://www.gnome-look.org/](http://www.gnome-look.org/) for some FULL THEMES

---

### Post by elcasey on 2006-10-28
As near as I can tell the Gnome Art Manager is a "no longer supported" project. It doesn't show up in Synaptic for me, nor does the "apt-get install gnome-art" work. I get an "E: Couldn't find gnome-art package" error.

Does anyone else know how to install this? Am I doing something wrong?

Help is much appreciated. :-k

---

### Post by ShadowVlican on 2006-10-28
i had to enable all the repositories to find it, but it's there (well at least in 6.06)

---

### Post by IbeeX on 2006-10-29
Funny I was always thinking that theme should be combination off widow borders wallpaper icons gdm and so on preferably splash screen log off, engine ... but no in gnome you need to download every thing separately,

It would be very nice if i Ubuntu you can get application to change complete look starting from splash and so on preferably even plug ins so that you can also change individual applications.!

---

### Post by syrleb on 2006-11-29
hmmmmm, windows seems to be alot better in the theme department, its a ballbreaker on ubuntu

---

### Post by SaintDanBert on 2009-12-11
> **bvc said:**
> 
[http://art.gnome.org/faq.php](http://art.gnome.org/faq.php)

I redownloaded the package. Each theme is already an archive, so you should just drag and drop each archive to the theme manager. I do not use this method and haven't for years. It used to be very buggy and it is now just a habbit for me to extract them to .themes with file-roller.

I download several "mumble.tar.gz" files from the gnome-look site.
Using System->Preferences->Appearance, I select [Install...] to choose
a theme. Every time I get a "theme error" dialog.  I find it hard to believe that all of them are corrupted tar-balls. What can you suggest?

Also, since you obviously know a lot about themes, can you recommend a good HOWTO about making my own themes. I'm no artist and simply want to play with some of the graphics tools.

~~~ 0;-Dan

---

### Post by Exodist on 2009-12-11
> **SaintDanBert said:**
> I download several "mumble.tar.gz" files from the gnome-look site.
Using System->Preferences->Appearance, I select [Install...] to choose
a theme. Every time I get a "theme error" dialog.  I find it hard to believe that all of them are corrupted tar-balls. What can you suggest?

Also, since you obviously know a lot about themes, can you recommend a good HOWTO about making my own themes. I'm no artist and simply want to play with some of the graphics tools.

~~~ 0;-Dan

On the theme selection page try to drag and drop them on. It normally auto installs them for you. 

I will admit though, some of the more complex ones have multiple tarballs located in the file. IMHO they are piss poor put together. [Gnome Legacy]("http://www.gnome-look.org/content/show.php/Gnome+Legacy?content=115142") is my most recent, try it as a base trial to make sure nothing is wrong on your end.

---

### Post by kepps03 on 2010-07-19
gnome-art does not work for me. It says "error extracting" when I try to install via appearance properties--->themes. If I try to install via gnome0art, it does not show up under themes. I'm a total linux noob, so now what??

---

