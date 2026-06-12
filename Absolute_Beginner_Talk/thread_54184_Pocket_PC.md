---
title: "Pocket PC"
date: 2005-08-03
forum: Absolute Beginner Talk
---

### Post by the_purulent on 2005-08-03
I have an Ipaq 3000 series, multi media type handhelp.

What do I use to autosync it with a ubuntu system so that I can copy email, address, files and such back and forth? 

Great product for movies on the road by the way ;)

---

### Post by Nequeo on 2005-08-03
Try this:
[http://www.ubuntuforums.org/showthread.php?t=30936&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=30936&page=1&pp=10)

I should add, though, that I have a Navman PocketPC (GPS navigation), and I've never succeeded in getting it to connect with Hoary 5.04. It does beep at me when I type in the commands to connect... but then it just sits there saying, "Waiting for your PC to connect". Anyway, give it a shot.

Cheers,

---

### Post by the_purulent on 2005-08-03
Hmmm... yes I saw that guide, but it doesn't seem to cover the basics.  Do I just find This 'synce' program in synaptec or app-get it and then hook up my ppc?

---

### Post by Nequeo on 2005-08-03
[QUOTE=the_purulent]Hmmm... yes I saw that guide, but it doesn't seem to cover the basics.  Do I just find This 'synce' program in synaptec or app-get it and then hook up my ppc?[/QUOTE]
 The article does state what you need to apt-get. In this case
```

sudo apt-get install librra0 librra0-tools librapi2-tools libsynce0 synce-dccm synce-multisync-plugin synce-serial
```
But you will need to read the entire thread from beginning to end if you want to have any hope of getting your PPC syncing. And even then it probably won't work. I'm afraid that pocketPC support is severly lacking in Gnome. 

If PPC support is a Big Thing for you, you might want to try Mepis ([www.mepis.com)](www.mepis.com)). If you can live with the fact that parts of it aren't open source, and don't mind KDE, you might have better luck there. KDE has better GUI programs for PocketPC support, it seems.

Otherwise... you have three options. Program it yourself, buy a palm, or switch back to Windows and try again when Ubuntu 6.04 comes out next year!  

Sorry for the bad news, but good luck nonetheless. 

And if you do get it working, be sure to post about it here! 

Cheers,

---

### Post by The Odometer on 2005-08-11
[QUOTE=Nequeo]
If PPC support is a Big Thing for you, you might want to try Mepis ([www.mepis.com)](www.mepis.com)). If you can live with the fact that parts of it aren't open source, and don't mind KDE, you might have better luck there. KDE has better GUI programs for PocketPC support, it seems.

[/QUOTE]

For what its worth-I have gotten my IPAQ 3835 to sync with Kubuntu.  I just used the How-To stated in the thread.  So-there is some hope in trying to get it to work-as a matter of fact, couldn't you just install the KDE base-and use it to sync-then simply log out and log back into GNOME?  (As opposed to using MEPIS-which I could never get to sync with my IPAQ) I'm just a noob as well-but that seems reasonable.

---

