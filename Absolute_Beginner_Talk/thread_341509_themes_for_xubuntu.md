---
title: "themes for xubuntu"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2007-01-18
hi, does the "GTK 2.x Theme/Style" themes work on ubuntu or only the XFCE?

---

### Post by euler_fan on 2007-01-18
They should work for both. Regular Ubuntu runs the GNOME desktop, and [http://www.gnome-look.org/]("http://www.gnome-look.org/") has an entire section of themes devoted to those build on GTK 2.x. If it doesn't run on yours, I suggest searching for "GTK" in Synaptic (assuming you have it) and grab one of the theme packages whose description includes something about "built using GTK 2.x" or "A GTK 2.x . . ." etc. Install it and synaptic should take care of the dependencies.

However, I don't see why this should be necessary. When I was running Ubuntu 6.06 and 6.10 before switching to Xubuntu, GTK 2.x theme support was part of the default GNOME desktop.

---

### Post by Jorge32 on 2007-01-18
Actually I am on xfce-look.org  and I liked a bar that comes in a "Mac os" like theme, but it is on GTK. The problem is, I am not using GNOME! I use XFCE!  so maybe it was kind of obviuos my question, but still I wanted to know if I can install it. 
Or well is there a way of creating a bar that looks like the one at the bottom on the MAC OS? mainly that is what I am looking for.

---

### Post by Pobega on 2007-01-18
> **Jorge32 said:**
> Actually I am on xfce-look.org  and I liked a bar that comes in a "Mac os" like theme, but it is on GTK. The problem is, I am not using GNOME! I use XFCE!  so maybe it was kind of obviuos my question, but still I wanted to know if I can install it. 
Or well is there a way of creating a bar that looks like the one at the bottom on the MAC OS? mainly that is what I am looking for.

GTK isn't just for Gnome; GTK stands for "Gimp Tool Kit", not "Gnome TK". Xfce actually uses GTK, so you shouldn't worry about GTK Apps.

---

### Post by Jorge32 on 2007-01-18
but talking about a theme, will it support it? look:
Description:
A fast Clearlooks and Ubuntulooks themes for Gnome made to loosely resemble OSX Tiger.
and it is a  GTK 2.x Theme/Style


or there is a way of creating the bar? the rotating- tranpsparent-one?

---

### Post by euler_fan on 2007-01-18
Sorry if I misread your original post.

Taking things in reverse order . . . 

> **Jorge32 said:**
>  . . . or there is a way of creating the bar? the rotating- tranpsparent-one?

I know there are other threads on this. Sorry, not something have ever tried to do to my own so I don't have an exact URL for you. :-k  I do remember it takes manually editing the xorg.conf file.

> **Jorge32 said:**
> but talking about a theme, will it support it? look:
Description:
A fast Clearlooks and Ubuntulooks themes for Gnome made to loosely resemble OSX Tiger.
and it is a  GTK 2.x Theme/Style

I don't think there will be any problems. I have installed a number of themes from gnome-look to my Xubuntu machine without incident. All were for gnome and used GTK 2.x.

---

### Post by Jorge32 on 2007-01-18
ok I've installed it but it isnt working i can't acces to it
does Xubuntu uses a different folder for themes instead of ~/.themes?

---

### Post by euler_fan on 2007-01-18
mine is at  /usr/share/themes

It is write protected so I ususally just untar the theme somewhere convenient and sudo mv file1 /usr/share/themes to get it into the themes folder. Once there Xubuntu recognizes right away for me.

---

### Post by Jorge32 on 2007-01-18
yeah that was it, now i can usue the mac os theme, but. The bar isn't appearing! :S:confused:  so much work for nothing?
I've read t he transparency depends on window manager, if it suports it. So I am destined not to use if because of xfce?

---

### Post by euler_fan on 2007-01-18
Well, I can't speak to your specific desire, but if you want an OSX-style bottom bar, I would suggest the following (so long as transparency isn't a major issue).:-k 

First, move anything you need from the default lower bar to the upper bar.
Then, go to applications ->settings -> settings manager ->Panel
Select whichever the bottom panel is (on mine it is number 2)
Move the pixel width selector until it is as tall as you like it.
Change the width setting from full to normal
Close the settings windows.
Now right click on the bottom bar and start adding launchers to it. I get my commands using the appfinder tool under Accessories.
Delete the Task list, Pager, show desktop, and trash items from this one.
That should be it. Not transparent, but an OS-X style launcher bar. If you want the Active programs to show up, don't delete the task list, just go into its properties menu and change the setting from show application names to do not show application names.

Icons are in the /usr/share/icons folder (at least they are on mine).

That should get you started at least. If someone else has a better suggestion, please share.

And if you want, you can now move anything from the upper bar you want to the lower one and delete the upper one should it prove too un-mac-like.

Hope that all made sense. Good luck getting transparency to work.

---

