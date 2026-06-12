---
title: "gdesklets"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by veritas366 on 2006-01-28
I have several problems and I don't have much luck in other forums so maybe someone here can help.  I'll post each one separately.

First, gdesklets.  I had the cpu monitor and various other monitors working under hoary.  under breezy, you can see the percentages, but the visual output, the line under the percentage, stays at 100%...it doesn't move.  

Many other gdesklets don't work at all.  I don't know what else to add, so if someone could direct me to what other information might be helpful, I'd appreciate it.

---

### Post by skirkpatrick on 2006-01-28
Ever since Breezy, any desklet with a "progress" bar in it has had problems, they all show 100%.  It's not a problem with the desklet but with gdesklets.  There's been a couple of threads in the forums about this but nobody has come up with a solution yet.

As far as non-working desklets go, I remember seeing a message on the gdesklets site that some of the older desklets won't work with the new application.

---

### Post by hen3rz on 2006-01-29
> Ever since Breezy, any desklet with a "progress" bar in it has had problems, they all show 100%. It's not a problem with the desklet but with gdesklets. There's been a couple of threads in the forums about this but nobody has come up with a solution yet.

Strange as all my desklets work perfectly. Currently im using FTB-cpu-plot 0.3.2 and both the graph and cpu percentage works fine.

---

### Post by skirkpatrick on 2006-01-29
Are you running gdesklets from the repositories?  I'm using FTB and all the percentage bars show 100%.

---

### Post by tim15856 on 2006-01-29
Speaking of gdesklets, how do properly change the city for the weather desklets? Every city I put in doesn't seem to work.

---

### Post by Lightmans on 2006-01-30
Hello my friends, i have the solve...

Please Download the new Python version 2.4.2 [http://www.python.org/ftp/python/2.4.2/Python-2.4.2.tgz]("http://www.python.org/ftp/python/2.4.2/Python-2.4.2.tgz") 2.4.2 at [www.python.org](www.python.org).
unpack,compile and install it with

tar -xf Python-2.4.2.tgz
cd Python-2.4.2
./configure
make
make install

then ...

Please Download the PyGTK version 2.8.4 [http://ftp.gnome.org/pub/GNOME/sources/pygtk/2.8/pygtk-2.8.4.tar.bz2]("http://ftp.gnome.org/pub/GNOME/sources/pygtk/2.8/pygtk-2.8.4.tar.bz2")  at [www.pygtk.org](www.pygtk.org)
unpack,compile and install it.

tar -xf pygtk-2.8.4.tar.bz2
cd pygtk-2.8.4
./configure
make
make install

and then install the last part ...

Please Download the gdesklets version 0.35.3 at [www.gdesklets.org](www.gdesklets.org)
[http://gdesklets.org//downloads/gDesklets-0.35.3.tar.bz2]("http://gdesklets.org//downloads/gDesklets-0.35.3.tar.bz2")

unpack,compile and install it.
tar -xf gDesklets-0.35.3.tar.bz2
cd gDesklets-0.35.3
./configure
make
make install

ok now start gdesklets and the progressbar will now function ...
Greetings
Lightamns

---

### Post by hen3rz on 2006-01-30
> Are you running gdesklets from the repositories?

Yeah installed through synaptic

---

### Post by Joeb on 2006-01-30
[QUOTE=tim15856]Speaking of gdesklets, how do properly change the city for the weather desklets? Every city I put in doesn't seem to work.[/QUOTE]

If you are in the US, try putting in a zip code and see if that works (it will depend on which weather desklet you are using, however).

---

### Post by skirkpatrick on 2006-01-30
I've reinstalled (from the repositories) python v2.4.2, pygtk v2.8.1, and gdesklets v0.35.2 and still no joy.  After fiddling around with Thunderbird and Firefox builds versus repositories, I really hate to build something that's also in the repositories.  Nothing ever seems to install the same way.

If you use iWeather, use your ZIP code.

---

### Post by veritas366 on 2006-01-30
> 
Please Download the gdesklets version 0.35.3 at [www.gdesklets.org](www.gdesklets.org)
[http://gdesklets.org//downloads/gDesklets-0.35.3.tar.bz2]("http://gdesklets.org//downloads/gDesklets-0.35.3.tar.bz2")

unpack,compile and install it.
tar -xf gDesklets-0.35.3.tar.bz2
cd gDesklets-0.35.3
./configure
make
make install

Thanks for the tips.  All went well until I got to the gdesklets itself.  Trying to configure I get:
> checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
 
I used synaptic to download everything with parser, perl and xml in the title...this error message is not very specific.  Any idea which module it wants?

---

### Post by cbudden on 2006-01-30
libxml-parser-perl is the package.  I managed to get it all installed but gDesklets didn't work, it spewed out errors when I tried to run it.  I used checkinstall.

---

### Post by veritas366 on 2006-01-30
Got the above figured out.  The error message was vague but I found the xml parser.

Now I have this:

> checking for GDESKLETS... configure: error: Package requirements (pygtk-2.0 >= 2.4.0 pyorbit-2 >= 2.0.1 gnome-python-2.0 >= 2.6.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

This was AFTER I'd compiled the two packages you linked to.  Any ideas?

---

### Post by Lightmans on 2006-02-01
Hello,

Ok try first this in the shell:

# sudo apt-get build-dep gdesklets 

Are you sure that you Download and install the new Python Version and the pyGTK?

After the shell command and the installationof Python and the pyGTK try to compile and install the new gdesklets version.

greets,
lightmans

---

### Post by kewl1uk on 2006-02-01
[QUOTE=tim15856]Speaking of gdesklets, how do properly change the city for the weather desklets? Every city I put in doesn't seem to work.[/QUOTE]

As already said the zip code works for U.S. cities. Otherwise [http://www.aspnetresources.com/tools/locid.aspx](http://www.aspnetresources.com/tools/locid.aspx) entering the location as city, country

---

