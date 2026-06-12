---
title: "Opera Icon"
date: 2005-09-02
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-09-02
i've had some trouble finding the Opera icon. I'm registering to the Opera Forums, but in the meanwhile i hoped someone here would know anyways how i might go about putting an Opera icon on the panel.

is there  a settings/refresh icons somewhere?

--
sophtpaw

---

### Post by KingBahamut on 2005-09-02
lol

hmmm...

/usr/share/pixmaps.

---

### Post by sophtpaw on 2005-09-02
[QUOTE=KingBahamut]lol

hmmm...

/usr/share/pixmaps.[/QUOTE]


Thats genius. I didn't know that there was a place where they all hung out. For some reason, however, the Opera icon is not among them  :-? 

Any other suggestions?

I'm glad to hear that my stupid questions are welcome,

--
sophtpaw

a.ka.
grasshopper

---

### Post by aysiu on 2005-09-02
My Opera icon is in /usr/share/opera/images/

Of course, you can always just download it:

[http://www.ecards-gallery.com/images/opera-icon.png](http://www.ecards-gallery.com/images/opera-icon.png)

---

### Post by sophtpaw on 2005-09-02
[QUOTE=aysiu]My Opera icon is in /usr/share/opera/images/

Of course, you can always just download it:

[http://www.ecards-gallery.com/images/opera-icon.png](http://www.ecards-gallery.com/images/opera-icon.png)[/QUOTE]


Who's got a cool 'O' on top of their panel?!

Thanks Aysiu!

Seems i always wanna make easy things difficult  :grin:  KingBahamut had me along the right tracks. 

Actually, i had just found where the icons are kept in Opera.com and tried to download it to /usr/share/pixmaps but it wouldn't let me because i would need to have root priviledges.

Although hypothetical now, can you please, or someone, tell me how i would save something to a root prviledge folder?

so, i'm in Opera just for example, i see the icon but instead of saving it to /home/username as per usual how do i put it in this case in /usr/share/pixmaps?

i reckon that knowledge might come in handy sometime  :-P 


thx again,

--
sophtpaw

---

### Post by xmastree on 2005-09-02
```
sudo cp ~/source.file /usr/share/pixmaps/
```

---

### Post by aysiu on 2005-09-02
Or if you want to move it instead of copying it:

sudo mv /home/username/opera.png /usr/share/pixmaps/opera.png

---

### Post by sophtpaw on 2005-09-02
[QUOTE=xmastree]```
sudo cp ~/source.file /usr/share/pixmaps/
```[/QUOTE]

I wanna get this clear and i'm gonna try this. 

So, xmastree, i'm at the page [http://my.opera.com/community/gfx/banners/](http://my.opera.com/community/gfx/banners/)  how exactly are you suggesting i would now copy?

If i wanted Opera1.gif from the list i would not open a terminal and go: sudo cp ~/Opera.gif/usr/share/pixmaps  ??

i tried that:

conrad@x1-6-00-0b-6a-16-78-f0baraka:~$ sudo cp ~/Opera.gif/usr/share/pixmaps
Password:
cp: missing destination file
Try `cp --help' for more information.

I know its right in front of me - i'm just blind  :) 

--
sophtpaw

---

### Post by xmastree on 2005-09-02
> So, xmastree, i'm at the page [http://my.opera.com/community/gfx/banners/](http://my.opera.com/community/gfx/banners/) how exactly are you suggesting i would now copy?First you right click on the graphic you want, and save it in your home directory or wherever. Then using a terminal, sudo either copy (cp) or move (mv) it to the new destination.

You could run opera as root, and save it directly to that folder, but that's probably not a good idea.



> conrad@x1-6-00-0b-6a-16-78-f0baraka:~$ sudo cp ~/Opera.gif/usr/share/pixmapsJust noticed that. there should be a space between the end of the filename and the beginning of the destination folder.

```
sudo cp ~/Opera.gif /usr/share/pixmaps
``` 

HTH

---

### Post by sophtpaw on 2005-09-02
[QUOTE=xmastree]First you right click on the graphic you want, and save it in your home directory or wherever. Then using a terminal, sudo either copy (cp) or move (mv) it to the new destination.

You could run opera as root, and save it directly to that folder, but that's probably not a good idea.



Just noticed that. there should be a space between the end of the filename and the beginning of the destination folder.

```
sudo cp ~/Opera.gif /usr/share/pixmaps
``` 

HTH[/QUOTE]

So, its a two step. 
No problemo. i got it in downloads.
 now:

conrad@x1-6-00-0b-6a-16-78-f0baraka:~/downloads$ sudo cp ~/Opera.gif /usr/share/pixmaps
cp: cannot stat `/home/conrad/Opera.gif': No such file or directory
conrad@x1-6-00-0b-6a-16-78-f0baraka:~/downloads$

Arrrgh...
No such file or directory?? but i can see it in my /home/downloads now!
well, the space in between filename and destination did make a difference anyways. Different error message  :)  hopefully in the right direction

--
sophtpaw

---

### Post by xmastree on 2005-09-02
> ~/downloads$ sudo cp ~/Opera.gif /usr/share/pixmaps
```
~/downloads$ sudo cp Opera.gif /usr/share/pixmaps
``` Spot the difference.

You in london? Must be about 4:10 am there...

---

### Post by sophtpaw on 2005-09-02
[QUOTE=xmastree]```
~/downloads$ sudo cp Opera.gif /usr/share/pixmaps
``` Spot the difference.

You in london? Must be about 4:10 am there...[/QUOTE]


the eagle has landed! what a difference a squiggly line makes. Yes, London 4:18 am, so i hope i can be forgiven. Woke up and wanted to  have another go at this problem. I don't trust my machine will be there in teh morning  ;-) 

Thank you for the lesson in cp and command line!

--
sophtpaw

---

