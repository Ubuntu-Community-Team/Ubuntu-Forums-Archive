---
title: "A neat new way to get themes and backgrounds"
date: 2005-04-15
forum: Art &amp; Design
---

### Post by kassetra on 2005-04-15
[http://www.gnomefiles.org/app.php?soft_id=889](http://www.gnomefiles.org/app.php?soft_id=889)

I have to say that this app is a great idea... people post the themes and artwork, and then it magically appears in a convenient app for you to browse through, download and use at your leisure.

:)

---

### Post by TravisNewman on 2005-04-15
Fantastic!

---

### Post by kiddo on 2005-04-15
[size=7]O_O[/size]

when will we see it in the breezy repositories? :)

---

### Post by bvc on 2005-04-16
what is the advantage of this over your current browser?

---

### Post by kassetra on 2005-04-16
[QUOTE=bvc]what is the advantage of this over your current browser?[/QUOTE]

Well, I can browse them without having to go to the website, they're already there, and you can choose to download or install, and if I choose to install, *poof* it's installed...  It's kind of like synaptic for themes/colors/backgrounds, which I think is cool.

I mean, sure I can go out to websites and download/install .deb files, but synaptic is browsing for something I want... which is why I think it's neat.  :)

---

### Post by rwabel on 2005-04-16
Yeah, that tool ist a must for everyone who is in chaning themes, icons etc
Must come also into hoary!!

---

### Post by kiddo on 2005-04-16
It just came to my mind: uber newbies are often seen asking "how can I change themes?". Knowing that you must create a .themes dir in your home (or something else?) is not newb-proof.

---

### Post by bvc on 2005-04-16
.themes is created the first time the user runs the gnome-theme-manager (or should be)

It is somewhat convenient for a newbie and will be even better when everything can be installed, everthything is cached, filters are added, and a.g.o. gets a database of stuff again.

---

### Post by Spark* on 2005-04-16
[QUOTE=kassetra]Well, I can browse them without having to go to the website, they're already there, and you can choose to download or install, and if I choose to install, *poof* it's installed...  It's kind of like synaptic for themes/colors/backgrounds, which I think is cool.

I mean, sure I can go out to websites and download/install .deb files, but synaptic is browsing for something I want... which is why I think it's neat.  :)[/QUOTE]
What do you mean with "they're already there"? Opening a certain application is not much different from opening a certain website. :) A website usually even has better listing and searching facilities (same thing with email, it's hard to make a client that's better than gmail).
As for "poof it's installed", ever tried dragging a theme from art.gnome.org into your theme manager? :) Many people do not even realize yet just how convenient GNOME theme management is, so often you will see explainations and help that sounds a lot more complicated than it really is.

A tool like this might be very handy and easier to use, just like a native email client. I'm not sure which approach is better, that's something I have been thinking about for a while now. :) It would probably be nice to have applications running on a server but creating native GUIs. I think some of Microsoft's Longhorn stuff is going into this direction.

---

### Post by kassetra on 2005-04-16
[QUOTE=Spark*]What do you mean with "they're already there"? Opening a certain application is not much different from opening a certain website. :) 
As for "poof it's installed", ever tried dragging a theme from art.gnome.org into your theme manager? :) 

A tool like this might be very handy and easier to use, just like a native email client. [/QUOTE]

Well, when you open the app, new themes are dumped in automatically, so you always see the latest - which is not easy sometimes on the websites, plus you just browse through them all at once, without having to go from page to page, waiting for the server, etc. 

Yes, I have tried dragging themes, and yes it works wonderfully. But the difference is this - with this app I just click on the theme I like and click install, it downloads and installs it for me... I don't need to download it, find it on my desktop and then open up theme manager and drag it in there... One step, instead of many... that's all. :)

I'm not saying it's better, all I'm saying is that it's neat and it could be very useful.  :)  I wanted people to know about it, because I thought it would be valuable to some people.  :)

I think if a nice little app like this were included in Ubuntu, it would be a good thing for many users.

---

### Post by st0necol on 2005-04-21
Now gnome-art is already added in Breezy.

update your sources.list to breezy and reload ;)

search for gnome-art and gnome-splashscreen-manager

---

### Post by rwabel on 2005-04-21
I hope it gets backported to hoary :-)
in debian sid it's only version 0.1-2 but on the homepage the latest version is 0.2

---

### Post by mayasp on 2005-04-25
just how do i run this app after installing?
i'm not even sure i installed it correctly, where can i find instruction for begginers?

---

### Post by seven on 2005-04-25
awesome @_O
this should be "out of the box" at breezy.
great app, thanks :)

---

### Post by dude2425 on 2005-05-03
I can't get this thing to work under breezy. It ask's for libglade2-ruby (>=0.12.0) but 0.11.0-1ubuntu1 is to be installed
There is no 0.12.0 in breezy. I try compiling this thing, but it crashes a lot because of libglade2-ruby isn't the right version.

---

### Post by BAshworth on 2005-05-04
Mayasp, just got it working myself.  :D  If you have the repositories listed in the ubuntuguide, here is how to install this.

Go to the gnome-art website, and download the tar file.  Now, download the required packages.

sudo apt-get install ruby
sudo apt-get install ruby-gnome2
sudo apt-get install librexml-ruby

Then go the the folder where you extracted the archive file, and type

sh setup.sh

Make a launcher for the command 'gnome-art' and you're all set.

---

### Post by dude2425 on 2005-05-04
I can't seem to get ruby-gnome2 installed, because it cant install libgda2-ruby because libgda2-1 isnt on the server, although, I got libgda2-3 installed. I still need libglade2-ruby (>=0.12.0) though. I can get into gnome-art, but then certain things crash it with:
/usr/local/lib/site_ruby/1.8/gnome-art/ui/main_window.rb:59:in `on_menu_help_about_activate': uninitialized constant Gtk::AboutDialog (NameError)
        from /usr/lib/ruby/1.8/libglade2.rb:44:in `call'
        from /usr/lib/ruby/1.8/libglade2.rb:44:in `connect'
        from /usr/lib/ruby/1.8/libglade2.rb:44:in `call'
        from /usr/local/lib/site_ruby/1.8/gnome-art/gnome_art.rb:132:in `main'
        from /usr/local/lib/site_ruby/1.8/gnome-art/gnome_art.rb:132:in `main'
        from /usr/bin/gnome-art:25
(this was done by opening the about dialog)

---

