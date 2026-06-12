---
title: "replacement for kazaa?"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by JohnJSal on 2006-08-17
Hi all. Can anyone recommend a good replacement for Kazaa? Does Linux support P2P programs?

Thanks.

---

### Post by Munchkinguy on 2006-08-17
There's a program that connects to the eDonkey2000 Network. It's called *amule*. Make sure you have the "universe" repository enabled, then:

sudo apt-get install amule

---

### Post by Donnut on 2006-08-17
Limewire is also a good P2P program.  Install Java first.  Frostwire is another one...

---

### Post by h2gofast on 2006-08-17
azureus is worth a try if you can get java installed, try automatix for that.  Some folks complain about java apps in Linux, but azureus just handles stuff easily.  It's a bittorent app which is the way to go for p2p,  my two cents.
cheers

---

### Post by JohnJSal on 2006-08-17
I tried searching for Limewire but nothing came up. I have Azureus already, but I'm looking for something I can use to search for files as well. Azureus can't do that, right?

Edit: Well, amule won't work because it requires removal of a dependency for Python, which I need.

---

### Post by peadenm on 2006-08-18
you can get limewire from [www.download.com](www.download.com)

---

### Post by JohnJSal on 2006-08-18
> **peadenm said:**
> you can get limewire from [www.download.com](www.download.com)

Ok, I got the rpm installed, but when I try to run it nothing happens. When I run it from the terminal I get error messages about not having the JRE, so I installed JRE 5.0, but I still get error messages about not finding the proper Java files.

P.S. How do I uninstall an rpm program?

---

### Post by DSn0wMan on 2006-08-18
type:

java -version

at the prompt and you can tell what version of java you are using.

Edit: There is some dpkg command to switch the java version that you are using, but I forget exactly what it is.

---

### Post by DSn0wMan on 2006-08-18
Here is the command to switch java versions
```

update-alternatives --config java

```

---

### Post by JohnJSal on 2006-08-18
Hmmm, my version is 1.4.2 and the error messages I'm getting say to install a version 1.4.x, so I don't know why it doesn't work.

---

### Post by DSn0wMan on 2006-08-18
> **JohnJSal said:**
> Hmmm, my version is 1.4.2 and the error messages I'm getting say to install a version 1.4.x, so I don't know why it doesn't work.

If it is the blackdown version 1.4.x or something you need to select a different java version using the command I listed above.

blackdown is the pre-installed version, and doesnot work with alot of things.

Make sure you select a sun version. If you installed JRE 5.0 it should work.

---

### Post by omns on 2006-08-18
.

---

### Post by anaconda on 2006-08-18
> **JohnJSal said:**
> I have Azureus already, but I'm looking for something I can use to search for files as well. Azureus can't do that, right?


Yes, azureus can't search, BUT you can easily search torrents from torrent-pages.. eg.
[www.isohunt.com](www.isohunt.com)
[www.piratebay.org](www.piratebay.org)
[www.mininova.org](www.mininova.org)

just to mention few...

---

### Post by Freakenstein on 2006-08-18
> **JohnJSal said:**
> Ok, I got the rpm installed, but when I try to run it nothing happens. When I run it from the terminal I get error messages about not having the JRE, so I installed JRE 5.0, but I still get error messages about not finding the proper Java files.

P.S. How do I uninstall an rpm program?
If you installed the RPM via Alien, you can use **alien -e packagename**.

---

### Post by Snakehit on 2006-08-18
You can download Automatix [www.getautomatix.com](www.getautomatix.com) ,

Automatix is a tool that installs for you the applications you want.
So you can just check Frostwire, Amule, Linux DC++ on and the progam will install it for you. Very easy...

---

### Post by Marsolin on 2006-08-18
Here is a list of some to try: [http://linuxappfinder.com/internetandnetworking/filesharing](http://linuxappfinder.com/internetandnetworking/filesharing)

KMLDonkey, xMule, Gtk-Gnutella, and Apollon are among the options in the Ubuntu repositories.

Thanks to manika for the FrostWire link. I'll have to add that one.

---

### Post by JohnJSal on 2006-08-18
Thanks guys. Frostwire seems to be a pretty good choice, so I'll give that one a try.

---

### Post by Marsolin on 2006-08-18
Here is a list of some to try: [http://linuxappfinder.com/internetandnetworking/filesharing](http://linuxappfinder.com/internetandnetworking/filesharing)

KMLDonkey, xMule, Gtk-Gnutella, and Apollon are among the options in the Ubuntu repositories.

Thanks to manika for the FrostWire link. I'll have to add that one.

---

### Post by JohnJSal on 2006-08-19
Eh, Frostwire still gives me the Java trouble I had with Limewire.

---

### Post by David Corrales on 2006-08-19
Install the sun java (available now from the repositories) and frostwire. Don't forget to update your alternatives before starting frostwire :)

---

### Post by dasunst3r on 2006-08-19
I like the Gnutella and BitTorrent protocols.  In any case, here's the obligatiory "please respect intellectual property and buy your music, movies, software, etc." message.  Seriously.  We'd hate to see you fall victim to those stupid lawsuits.  If something is good to the point that it is worth using or keeping for the forseeable future, it is worth buying to encourage future development on the makers' part.

---

