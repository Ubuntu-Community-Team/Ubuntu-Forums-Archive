---
title: "No clue how to install wine"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by regiemon on 2006-02-16
hello, i'm a newbie in linux. for my first linux os, i installed ubuntu.
and right now i wanted to install wine so i could install some windows application.i just downloaded wine(wine-0.9.8.tar.bz2) at sourceforge.net.

but right now i don't have any clues :-k on how i could install this to my ubuntu.

please help.

thanks very much.:)

---

### Post by ubuntes on 2006-02-16
Hi, I just did this!

click System->Synaptic Package Manager
click Settings->Repositories
click Add->Custom

enter "deb  [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/

Cheers,
Alex

---

### Post by wondering_jew on 2006-02-16
delete this post :P some one answered while i was answering :p

---

### Post by regiemon on 2006-02-16
but my ubuntu is not yet connected to internet. i haven't configure it to access internet yet.



[QUOTE=ubuntes]Hi, I just did this!

click System->Synaptic Package Manager
click Settings->Repositories
click Add->Custom

enter "deb  [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/

Cheers,
Alex[/QUOTE]

---

### Post by Sutekh on 2006-02-16
I think you'd be *way* off better trying to download a debian package (.deb) for wine, rather than the source code (.tar.gz) and have to compile it.

Here's a link (not the latest version, but 
[Wine 0.9.8 - From wine.sourceforge.net]("http://wine.sourceforge.net/apt/breezy/wine_0.9.8-winehq-1_i386.deb")

Once you download the wine package, transfer the file to a folder in Ubuntu.  Then you can install from the folder using
```
sudo dpkg -i wine_0.9.8-winehq-1_i386.deb
```

---

### Post by steve.horsley on 2006-02-16
[QUOTE=regiemon]but my ubuntu is not yet connected to internet. i haven't configure it to access internet yet.[/QUOTE]

Get this working first. Top priority. Ubuntu is a huge distro, and it includes wine, but most of the distro is not on the install CD - just the online repositories.

P.S.
Welcome to the community.

---

### Post by regiemon on 2006-02-16
I installed my network card and now i can access internet via a router.
that was easy i thought i'll be having a hard time installing it.

i installed also the wine.thanks very much for your responses.

now,how do i install microsoft office.it still doesnt recognize setup.exe?

sorry for my dumb questions.coz i'm really new in linux.

thanks in advance

---

### Post by regiemon on 2006-02-16
also, why i couldnt see the ubuntu into my windows os.but in vice versa
i could see my windows files when im using ubuntu.
how do i access ubuntu in my windows os?

---

### Post by handy on 2006-02-17
Windoze does not recognise the Linux file system.

This is how windoze is made!

Ubuntu can read & copy files FROM ntfs, but not write or delete them on ntfs.

Fat32 is rw (readable & writable) to Ubuntu & windoze of course!  So it is often a good idea in a dual boot situation to create a fat32 partition to move files from linux to windoze.

If you choose to do that you may need to post a question so that we can tell you what you need to do in Ubuntu to make that partition accessible to Ubuntu. 

It is not hard, just a few steps & a little editing!:KS 

The first thing that you will have to do if you go to making another partition, is make it!  
Do you have Partition Magic?  If so that will make the job very easy.

Post questions here, it is rare not to get help...:KS

**[Edit:]**  Unlike windoze, Ubuntu has very good online help!  You might be surprised how well many things are explained there.  If you haven't checked it out yet it is accessed via the small red & white **life-bouy** icon in the panel, & via the ***Menu:*  System / Help**

---

