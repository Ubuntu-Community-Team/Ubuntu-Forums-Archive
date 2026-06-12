---
title: "Howto tile windows in gnome. Window tiling. Here are instructions."
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Eoghanalbar on 2007-06-10
I am a total newb, but after much struggling I got this working and I've written some instructions that even I could follow. I did this for two reasons. First, I don't want anyone to have to struggle for such a stupid reason ever again. And second, I hope a more experienced user will come along and tell me how to do this easier.

First let me tell you how you actually use the tiling thingy, so that you can decide if you want get it. Say you want to tile two windows out of a bunch in the Window List (the actual name of that bar at the bottom). You click on the show desktop button, then you click on the list icons of the windows you want, then you've got to make sure they're not maximized, and then you click on the tile horizontal or tile vertical icons in the gnome panel.

It's okay, I guess. The not maximized thing is the most annoying part. At any rate, you learn a bit in getting it working, especially if you follow along with the directions and look up the bash commands (bash is the name of the crazy language of inscrutable contracted commands that you use in the terminal) that you're using as you come across them (use a site like [this]("http://linuxcommand.org/learning_the_shell.php") or google). Maybe that's one of the hardest things about starting to learn about linux: people are either trying to help by telling you to do perform these complicated rituals you don't understand, or you're trying to sift through huge databases full of explanations that you can't connect to anything. Maybe if you can somehow find a way to get explanations in context, that would be the key. But as I said, I'm still a newb. I guess we'll find out later.

But I digress.

(Some random notes to save trouble down the road:
-copy/pasting in the terminal is by SHIFT-ctrl-c/v, for some stupid reason.
-if you mess up some capitals, you get problems. It's Desktop, not desktop, for instance.
-and while you're copy/pasting, don't forget to replace YOU_USER_NAME with your actual user name :P )

1. First you need to download [THIS]("http://freshmeat.net/redir/wmtile/56365/url_deb/tile_0.7.1_i386.deb").

2. Firefox should automatically try and open it with the "gdebi package installer". It should open, and you should press "install package", and it should work.

(Steps 3 to 6 are how I got around the permission restrictions that wouldn't let me save changes to a file. Maybe there's a better way.) 

3. That done, you need to go through the menus [Applications > Accessories > Terminal]

4. Type in [sudo su] and hopefully you have the password. I popped up under "root@YOUR_USER_NAME:/home/YOUR_USER_NAME#", and I hope you do too.

5. Type in [cd /usr/share/tile] and hopefully you end up with "root@YOUR_USER_NAME:/usr/share/tile#"

6. Type in [gedit rc].

7. In the second "paragraph" the fourth line reads "multi-desktop off". Change it to [multi-desktop netwm] and save.

8. You do this step twice. Once for the vertical and once for the horizontal. 
Right click on the Gnome Panel (that's the name of that bar with "Applications" on it, but don't click on applications, click on an empty space) and go for "Add to Panel..." and click on "Custom Application Launcher". Set up everything like this:

Type: Application
Name: [Vertical or Horizontal or whatever you want. I just put in V and H]
Command: tile -v -w
(-v for vertical, -h for horizontal. No idea what the -w is for. Something to do with Gnome, I think)
Comment: [Anything you want; I left it blank]

It works?

I wanted to get some icons, too. So I eventually figured this out:

First I had to make the icons. If you want, skip that and just take mine and save them to your desktop (I hope this works). They're at the bottom of this post, the attached images.

Or make your own:

1. Menus [Applications > Add/Remove...]

2. Find and download "KIconEdit". This'll be under menus [Applications > Graphics] if you lose it.

3. Make and save your icon to the desktop (as V.png and H.png if you want to match the names I use in the instructions. Remember, capital letters are different from lower case.)


Now to get it working:

1. You still got the terminal open in root? Better go get it again if you don't.

2. [mv /home/YOUR_USER_NAME/Desktop/V.pgn /usr/share/pixmaps]

3. Repeat with H.png

4. Right click on your vertical tiling button in the panel bar, select properties, click on that "Icon" thing in the upper left, and find your "V.png". 

5. Repeat with the horizontal button.



Okay, did that all work?

---

### Post by bone43 on 2007-06-10
Nice job you may also want to check out this page..

[http://ubuntuguide.org/index.php?title=Ubuntu:Feisty&printable=yes](http://ubuntuguide.org/index.php?title=Ubuntu:Feisty&printable=yes)

there is a how to for a launcher that tiles windows horizontally and many many other guides i have not tried it as i use Beryl. :D

---

### Post by Eoghanalbar on 2007-06-10
Thank you, bone43, for *directing me to the main source that I used to write this guide*.

*cough cough*

Or was that your point? My version is a lot easier to understand, at least.

Um, namaste.

---

### Post by bone43 on 2007-06-10
> **Eoghanalbar said:**
> Thank you, bone43, for *directing me to the main source that I used to write this guide*.

*cough cough*

Or was that your point? My version is a lot easier to understand, at least.

Um, namaste.


No point and as i said "good job" really!
 I just included the link becuse it is useful to have and had no idea you had made you instrucions from the page.

Have a great day :p

---

### Post by Eoghanalbar on 2007-06-10
Sorry, was I coming off as snappish? Thanks anyway, man.

---

### Post by bone43 on 2007-06-10
> **Eoghanalbar said:**
> Sorry, was I coming off as snappish? Thanks anyway, man.


No worries mate!!!! :p

---

### Post by Nonno Bassotto on 2007-06-13
Just a little thing: if you want you can condense step 4 to 6 in
```

sudo gedit /usr/share/tile/rc

```

And you can change the terminal settings, so that copy/paste is ctrl c/v, under edit->current profile. I don't know why it has this strange default.

---

### Post by kittyhawk63 on 2007-06-13
> **Nonno Bassotto said:**
> Just a little thing: if you want you can condense step 4 to 6 in
```

sudo gedit /usr/share/tile/rc

```And you can change the terminal settings, so that copy/paste is ctrl c/v, under edit->current profile. I don't know why it has this strange default.

If you have a mouse with a wheel, all you have to do to copy and paste is highlight the words you want to copy and paste and then go into Terminal or any document and press your wheel down. It will paste. Try it. It makes it easy to avoid mistakes, which the original poster mentioned.
kh

---

### Post by Eoghanalbar on 2007-06-13
Thank you both for the additional information. If you only need superuser for one thing, then it's easier to just stick a "sudo" on the front of whatever you're doing, but if you're doing multiple things, then it's more efficient to use the "sudo su"?

---

### Post by Nonno Bassotto on 2007-06-14
I guess in general it is safer to use sudo. After the first time it will not ask your password again for 15 minutes, so it is not that annoying.

---

### Post by greg_g on 2007-07-04
The reason why ctrl-c is not copy in terminals is because ctrl-c is the default key choice to end a process.  So if a process was "hung" you can ctrl-c and it will be killed.  If you are changing the keybindings, be sure to make a substitute for the ctrl-c option in case you need it.

Just a warning.

---

### Post by Irony on 2007-07-10
The latest version of tile is here;

[http://ftp.unixdev.net/pub/debian-udev/pool/main/t/tile/](http://ftp.unixdev.net/pub/debian-udev/pool/main/t/tile/)

Download the tile_0.7.4_i386.deb and install it by double clicking on it.

Now go to;

[PHP]/usr/share/applications[/PHP]

Scroll down to;

[PHP]Tile Windows Horizontally
Tile Windows Vertically[/PHP]

Drag them to your desktop or to your panel. Open a couple of windows and test the tile program by clicking the tile icons.

Now right click on the tile icons and choose Properties. Click the No Icon symbol and link to your prepared vertical and horizontal pictures.

Go to;
[PHP]
/usr/share/tile[/PHP]

Open wmprofiles with sudo.

I changed the line;

[PHP]Gnome2 0 0 36 0[/PHP]

to;
[PHP]
Gnome2 0 0 00 0[/PHP]

Which allows full screen tiling because my menus are on autohide.

---

### Post by Irony on 2007-07-11
This thread should be moved to the Tutorials & Tips section.

---

### Post by olejorgen on 2007-08-10
Thanks for the quide. i rememeber I tried tile once, but I didn't do anything with the config files. It completely screwed my windows and panels, so I removed it again.

Isn't there som kind of extension to gnome that give you the (MS) Windows behavior? (Shift/Ctrl click the "tabs" you want tiled and right click, then select vertical / horizontal)

When we are on the topic of silly things that is difficult to archieve: Is there any way to reorder the "tabs" in the taskbar?

In windows of course, this is mostly useless because so many programs use MDI with "fake tabs". (Like acrobat reader and exel. Well acroreader 8 has actually fixed this)

---

### Post by ecschiel on 2008-04-23
> **Nonno Bassotto said:**
> Just a little thing: if you want you can condense step 4 to 6 in
```

sudo gedit /usr/share/tile/rc

```

And you can change the terminal settings, so that copy/paste is ctrl c/v, under edit->current profile. I don't know why it has this strange default.

The default is Ctrl+Shift+C because Ctrl+C is SIGINT (the signal u use to interrupt processes) So, i wouldn't advice changin those. Use default or MMB.
I hope this helps

---

### Post by olejorgen on 2008-04-24
My solution was to use a real WM. Ion in my case, but I'm sure wmii, awesome and xmonad are ok too

---

