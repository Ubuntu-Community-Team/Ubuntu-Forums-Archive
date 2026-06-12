---
title: "Simple question"
date: 2005-11-11
forum: Absolute Beginner Talk
---

### Post by natman on 2005-11-11
Hi i have been looking around to get (ndiswrapper) a wireless card working and i came across some good instructions, but i am stuck at one point.
It says
> Use this list ([http://ndiswrapper.sourceforge.net/phpwiki/index.php/List](http://ndiswrapper.sourceforge.net/phpwiki/index.php/List)) to look up the right driver. The drivers that came with the card on a cd do not always work and may cause crashes. The cabextract ([http://www.kyz.uklinux.net/cabextract.php](http://www.kyz.uklinux.net/cabextract.php)) tool will help to decompress some drivers. Once you have all the driver files ready, look for the right .inf file (bcmwl5a.inf for example). Then use the ndiswrapper command to install it:

 # ndiswrapper -i bcmwl5a.inf

And check the status:

 # ndiswrapper -l

When you insert the card and run the above command you should see:

 Installed ndis drivers:
 bcmwl5a driver present, hardware present



I have the inf file lying on my desktop, when i run the command i get the following
> Unable to create directory /etc/ndiswrapper/rt2500. Make sure you are running as root
natman@centralcomputer:~$ sudo ndiswrapper -i Rt2500.inf
Password:
Installing rt2500
cp: cannot stat `Rt2500.inf': No such file or directory


Can anyone help ?
Thanks

---

### Post by Kyral on 2005-11-11
Maybe you need to type out the whole path?

---

### Post by natman on 2005-11-11
I am really a newbi , whats the whole path, can you give me the path?

---

### Post by Third Thoughts on 2005-11-11
[QUOTE=natman]I am really a newbi , whats the whole path, can you give me the path?[/QUOTE]
The path to your Desktop will be ~/Desktop, or /home/<username>/Desktop where <username> = your username. Alternatively if you're in your Desktop then you can just type ./ which means current working directory. Any of the three methods should work.

~Andrew S.

---

### Post by lik3n on 2005-11-12
I would say get the gui way to install drivers for wireless cards. I spent a good 2 hours trying to do it with the console then I found this and it worked on the first try.
```
sudo apt-get install ndisgtk
```

Run it and select the driver.

You *should* be good to go. Notice that I say should.

---

