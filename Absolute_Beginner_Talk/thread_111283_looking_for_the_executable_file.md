---
title: "looking for the executable file"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by mr.wx on 2006-01-02
I think I got the program zinf to install but now what? I believe I need to create a launcher on the desktop but I have no idea what file to link to.Does the file I need have a particular file extension?Just what do I look for in a the list of files is there a particular icon to search for? thanks

---

### Post by ape on 2006-01-02
open a terminal window and type the command `which zinf`.  This will give you the path to the executable zinf file.  This would be the path that you would enter into your launcher properties.

---

### Post by mr.wx on 2006-01-02
[QUOTE=ape]open a terminal window and type the command `which zinf`.  This will give you the path to the executable zinf file.  This would be the path that you would enter into your launcher properties.[/QUOTE]

I tried it and the terminal just goes blank .I think the files are installed I can see them and go through them.

---

### Post by ninotob on 2006-01-02
blank?  weird.

Try:

whereis zinf

You'll see a few more entries, look for the *bin* entry (but not the *bin/X11* entry, or the *man* entry).

---

### Post by mr.wx on 2006-01-02
[QUOTE=ninotob]blank?  weird.

Try:

whereis zinf

You'll see a few more entries, look for the *bin* entry (but not the *bin/X11* entry, or the *man* entry).[/QUOTE]

well that is a little better it instead of returning a blank it retuned  -    zinf:

---

### Post by ninotob on 2006-01-02
That means it couldn't find it -- I suspect you don't have it installed.

Did you install from synaptic or download from zinf's website?

---

### Post by ninotob on 2006-01-02
I just installed zinf through synaptic.  When I do a whereis zinf, I get this:

```

zinf: /usr/bin/zinf /usr/lib/zinf /usr/bin/X11/zinf /usr/share/zinf /usr/share/man/man1/zinf.1.gz
```

the executable you'd want to use is:

/usr/bin/zinf

But you don't have it.  Try installing through synaptic (System-Administration-Synaptic...).  Search for "zinf" -- select the "zinf" package for installation -- press "apply".

---

### Post by ninotob on 2006-01-02
Sorry to spam the thread -- but note that if you install through synaptic, you won't have to create a menu icon or anything.  Zinf will be placed in Applications-Sound&Video.  You may have to log out, and log back in to see it.

---

### Post by ninotob on 2006-01-02
Me again, sorry, but Zinf seems pretty rudimentary.  I don't see smart playlists (I didn't look hard though).  Rhythmbox (already installed) allows smart playlists.

Smart playlists are things like this:  Show all songs rated 3 stars or better, which I haven't listened to in at least one month, but don't include the 60s genre.

You can access your music like info in a database.  Way better than manually creating playlists (which you can also do if you want).

Which brings us to uninstalling -- go back to synaptic, search for zinf, right click on the box, and choose to remove, or completely remove ... I'm off to do that now.  ;-)

---

### Post by mr.wx on 2006-01-02
[QUOTE=ninotob]That means it couldn't find it -- I suspect you don't have it installed.

Did you install from synaptic or download from zinf's website?[/QUOTE]

I installed it through the website.I understand how to install a package from synaptic that is already listed there ,but how do you place a file of your own such as zinf to be installed through synaptic?
I unistalled what files there were and I'm ready to try the synaptic method.

the reason I'm going to try zinf is because I couldn't get rythmn box to work for internet radio.It works great for playing cd's but I tried for several hours to get it to work for internet radio and I get nothing but static.

---

### Post by phido on 2006-01-02
[quote=mr.wx]I installed it through the website.I understand how to install a package from synaptic that is already listed there ,but how do you place a file of your own such as zinf to be installed through synaptic?
I unistalled what files there were and I'm ready to try the synaptic method.

the reason I'm going to try zinf is because I couldn't get rythmn box to work for internet radio.It works great for playing cd's but I tried for several hours to get it to work for internet radio and I get nothing but static.[/quote] 

If u have a *.deb package, its *dpkg -i package.dep*.   
For source u need this *dh-make fakeroot build-essential*, then goto the source folder, and type *dh_make* if theres no debian folder in there. Now u can make a debian package with *fakeroot debian/rules binary *and then install it with *dpkg -i ../package.deb.*

---

### Post by ninotob on 2006-01-02
If you don't see zinf in synaptic, you need to enable some extra repositories.

Open synaptic, click "settings" then "repositories".  A popup opens, click the settings button at the bottom, check the "Show disabled ..." option at the top of the new popup.  Click OK.

You should see more repositories -- I'm not sure which one zinf is in, but it is in one of the default but disabled set.

---

