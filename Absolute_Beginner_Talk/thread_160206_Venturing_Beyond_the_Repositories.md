---
title: "Venturing Beyond the Repositories"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by Mookawaka on 2006-04-14
I am a newbie in the Linux and Ubuntu world, but very excited about my new experiment.  I have not had this much fun with a computer since playing with my [Commodore 64]("http://www.old-computers.com/museum/computer.asp?c=98").
I have a dual boot set up of Ubuntu Breezy and Windoze XP on a slightly elderly PIII 1.1 Gig Dell Inspiron 4100 portable computer.  I would like to leave the programming nightmare from my hometown that is Microsoft all together, but I am testing an online game developed by a friend and cannot get around the seemingly common problem of Lexmark printer drivers.
I have managed to wrap my brain around apt-get and Synaptic.  Now I am trying to venture into the realm of unsupported applications in the form of .rpm packages and tarballs. 
I am familiar with the [Ubuntu Starter Guide]("http://ubuntuguide.org/").  I have alien and have followed the instructions, but have not been able to get any of the little programs I would like to install, to actually be accessible and work, without a specific walkthrough where I can copy and paste command lines.
So does anyone know of a HOW TO that could give me the hand-holding that I apparantly need, or specific advice on the three versions I have found of downloading a package and installing it manually?
1) [Lexmark Printer Driver]("http://ubuntuforums.org/showthread.php?t=49714") (my specific issues are near the end of the post.)
2) I have tried to install the [xu4]("http://xu4.sourceforge.net/") .rpm package, and am now stuck with some zipped README files about the game and no executable file.
3) With my difficulties so far I have not dared to compile a tarball like that for [Dark Oberon]("http://dark-oberon.sourceforge.net/").

---

### Post by xyz on 2006-04-14
Hi,
I don't get this:

> I would like to install to actually be accessible and work without a specific walkthrough where I can copy and paste command lines
Pretty much the same as Ubuntuguide:
[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

---

### Post by Mookawaka on 2006-04-14
I guess I forgot some commas.
What I was muttering about, is that I have not been able to figure out installing an .rpm or tarball from beginning to end without instructions specific to the package (such as the Lexmark driver, which still did not work due to some other mystery involving printer cartidges.)
Thank you for the updated guide to Breezy.

---

### Post by xyz on 2006-04-14
This link would be of interest to you, I think.
[http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/](http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/)

aahh...Berlin....wunderbar Kunst und mehr...

---

### Post by Axces on 2006-04-14
Well, I could give ya a quick run through of the "usual" case of tar balls.

First you untar it: tar xzvf filename if it is a tgz file, if not, then just tar xvf filename

Then you configure the package: ./configure will usually do the trick, the readme will have any information about weird flags

Now, the program has a good amount of information about your computer, so it needs to figure out how its going to install it: make should do just fine.

And finally, we get to install it:
sudo make install will usually get the job done. 

This is the typical tarball source install, some tarballs of course have weird steps or sometimes you get lucky and you get one in ruby, which is even easier. Again, if it is inconsistent they usually let you know.


As for RPMs, turns out those can sometimes be easier! 
There is a program called alien that converts rpm's to dpkg's(debian packages). To get this type: sudo apt-get install alien

Now, to convert your package type: sudo alien -k name-of-rpm-file.rpm

This will convert the .rpm package right into a dpkg in the same folder, so to install that type: sudo dpkg -i name-of-rpm-file.dpkg

And that should do it.

---

### Post by Axces on 2006-04-14
[QUOTE=Axces]

As for RPMs, turns out those can sometimes be easier! 
There is a program called alien that converts rpm's to dpkg's(debian packages). To get this type: sudo apt-get install alien

Now, to convert your package type: sudo alien -k name-of-rpm-file.rpm

This will convert the .rpm package right into a dpkg in the same folder, so to install that type: sudo dpkg -i name-of-rpm-file.dpkg

And that should do it.[/QUOTE]


The link from xyz might have helped me out here :)

---

### Post by timsch75 on 2006-04-14
untar the tarballs with **tar zxvf _file_** if it is a *.tar.gz file (.tgz is slackware, i believe) or **tar jxvf _file_** if it is a *.tar.bz2 file.  Inside each tarball is usually a README and/or INSTALL text file that will tell you the commands to use to install the program.  Before doing so, look for information on dependencies in those files or on the program homepage.  The process is usually fairly easy, and once you've done a few, you'll see it's no big deal, and liberating as well.

---

### Post by OffHand on 2006-04-14
ubuntuguide is kinda old (for 5.04). this is an updated version (for 5.10):

[http://makuchaku.info/amnesty/#](http://makuchaku.info/amnesty/#)

---

### Post by Axces on 2006-04-14
Slackware with its own tarball extentions? Nahh, its just another extention to gzip files. I've never ran into the j flag though, that is interesting. It is quite liberating :).

---

### Post by timsch75 on 2006-04-16
Axces
    It's true.  *.tgz are slackware packages.  Maybe they work elsewhere as well, I don't know.

---

