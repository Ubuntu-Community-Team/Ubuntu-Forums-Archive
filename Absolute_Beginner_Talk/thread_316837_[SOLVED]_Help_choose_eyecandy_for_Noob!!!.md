---
title: "[SOLVED] Help choose eyecandy for Noob!!!"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by victorbrca on 2006-12-11
Hi all,

  Can anyone help me with inputs in which Composite manager and X server to use?

  I have a dell Inspiron 1300 with 915resolution on a Breezy Badger.

  I don't need anything major as it's for my laptop and I like speed better than looks. I just wanted to add a bit of transparency and make it all look better..
  
  I was deciding for XGL server and Compiz... I'm not sure if beryl is compatible with breezy and if it's better than compiz...

Tanks a lot,


Vic.

---

### Post by Bachstelze on 2006-12-11
I'm personnally perfectly happy with the eyecandy of [my KDE](http://img147.imageshack.us/my.php?image=screenshot2qs0.png) without messing with Compiz/Beryl/whatever.

---

### Post by PriceChild on 2006-12-11
If I were you I would forget any compositing because you're running Breezy.

Everything has advanced just too much. Not even Dapper is supported anymore for the latest Beryl.

I also don't think you should upgrade Breezy if its working for you.

/me strokes his edgy and feisty boxes running beryl.

---

### Post by bulldog on 2006-12-11
Maybe time to upgrade your distro to Dapper or even Edgy.
Beryl will work with both of them.

Have no knowledge about Breezy,so can't help you with that.

---

### Post by 23meg on 2006-12-11
All you can run on Breezy is ancient versions of XGL and Compiz; given how buggy they are and the current state of things, I'd say it's not worth bothering.
> 
I just wanted to add a bit of transparency

For that you can use the composite extension + xcompmgr.

---

### Post by robgill on 2006-12-11
> **PriceChild said:**
> If I were you I would forget any compositing because you're running Breezy.

Everything has advanced just too much. Not even Dapper is supported anymore for the latest Beryl.

I also don't think you should upgrade Breezy if its working for you.

/me strokes his edgy and feisty boxes running beryl.

Well, you can get the most recent version of beryl PACKAGED for dapper here..

[http://forum.ubuntu-it.org/index.php?PHPSESSID=4bd8c6bdb0fc0827aaa4cea601b14910&topic=45451.0](http://forum.ubuntu-it.org/index.php?PHPSESSID=4bd8c6bdb0fc0827aaa4cea601b14910&topic=45451.0)

The page is Italian, but scroll down to the bottom of the first post and you'll see the 3 or 4 most recent svn releases, usually updated everyday.

TO install it, extract only the archive you downlod, navigate to the directory in terminal and type:

```
sudo dpkg -i *.deb
```

And now you have close to if not the most recent beryl for dapper.  I just upgraded to 1662 there today and have beryl 0.1.3 (just released) running flawlessly on dapper with an intel chipset like the first poster.

Sometimes beryl-dev breaks if you don't have all the dependencies, but just remove it after install in Synaptic (you don't need it at all to run beryl).

---

### Post by victorbrca on 2006-12-11
> For that you can use the composite extension + xcompmgr.

So, can I actually get something like this using xcompmgr?

[screenshot]("http://gentoo-wiki.com/images/thumb/1/1d/Transparent4.png/750px-Transparent4.png")



Vic.

---

### Post by 23meg on 2006-12-11
> **victorbrca said:**
> So, can I actually get something like this using xcompmgr?

[screenshot]("http://gentoo-wiki.com/images/thumb/1/1d/Transparent4.png/750px-Transparent4.png")



Vic.Yes, that could be xcompmgr.

---

### Post by mixmaster87 on 2006-12-11
> Well, you can get the most recent version of beryl PACKAGED for dapper here..

[http://forum.ubuntu-it.org/index.php...&topic=45451.0](http://forum.ubuntu-it.org/index.php...&topic=45451.0)

The page is Italian, but scroll down to the bottom...

how do i locate the directory? (downloaded to the desktop) and can i update it without deleting my currently running beryl?

---

### Post by victorbrca on 2006-12-11
> **23meg said:**
> Yes, that could be xcompmgr.

Tried it out with transset, but it slowed down enough for me not to like it...

Thanks for the tips thou...

Vic.

---

### Post by igknighted on 2006-12-11
Out of curiosity, is there a reason you are still running breezy?  The technologies involved in what you are trying to do have come a *very* long way since then.

---

### Post by robgill on 2006-12-11
> **mixmaster87 said:**
> how do i locate the directory? (downloaded to the desktop) and can i update it without deleting my currently running beryl?

Yes, you can do it without removing your current beryl.

If you downloaded to the desktop

```
cd ~/Desktop/beryl-svn-1662mc-dapper
```

assuming "beryl-svn-1662mc-dapper" is the name of the extracted folder

then
```
sudo dpkg -i *.deb
```

then click beryl-manager and reload window manager

---

### Post by victorbrca on 2006-12-11
> **igknighted said:**
> Out of curiosity, is there a reason you are still running breezy?  The technologies involved in what you are trying to do have come a *very* long way since then.

I'm a fresh noob, that's all. I installed Ubuntu from a CD a friend gave me last Tuesday. I'm trying it out first and learning. But I'll update from this version as soon as I feel I'm worthy of it!!!! ;) 

I'm already in love thou!!!!


Vic.

---

### Post by mixmaster87 on 2006-12-11
Edit cause the question was answered way before i saw that the post turned to a new page. sorry:P

new edit:

it didnt work.. i moved the file back to the desktop as i had moved it to try to find it earlier:P, then it didnt find it, so i made a directory there to put it in, it found it but when i tried to install it, it seems like it didnt find it anyway:
> 
mixmaster@prodigy:~$ cd ~/Desktop/beryl-svn-1662mc-dapper
mixmaster@prodigy:~/Desktop/beryl-svn-1662mc-dapper$ sudo dpkg -i *.deb
Password:
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
mixmaster@prodigy:~/Desktop/beryl-svn-1662mc-dapper$
mixmaster@prodigy:~/Desktop/beryl-svn-1662mc-dapper$

---

### Post by igknighted on 2006-12-11
> **mixmaster87 said:**
> Edit cause the question was answered way before i saw that the post turned to a new page. sorry:P

new edit:

it didnt work.. i moved the file back to the desktop as i had moved it to try to find it earlier:P, then it didnt find it, so i made a directory there to put it in, it found it but when i tried to install it, it seems like it didnt find it anyway:

I believe you need to substitute the package name for *.deb

---

### Post by ardvark71 on 2006-12-11
> **igknighted said:**
> Out of curiosity, is there a reason you are still running breezy?  The technologies involved in what you are trying to do have come a *very* long way since then.

In my case, it's because I running breezy on a Pentium III, 384 MB memory system (My motherboard even has two ISA slots) and Dapper locked up when I tried to install it from scratch. I doubt Dapper would have run speedily on my system anyway.

:KS

---

### Post by mixmaster87 on 2006-12-11
what do you mean with substitute? i tried this thou: ```
mixmaster@prodigy:~/Desktop/beryl-svn-1662mc-dapper$ sudo dpkg -i dpkg: --install needs at least one package archive file argument

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
mixmaster@prodigy:~/Desktop/beryl-svn-1662mc-dapper$

```

---

### Post by marx2k on 2006-12-11
How does one get all unfocused windows to become transparent? 

That's a pretty nice effect.  Another good effect without transparency is to have all unfocused/inactive windows to darken.  I haven't seen that ever done though :(

---

### Post by mixmaster87 on 2006-12-11
lol, sorry my bad:D i didnt unpack the files:P sorry for troubling tired minds:P i got it now:P (i just moved the packed file into a folder and named it after what you said:P)

---

### Post by lyceum on 2006-12-11
> **victorbrca said:**
> I'm a fresh noob, that's all. I installed Ubuntu from a CD a friend gave me last Tuesday. I'm trying it out first and learning. But I'll update from this version as soon as I feel I'm worthy of it!!!! ;) 

I'm already in love thou!!!!


Vic.

It is easier to learn from a newer modle. Less bugs, easier to use, etc..

> **ardvark71 said:**
> In my case, it's because I running breezy on a Pentium III, 384 MB memory system (My motherboard even has two ISA slots) and Dapper locked up when I tried to install it from scratch. I doubt Dapper would have run speedily on my system anyway.

:KS

I set up Dapper on P III with less memory all the time. You may want to try the alterent down load if you want Dapper, or you could run Xubuntu 6.06 or 6.10. If you don't like the XFCE DE you can add Gnome without loseing the speed. If you do want to try Xubuntu I like 6.10 alot better. Minor differences can mean the world sometime.

---

### Post by mixmaster87 on 2006-12-11
there is only one thing i need help with left with beryl.
how do i move the windows away from the desktop cube? like you see in those beryl 0.1.3 demos? where is the option for it or what is it called?

otherwise thx for all help:D i love the community here:D

---

### Post by robgill on 2006-12-11
> **mixmaster87 said:**
> there is only one thing i need help with left with beryl.
how do i move the windows away from the desktop cube? like you see in those beryl 0.1.3 demos? where is the option for it or what is it called?

otherwise thx for all help:D i love the community here:D

Check the second option on the left A 3D World.

---

### Post by victorbrca on 2006-12-11
> **marx2k said:**
> How does one get all unfocused windows to become transparent? 

That's a pretty nice effect.  Another good effect without transparency is to have all unfocused/inactive windows to darken.  I haven't seen that ever done though :(

I know, that's exactly what I wanted. I'm not sure how he did thou.

This is the link if interest you:

[Here]("http://gentoo-wiki.com/Xorg_X11_and_Transparency")


Vic.

---

### Post by ardvark71 on 2006-12-11
> **lyceum said:**
> 
I set up Dapper on P III with less memory all the time. You may want to try the alterent down load if you want Dapper, or you could run Xubuntu 6.06 or 6.10. If you don't like the XFCE DE you can add Gnome without loseing the speed. If you do want to try Xubuntu I like 6.10 alot better. Minor differences can mean the world sometime.

I would definately prefer Gnome and KDE if I were able to get Dapper to actually install.....no matter, Breezy is doing very well for what my needs are. 8) 

Best Regards...

:KS

---

### Post by dolphinsonar on 2006-12-11
Beryl is good.

---

### Post by victorbrca on 2006-12-13
> **igknighted said:**
> Out of curiosity, is there a reason you are still running breezy?  The technologies involved in what you are trying to do have come a *very* long way since then.

You know what, I'm so stupid.....  I'm running Dapper. I thought I read somewhere that the version that comes with the shipit CD was Breezy. 

I'm probably gonna install Edgy and delete my XP partition from my laptop. I just need to find more info about VMWare so I can use for my Windows studying!!!!


/vic

---

### Post by tonyisntcreative on 2006-12-17
> **victorbrca said:**
> So, can I actually get something like this using xcompmgr?

[screenshot]("http://gentoo-wiki.com/images/thumb/1/1d/Transparent4.png/750px-Transparent4.png")



Vic.
Funny you link that photo, because it actually stems from the HOWTO that I used to get transparency working on my computer.  I only browsed this thread so I'm not sure if you figured your problem out or not. 

This is the link to the page - [http://gentoo-wiki.com/TIP_Xorg_X11_and_Transparency](http://gentoo-wiki.com/TIP_Xorg_X11_and_Transparency)

---

### Post by victorbrca on 2006-12-18
> **tonyisntcreative said:**
> Funny you link that photo, because it actually stems from the HOWTO that I used to get transparency working on my computer.  I only browsed this thread so I'm not sure if you figured your problem out or not. 

This is the link to the page - [http://gentoo-wiki.com/TIP_Xorg_X11_and_Transparency](http://gentoo-wiki.com/TIP_Xorg_X11_and_Transparency)

You wouldn't believe the trouble I went to get things working on my Laptop.... I tried XGL x Compiz, them Aixgl x Compiz (which screwed my X) and them I decided to wipe out my laptop and install Edgy, and them Aixgl x Compiz....  Got it working thou... took me the whole weekend but was worthy.....


Vic.

---

### Post by reiatzu on 2006-12-18
Upgrade to Edgy/Fiesty.

---

