---
title: "Any ideas how or where do i get this?"
date: 2009-04-25
forum: Art &amp; Design
---

### Post by lechip on 2009-04-25
Ok, this is my first psot here, im not that new to ubunto, actually been using the system a year or so, and ive got everything pretty much personalized.
Recently i was editing a blog entry for my college and i found this screenshot:
[http://gadgetsutra.files.wordpress.com/2009/03/u904b.jpg](http://gadgetsutra.files.wordpress.com/2009/03/u904b.jpg)
I wonder if any of you guys knows where i can get my desktop to look that way, searched a little while on gnome looks and another couple pages but couldnt find anything like that.
Tnx a lot for any help.
Cheers.

---

### Post by U-Bom-2 on 2009-04-25
Hey! well for the transparent theme you can download [This one from gnome-look]("http://www.gnome-look.org/content/show.php/Radial-Light-Clean-Transparent-Glassy?content=102974"), is preaty similar to the one of the screenshot.

To use it you need Beryl Emerald that probably you dont have. So to download and install is just go to your terminal and write:
```
sudo apt-get install emerald
```

After that you can go to System > Preferences > Emerald Theme Manager where you can select the file of the theme and use it.

PS: Before use it you need to activate emerald pressing ALT+F2 and writing:
```
emerald --replace
```

I dont know yet how to auto-run emerald in each session but each time you start you computer you need to start emerald with the emerald --replace

You can see the full thread that help me out [Here]("http://ubuntuforums.org/showthread.php?p=7108605#post7108605")

---

### Post by rushmobius on 2009-04-25
That is actually just a mock-up of WillWill's Intrepid screens if I recall.

I know that a few of the items including a GDM and Gtk theme were done, though the results aren't quite the same as the mockup.

This page has links to the GDM and Gtk themes.
[http://willwill100.deviantart.com/art/Interpid-Ibex-Mockup-Part-2-93584910]("http://willwill100.deviantart.com/art/Interpid-Ibex-Mockup-Part-2-93584910")

---

### Post by markitoxs on 2009-04-26
YEah, it's a mockup, the msot you can achieve is the emerald replacement and a dock like cairo or awn

---

### Post by D-Dan on 2009-04-26
> **U-Bom-2 said:**
> 

I dont know yet how to auto-run emerald in each session but each time you start you computer you need to start emerald with the emerald --replace


Go to compiz-settings-manager (install from the repository if you don't have it). Fire it up and double click the Window Decoration option. In the window decorator, replace what's there with emerald --replace.

Job done.

Steve

---

### Post by U-Bom-2 on 2009-04-26
Yeah, i get it late, also you can do it by going to System > Preferences > Startup Applications click Add and in command write emerald --replace, this worked for me :)

---

