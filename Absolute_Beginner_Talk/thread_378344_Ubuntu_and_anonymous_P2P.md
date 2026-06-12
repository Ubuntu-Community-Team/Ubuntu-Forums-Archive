---
title: "Ubuntu and anonymous P2P"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-03-07
Has anyone successfully used Anonymous P2P with Ubuntu?
I tried ANtsP2P but it won't start, supposedly because the port 443 it would like to use is already taken (even after I have changed the default port setting), and am now considering giving MUTE a shot.
Have you had better luck?

---

### Post by Blofeld on 2007-03-07
To rephrase my question (I don't want to focus on getting ANtsP2P up and running), how can I do Anonymous Filesharing with Ubuntu -- are there any clients available?
Thanks.

---

### Post by Blofeld on 2007-03-07
I'm now trying out GNUnet, will let y'all know how it goes.:popcorn:

---

### Post by C-A on 2007-03-07
You could try [GNUnet]("http://gnunet.org/index.php?xlang=English").

Edit: Looks like you found it before I hit submit.

---

### Post by Sukarn on 2007-03-07
Theres something wrong here. Ubuntu Forums is showing that C-A posted this 5 minutes before Blofeld, but still Blofeld's post is appearing first.

---

### Post by Blofeld on 2007-03-07
@C-A:  Thanks, dude, I started feeling lonely in this thread.:( 
I've installed GNUnet but it just won't open.  Seems that it doesn't work with Xfce (I'm on Xubuntu), although it uses a GTK frontend.:confused: 
@Sukam:  I think it's just that the forum software doesn't update that often.  I've noticed that sometimes it takes quite some time for my postings to appear.

---

### Post by C-A on 2007-03-07
> **Blofeld said:**
> @C-A:  Thanks, dude, I started feeling lonely in this thread.:( 
I've installed GNUnet but it just won't open.  Seems that it doesn't work with Xfce (I'm on Xubuntu), although it uses a GTK frontend.:confused: 
@Sukam:  I think it's just that the forum software doesn't update that often.  I've noticed that sometimes it takes quite some time for my postings to appear.

If you haven't tried already, try running "gnunet-setup" from the command prompt. Once the set up window opens, you can make changes or you if you like the defaults just close the window and then try opening gnunet.

Also, you might find some other alternatives by googling: onion router bittorrent.

---

### Post by Blofeld on 2007-03-08
Running gnunet-setup results in an "error while loading shared libraries".  I suspect that this has to do with me using Xfce rather than GNOME, or possibly because I'm already using Xfce 4.0.

---

### Post by mikeym on 2008-06-20
The problem is that the version of gnunet-gtk for hardy does not match the version of gnunet. 

You can install it from this page instead [http://gnunet.org/download.php3](http://gnunet.org/download.php3).

---

