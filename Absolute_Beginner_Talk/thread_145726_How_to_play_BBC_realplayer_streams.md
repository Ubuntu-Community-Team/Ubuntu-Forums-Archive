---
title: "How to play BBC realplayer streams"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by High Plains Drifter on 2006-03-16
[IMG]http://newsimg.bbc.co.uk/nol/shared/img/nav/v3_banners/v3_ifh_banner.gif[/IMG]

Install RealPlayer 10

[http://www.real.com/linux?pcode=rn&opage=freeplayer_partner&src=freeplayer_partner](http://www.real.com/linux?pcode=rn&opage=freeplayer_partner&src=freeplayer_partner)

cd ~/Desktop
sudo apt-get install libstdc++5
chmod +x RealPlayer10Gold.bin
sudo ./RealPlayerGold.bin

When the installer asks for a directory, you should use one of the customary locations for software that is not part of a distribution, either /opt/RealPlayer or /usr/local/RealPlayer. 


After installing Realplayer, you need to copy the files nphelix.so and nphelix.xpt from /usr/lib/mozilla/plugins to your .firefox and .mozilla plugins folders in /home/username/.firefox/plugins and /home/username/.mozilla/plugins.

Then you restart firefox and away you go!

---

### Post by jonathansizz on 2006-03-16
[That's what I said!]("http://www.ubuntuforums.org/showthread.php?t=133544")

---

### Post by lerrup on 2006-03-17
or you could download a .deb from a repository such as the mariallat one and let  apt deal with it (don't count on my spelling though).

Use the package management system - its why debian and its progenies are worth using...

---

### Post by dvarsam on 2006-03-17
And what do you do when you reach this stage:

"...Copying RealPlayer files...configure system-wide symbolic links? [Y/n]: ..y.
enter the prefix for symbolic links [/usr]: ......................: "

What do I type man?

Your "HowTo" is only partially complete!

---

### Post by jonathansizz on 2006-03-25
you just hit enter for the default (/usr)

---

### Post by gigi1234 on 2006-04-14
I don't know if anyone is still looking at this thread but I am trying to follow these instructions and I seem to lack any .firefox and .mozilla directories in my /home/username directory. 

So...I am totally stumped! Anyone know what the problem could be?

I am running Breezy.

---

### Post by gingermark on 2006-04-14
[QUOTE=gigi1234]I don't know if anyone is still looking at this thread but I am trying to follow these instructions and I seem to lack any .firefox and .mozilla directories in my /home/username directory. 

So...I am totally stumped! Anyone know what the problem could be?

I am running Breezy.[/QUOTE]

When a directory begins with a dot it means it's hidden. There should be an option to view hidden files and folders in your file manager - not too sure where it is for gnome though.

---

### Post by gigi1234 on 2006-04-14
Oh!!! Ah hah, so you really DO learn something new everyday! Thanks!

I wondered what the dot meant!

---

### Post by gigi1234 on 2006-04-14
I still do not see the .firefox dir however I do see the .mozilla dir. 

Maybe it is enough just to copy the files here?

---

### Post by catflea on 2006-04-16
within my .mozilla folder there was a firefox sub-folder,  I copied the plug-in files into there too.

For the sake of completism I created a .firefox folder and copied into there as well.

BBC now works perfectly

---

