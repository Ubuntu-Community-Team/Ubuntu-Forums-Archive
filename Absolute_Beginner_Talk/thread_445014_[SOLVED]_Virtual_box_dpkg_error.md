---
title: "[SOLVED] Virtual box dpkg error"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-05-15
I've had some trouble with installing virtual box 

it stopped and so has synaptic now 

problems in this thread
[http://ubuntuforums.org/showthread.php?t=444863](http://ubuntuforums.org/showthread.php?t=444863)

followed instr in this thread
[http://ubuntuforums.org/showthread.php?t=442722&highlight=synaptic+error](http://ubuntuforums.org/showthread.php?t=442722&highlight=synaptic+error)

but i get this in the terminal 

kevin@kevin-desktop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate a file for the virtualbox package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
kevin@kevin-desktop:~$ 

which are the errors i get in synaptic - is this going to go round and round?

if i try to open the package i get another error

---

### Post by netwerx on 2007-05-15
have you tried downloading the virtualbox package again? like with 
sudo apt-get install virtualbox 
?

---

### Post by forestpixie on 2007-05-15
yes i did - got 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.

---

### Post by bapoumba on 2007-05-15
[http://www.ubuntugeek.com/package-installation-error-and-solution.html]("http://www.ubuntugeek.com/package-installation-error-and-solution.html")

Please check the comments, there is a procedure for virtualbox.

---

### Post by forestpixie on 2007-05-15
Thanks for reply 

Are you talking about the Brian Burch post - sorry to need reassurance only been here for a week

Can I assume (with some hope) that getting to 6 in that post will have cleaned it out?


If I then leave off virtualbox till i've got a bit more time will I not need to do rest, or do I need to do the "linux-headers-xxx package" bit

if I need to do the last bit how do I know which kernel I'm running?

Think I would like to get to a position where pc is ok without virtualbox and drink a glass of wine

---

### Post by forestpixie on 2007-05-15
Oh hang on i was looking at this thread

[http://ubuntuforums.org/showthread.php?t=413879](http://ubuntuforums.org/showthread.php?t=413879)

post 2 

i tried looking for /etc/init.d/virtualbox and it's not there - nor is it hidden either

---

### Post by lazyart on 2007-05-15
VirtualBox isn't in the respositories.  Download it again from the site and start over again.

---

### Post by forestpixie on 2007-05-15
Hi - tried that after the sudo apt-get thing failed 

and trying to run the new download gave me a could not open error -package might be corrupted or you're not allowed to open :please check permissions

then it closes and i'm back at the beginning again


i still haven't tried the procedure from bapoumba's post as i'm a bit wary about getting past point 6 of that Brian Burch posting in 

[http://www.ubuntugeek.com/package-installation-error-and-solution.html](http://www.ubuntugeek.com/package-installation-error-and-solution.html)

---

### Post by bapoumba on 2007-05-15
Look down the comments, you can first try:
```
sudo dpkg –remove –force-remove-reinstreq virtualbox
```

---

### Post by forestpixie on 2007-05-15
ok did first one and got 
kevin@kevin-desktop:~/Desktop$ sudo dpkg &#8211;remove &#8211;force-depends &#8211;force-remove-reinstreq virtualbox
Password:
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
kevin@kevin-desktop:~/Desktop$

---

### Post by forestpixie on 2007-05-15
I don't have anything in edit /etc/init.d/virtualbox so can't edit it

nor where there any entries in /var/lib/dpkg/info/  before i did sudo dpkg &#8211;remove &#8211;force-depends &#8211;force-remove-reinstreq virtualbox

do i carry on and do sudo dpkg -i VirtualBox_blah.deb -  obviously changing blah

---

### Post by bapoumba on 2007-05-15
dpkg --remove --force-remove-reinstreq virtualbox

My mystake, the -- do not come out right in the "code" area.
Try now, sorry.

---

### Post by forestpixie on 2007-05-15
Woohoo

I can open synaptic now so i guess that bit's ok

has that command cleaned all the virtualbox files and anything it might have done out

is there anything i need to do to tidy up at all - bearing in mind I've arrived from windows and it leaves stuff all over the place!!

---

### Post by forestpixie on 2007-05-15
If that is all I thank you all and have 1 last question

if I was in aposition where I needed to reinstall could I copy xorg.conf to my win part, reinstall ubuntu and then copy file back ?

---

### Post by bapoumba on 2007-05-15
I do not know much about virtualbox. Hope others can answer that question better than me (I just like packages managers ;))

For xorg.conf, I guess if the proper drivers are running.

What I usually do though is:
```
sudo dpkg-reconfigure xserver-xorg
```
Keep the defaults answers when you do not know, and select items with <space> (to choose resolutions for ex).
Then restart X with CTRL-ALT-Backspace.

This procedure has never failed me.

---

### Post by forestpixie on 2007-05-15
I'll bear that in mind then if the need arises and copy the file just in case - getting twinview and colour tv was a bit of a battle 

Thanks very much for your help I really didn't want to start again twice in the same week

):P

---

### Post by bapoumba on 2007-05-15
You are very welcome :)

---

