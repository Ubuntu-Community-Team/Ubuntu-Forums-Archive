---
title: "Limewire or Equivelent?"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-12-02
Is there something like limewire or frostwire for ubuntu?  Any recommendations?

---

### Post by deep.tinker77 on 2007-12-02
You can find instructions on installing Frostwire at the following link. Good luck and i hope this helps.

[http://ubuntuforums.org/showthread.php?t=305337&highlight=frostwire](http://ubuntuforums.org/showthread.php?t=305337&highlight=frostwire)

---

### Post by Mze on 2007-12-02
Google is your friend...
[URL="http://www.google.ca/search?hl=en&q=frostwire&btnG=Search&meta="]
Frostwire[/URL]

---

### Post by prodigalson666 on 2007-12-02
Go to limewire web site they have a deb package for ubuntu.

---

### Post by jordank on 2007-12-02
haha, okay, in the case.
which is "better"
Frostwire or limewire?

---

### Post by gn2 on 2007-12-02
> **jordank said:**
> haha, okay, in the case.
which is "better"
Frostwire or limewire?

Frostwire.

---

### Post by MrFSL on 2007-12-02
> **gn2 said:**
> Frostwire.

agreed... please don't support the spyware infested limewire.

---

### Post by jordank on 2007-12-02
i tried downloading frostwire, and i got the tar.gz file.  Where do i extract this, and how do i set it up and everything once i get it? 
Bah what do i do with this thing?

---

### Post by atomkarinca on 2007-12-02
With Limewire you get popup messages something about getting the pro version on startup whereas Frostwire is free. But with Frostwire you can have problems typing, this is a bug and there's a workthrough for that: when you can't type in the search box, just go to the Community Chat tab and just type something then get back to the search box and voila.

---

### Post by atomkarinca on 2007-12-02
> **jordank said:**
> i tried downloading frostwire, and i got the tar.gz file.  Where do i extract this, and how do i set it up and everything once i get it? 
Bah what do i do with this thing?

You don't need to download the tar.gz package, just download [this]("http://www.frostwire.com/download/?os=ubuntu") and double-click it, it should also install the dependencies.

---

### Post by BigFoofieMan on 2007-12-02
You may also want to check out Bittorrent if you dont know about it.
I like it because i can get ISO's of linux very easy.

---

### Post by volkswagner on 2007-12-02
Can not access download.  The link provided in above post and when on frostwire both return a 404 error.  The only download link that works for me is the windows button.

Can anyone else confirm.  Is this a browser problem on my end. New install xubuntu, I did add the java via synaptic, anything else I need.

---

### Post by MrFSL on 2007-12-02
No it seems like this is an issue with their site.

Be patient I am sure it will be fixed.

---

### Post by jordank on 2007-12-03
does anyone know how to get this working for 64 bit ubuntu? It doesn't seem to want to install.

---

### Post by sethvath on 2007-12-03
It works on amd64. Save the deb to desktop and issue the following commands in terminal

cd ~/Desktop
sudo dpkg --force-architecture *.deb

---

### Post by jordank on 2007-12-03
jordan@Jorcomp:~$ cd ~/Desktop
jordan@Jorcomp:~/Desktop$ sudo dpkg --force architecture *.deb
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
jordan@Jorcomp:~/Desktop$

---

### Post by moondoggy17 on 2007-12-03
> **jordank said:**
> haha, okay, in the case.
which is "better"
Frostwire or limewire?

limewire and frostwire are the same thing. frostwire was made for use as a limewire backup in case the people that started limewire get into any legal issues with copyright infringement.

---

### Post by gn2 on 2007-12-03
> **moondoggy17 said:**
> limewire and frostwire are the same thing. 

Frostwire = Limewire Pro. All the extra functions are available for free.

---

### Post by moondoggy17 on 2007-12-03
> **gn2 said:**
> Frostwire = Limewire Pro. All the extra functions are available for free.

limewire pro is free too
just download it using basic, and if you have common sense  you will scan all programs before you use them

---

### Post by xtrm_redbull on 2007-12-03
Try this site [http://sourceforge.net/project/showfiles.php?group_id=142481](http://sourceforge.net/project/showfiles.php?group_id=142481) 
its the first file frostwire-4.13.3.i586.deb :)

---

### Post by subs on 2007-12-03
> **moondoggy17 said:**
> limewire pro is free too
just download it using basic, and if you have common sense  you will scan all programs before you use them

limewire does have some spyware worries.... frostwire on the other hand is a much more cleaner prospect:guitar::guitar:

---

### Post by sethvath on 2007-12-03
> **jordank said:**
> jordan@Jorcomp:~$ cd ~/Desktop
jordan@Jorcomp:~/Desktop$ sudo dpkg --force architecture *.deb
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
jordan@Jorcomp:~/Desktop$

I left out the -i (install) option
sudo dpkg -i --force architecture *.deb

---

### Post by Sarteck on 2007-12-03
Personally, I'd reccomend BitTorrent over anywire.  Heh.  You might want to check out the BitTorrent client that comes with your distro, or download Azureus.

BitTorrent is much more widely in use, I believe, and thus things are easier to find on the 'Net.

---

### Post by aonegodman on 2008-01-02
Well as a former Limewire Pro user under Windows I can tell you that I just D/L'd

frostwire-4.13.4.i586.deb  -  couldn't find a  i386.

Double-clicked on deb and Package Manager installed it flawlessly.

First run setup. Came up like a champ and took about 5 sec to go full turbo mode. Limewire under Windows would take up to 5 minutes or more sometimes on very same connection.

This is, in my opinion, an exact clone of Limewire Pro in a new and improved wrapper but MUCH FASTER under Ubuntu Linux.

Did a search for a couple tunes - Bam!

Clicked on Launch button and player and sound worked perfect.

Very happy with this P2P - Try it!  \\:D/

---

