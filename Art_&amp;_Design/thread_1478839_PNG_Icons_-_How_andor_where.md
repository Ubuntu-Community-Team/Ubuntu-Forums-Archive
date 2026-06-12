---
title: "PNG Icons - How and/or where"
date: 2010-05-10
forum: Art &amp; Design
---

### Post by zootoxin on 2010-05-10
Good morning guys, 

I have created a large number of PNG icons which I want to incorporate into my ubunto 9.10 theme on my laptop. 

Please could somebody tell me in great detail how I go about doing this. 

Lets take as an Example my icon called pidgin.png which is sat in Pictures/My Icons/

how do I make sure that icon is used on awn, menu bar, panel and notification area. 

Many thanks in advance

---

### Post by arsenic23 on 2010-05-10
First take a look at the themes in /usr/share/icons

You are going to have to make a small one of these that inherits from whatever theme you are using.

The basic setup is that you'll have an index.theme, which is a plain text file, and a set of folders corresponding to icon sizes.  Since your icons are png, you can skip out on the scalable folder (I think), since it is designed for vector icons.  The index.theme refers to each folder and lets gnome know what is going on inside.  Inside each of these folder you'll place your icons, named correctly, and symlinks to them to cover whatever other names they need to be under.  The best way to find the correct filenames for them is to just look at the default Gnome icon them.  Just looking at how it is setup in the icon themes currently installed should be enough to get you started.

I recommend placing a folder someone in your home directory where it can live permanently, and then then symlinking it into the /usr/share/icons folder.  This way you can see the changes to your theme in realtime without installing and uninstalling it.

---

### Post by zootoxin on 2010-05-12
Thanks for the tip but it doesnt seem to work, if I change the icon in the folder it just stays the same on the UI. 

There also seems to be Icons every where and some are shortcuts to places I can not find.

Please can you explain.

---

### Post by arsenic23 on 2010-05-12
OK.  I have a small icon theme that I use on top of the old Human theme and Tango.  I'm going to use that as an example.  You can download it here if your interested: [http://gnome-look.org/content/show.php/Maulk?content=67832](http://gnome-look.org/content/show.php/Maulk?content=67832)
I'm using my theme because I know it so well, but when your setting yours up it'll be better to take cues from the default gnome theme them from anything else.

OK. If you look at the first image I've attached you'll see my setup for ease of updating.  Like I said before I have the theme folder laid out in my home directory with a symlink in /usr/share/icons/.  This means all I have to do to see my changes lives is quickly toggle between my icon theme and another in the Appearance dialog.  You can also get a decent idea on how the folder is laid out.  I said in my previous post that you wouldn't need a scalable folder, but that might not be true.  If you have a very high res copy of your icon then it might be prudent to include it in scalable.

I've also attached my index.theme file (as 002.txt).  
The Name and Comment fields should be obvious, the Inherits field should be the other icon themes applied under yours in depending order.  In my case if I don't have an icon for something it looks to the old Human theme, then Tango and then Gnome. (Of course these themes have to be installed for this to work.)  Example is the name of the icon that will show up in the Appearances dialog when to go to select your theme.  In my case x-directory-normal is one of the names take by my folder icon.  The directory list contains the names of every directory in your theme folder and under the main list is a brief setup for each one explaining to the theme what it contains.  If your index.theme is not 100% correct and typo free some of your icons will not appear.

You'll notice that the smaller sizes have less folders on my theme.  That is because you can get away with only making very small icons for the icons that will be displayed at those sizes.

Each icon image has to have its correct name and be included in the proper folder.  Many icons have multiple names they need to be included as, so creating one icon for each size and then symlinking it to its other names is what is normally done.  If you look at 004.png you'll see all of the different names the folder icon has to appear as to function correctly.  Just the home folder icon has three.  There are also some of the same icons in the filesystems folder.  

As for pidgin....  I'm not 100% on what that should be called.  I don't see it in any of the other themes I have.  I would assume that you'd simply place a pidgin.png in all of the apps folders but if that doesn't worked you could look for a theme on Gnomelook that replaces the pidgin icon, unpack it, and take a look at their setup.

---

### Post by zootoxin on 2010-05-13
Thanks very much I will look at this in more depth when I get home, but in the mean time (this is probably a super noob question but..) what do you mean by symlink? 

Thanks for all your efforts on this

---

### Post by arsenic23 on 2010-05-13
Symlinks (symbolic links) are basically shortcuts to a file or folder that can be treated as that file or folder for most intents and purposes.  Say the icon you are using as your network folder is 61kb.  By using symlinks that icon would take up just 100.6kb while if you copied if out 12 times you'd fill 732kb.  This quickly makes quite a difference in filesize of your icon theme once you start into it.  If you look up at the third image I posted in the above post you'll see the symlinks are the files with the little white arrows up in their corners.

The best way to create a symlink is through the command:
```
ln -s filetobelinkedto symlinkcreated
```

More in depth explanation of symlinks:
[http://en.wikipedia.org/wiki/Symlink](http://en.wikipedia.org/wiki/Symlink)

---

### Post by zootoxin on 2010-05-20
Is there a sort of family tree of icons listed anywhere? because that would be super cool

ie

Applications
        |
    pidgin
    Mplayer

etc etc...

---

### Post by arsenic23 on 2010-05-20
Not that I'm aware of.
If you find one, though, please tell me, because I'd love one as well.

---

### Post by bra|10n on 2010-05-20
Hi zootoxin
If you're not talking about creating a system-wide icon set then my advice is to to use a _[COLOR=Black]downloaded[/COLOR]_ theme you are reasonably happy with and substitute your icons for the default in that theme. 
With this approach you will soon become familiar with the icon-set structure used, eg symlinks and get a feel for what it takes to build an entire set from base.

Two points to note:
Your .png files can be renamed .svg and copied to the correct theme folder, causing the usual prompt; "File name exists. Replace?", to which you will of course accept.
To update syslinks to the particular icon you have substituted, a simple refresh is all that's required. This will help you see exactly where you are at.

Lastly, its tedious and a pain quite honestly, but rewarding to see your creations in situ

cheers

---

### Post by tgalati4 on 2010-05-20
Stand back:

locate icons

Once you have brushed yourself off:

cd
locate icons > icon_locations.txt

---

### Post by arsenic23 on 2010-05-21
> **bra|10n said:**
> Your .png files can be renamed .svg

This is unnecessary, you can just leave them png and remove the svg files; it is still much cleaner to use inheritance then to copy another theme and replace.

---

### Post by bra|10n on 2010-05-22
> **arsenic23 said:**
> This is unnecessary,[COLOR=Red] you can just leave them png and remove the svg files[/COLOR]; it is still much cleaner to use inheritance then to copy another theme and replace.
Now this I didn't know. Thanks arsenic23

---

