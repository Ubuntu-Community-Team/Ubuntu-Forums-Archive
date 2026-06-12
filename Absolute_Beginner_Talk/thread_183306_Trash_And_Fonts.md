---
title: "Trash And Fonts"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by Kernel Sanders on 2006-05-27
Hi guys,

I'm playing with the Ubuntu Dappa Live CD (The latest one) and i'm loving it 8) 

However, there are currently 2 things "bugging" me about it (and linux in general in fact)

1) How do I make the Trash icon go onto the desktop instead of the bottom bar?

2) How can I use my Windows XP fonts in Dapper? As internet sites font looks weird for me in Ubuntu compared to viewing the same site in Windows?

Thanks again!

John :)

---

### Post by johnc4510 on 2006-05-27
Try this forum link for the desktop trash:
[http://www.ubuntuforums.org/showthread.php?t=180885&highlight=trashcan+desktop](http://www.ubuntuforums.org/showthread.php?t=180885&highlight=trashcan+desktop)

---

### Post by Kernel Sanders on 2006-05-27
[QUOTE=johnc4510]Try this forum link for the desktop trash:
[http://www.ubuntuforums.org/showthread.php?t=180885&highlight=trashcan+desktop](http://www.ubuntuforums.org/showthread.php?t=180885&highlight=trashcan+desktop)[/QUOTE]

Cool thanks, i'll definately give that a try when I run the Live CD again! :) 

What about my issue about getting my windows fonts into Dapper and firefox so that webpages display "normally"?

---

### Post by Kernel Sanders on 2006-05-27
No-one has any idea how to install fonts in ubuntu? :(

---

### Post by user1397 on 2006-05-27
[quote=*John*]No-one has any idea how to install fonts in ubuntu? :([/quote]
actually it's quite simple.  go to a site like [http://gnome-look.org](http://gnome-look.org) and download a GTK2 theme.  go to system->preferences->themes adn drag the tar file into it.  (don't extract it, just drag the tar file into the themes window and click ok and it'll be installed, then just select it.)

---

### Post by Kernel Sanders on 2006-05-27
Right, after a bit of "self research" I think i've found the fonts folder here:

var/lib/defoma/gs.d/dirs/fonts

Is that right?

However, trying to copy my saved fonts over to that folder tells me I dont have permission because I am not "the owner"??

I'm guessing I have to log in as root? Is that possible in a live CD? :( 

So I did a search and copy and pasted this into the terminal:
```

sudo -s -H
Password: <specify user password>

```

However, I have no idea what the default livecd dapper password is?

HELP! Please!!! ](*,) :(

@erik1397

Thanks for the reply erik :D 

However, I have the fonts I want to install on the desktop, and i'm trying to install them but dont know what i'm doing........ :( 

Can you offer any help?

I'm using the Dapper live cd

---

### Post by BobSongs on 2006-05-27
Here's [a reference]("http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide") you may be interested in. Keep it handy. There are all kinds of things you can tweak in Dapper as well as in Breezy. It covers the questions you asked as well as a few other things.

Hope you find it useful.

---

### Post by mynimal on 2006-05-27
For Windows fonts, open up Synaptic and search for msttcorefonts. :)

---

### Post by skippy81 on 2006-05-27
I know this sounds really dumb, but where exactly can he copy fonts to if hes using a live CD? Does it simulate the filesystem with a ramdrive or something?

Last time I checked, CDs were read only :-D  But then again I've never actually used a live CD.

---

### Post by Kernel Sanders on 2006-05-27
Thanks for all your help, unfortunately, i'm still stuck :(

I tried synaptic, and when I searched, it came up, then in the right hand window only openoffice was in the list? :confused: 

I tried this:
```
ubuntu@ubuntu:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate

```

But that didnt work either :(

I'm using the Dapper Live CD and I have a folder on my desktop with fonts in it....... how do I install them? :confused: 

HELP!!! ](*,)

---

### Post by mynimal on 2006-05-27
Try enabling some of the other repositories through Synaptic, most likely universe.

---

