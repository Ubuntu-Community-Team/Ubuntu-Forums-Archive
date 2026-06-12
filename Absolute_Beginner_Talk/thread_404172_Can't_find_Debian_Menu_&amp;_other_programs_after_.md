---
title: "Can't find Debian Menu &amp; other programs after installation"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by HokkaidoHillbilly on 2007-04-08
Hi all,

After installing Automatix2, I decided that I wanted the Debian Menu (menu-xdg, I think it is), so clicked on it, hit start, it installed, and I'm good...or so I thought.

The problem is that the "Debian Menu" folder isn't under Applications->Accessories like it should be.  

After poking around a bit and hearing people bitch at newbies for using Automatix, I deleted it tried to install menu-xdg via Synaptic.  Found the package, installed, and everything's coming up roses...or so I thought, once again.

The thing is that menu-xdg isn't the only MIA package.  Other things like 3D chess installed from Synaptic aren't anywhere to be found either.  BTW, according to both Synaptic and Add/Remove, all these programs have been installed and can be uninstalled, but no matter how many times I reinstall them, no dice.

Any ideas?

Thanks in advance,



Hokkaido Hillbilly :)

---

### Post by LaurelLynn on 2007-04-08
Dear HokkaidoHillbilly,

Konnichi wa, mondai wa...

Forgive me for using english, my nihongo wa chooto.

The Debian directory is not shown by default.  To display it right click on Applications on the top Panel bar.  Pick the option that says edit menus. Click on the Applications listing on the left pane.  Debian will appear with a square checkbox in the right pane.  Click on the checkbox to add it to the menu.

Then click on the Debian entry in the left pane, and select any Debian aps you have installed.

Laurel Lynn

---

### Post by HokkaidoHillbilly on 2007-04-08
Hi ya, LaurelLynn, and thanks for the quick reply.

No worries about &#26085;&#26412;&#35486; *grin*  I'm actually an American, but I've lived in Hokkaido for the past 7 years.

Anyhoo, little problem.  I can see the Debian Menu icon and the box after right clicking the Applications menu, etc, but it won't let me click the check box for some reason.  Any ideas?

Cheers!

HH ;)

---

### Post by LaurelLynn on 2007-04-08
One Idea,

Debian appears in two places.  One is in the left hand pane **under** Applications.  That one controls what is and isn´t displayed in the Debian Menu. But, before if will work, you have to enable the Debian Menu.

That is a right pane option only seen after selecting Applications in the left pane. After clicking on Applications you should see the Debian entry appear on the right.  NOW you can go to the left pane Debian to enable programs.

I know all the left pane, right pane stuff is as confusing as a blind man watching a ping-pong match, but it is hard to discribe GUIs in text.

Laurel Lynn

---

### Post by Famicommie on 2007-04-08
For the programs you can't find:

Open up Synaptic, locate the package you installed, right click on it, select properties, tab to "Installed Files", and look for an entry like

/usr/bin/3dchess

3dchess is the command you would use from the terminal to open up 3dchess in that example. I'm just guessing at the name, but it will be /usr/bin/something

You can make a menu entry for it so that you don't have to open a terminal every time you want to run that program.

---

### Post by HokkaidoHillbilly on 2007-04-08
Yeah, I understand completely what you're talking about w/ the left/right panes, but I still get no love.  I've even uninstalled menu-xdg via both automatix & Synaptic (which was kinda odd, seeing as I uninstalled in one and it was still listed as installed in the other) then reinstalled, but no love.

Any ideas?

And where'd you learn Japanese?  Have you lived on this side of the pond?

---

### Post by LaurelLynn on 2007-04-08
Watashi wa Ni kagetsu no homu stay shimashita. Kanazawa no gaku ni benkyoo shimashita.  Demo, Hokkaido ni itta koto arimasen deshita. Gommen nasai.

One last idea, the edit menu in Synaptic has an option to fix broken packages.

Laurel Lynn

---

### Post by HokkaidoHillbilly on 2007-04-08
Yeah, tried that too, and unfortunately, nothing's really working.  In fact, I can't even edit the menu anymore in menu layout, i.e. even though I know the path for 3D Chess, for example, nothing happens when I add a new item. *sigh*

---

### Post by HokkaidoHillbilly on 2007-04-08
Oh yeah...Kanazawa and the whole Noto peninsula are one of my favorite places in Japan.  Ever get out to Wajima?  I camped there when I drove from Hokkaido to Kyoto over Golden Week a few years ago.

---

### Post by LaurelLynn on 2007-04-08
Is it too late to hope that you made backups before you started the original install?

I´m not sure what is causing the original problem, but if trying to fix it is causing other thinks to break. I would immediately stop and backup all my personal files (preferredly the whole system) before proceeding. It is just that the more years I spend working with computers, the more paranoid  I become.

Laurel Lynn

---

### Post by rajeev1204 on 2007-04-08
hi

this is a recently confirmed  bug in the alacarte menu editor for feisty atleast

Check out bug number 97460 . [https://bugs.launchpad.net/bugs/97460](https://bugs.launchpad.net/bugs/97460)
 I believe u are using feisty .Maybe it is for edgy also.

What happens is that some files in home directory required by menu editor end up being owned by root after an update i suppose,

 I just changed ownership of those files to myself from root .

Under hidden files in home have a look at .local/share/apps and .config/menus

they are probably owned by root .Changing them to user solves the problem


regards

rajeev

---

### Post by Famicommie on 2007-04-08
To elaborate on rajeev's post:

Open up a terminal. Enter the commands one line at a time in the following order:
```
sudo chown <user> ~/.local/share/applications
sudo chown <user> ~/.config/menus

```

Obviously, you need to replace <user> with your own username. My user name is fami, so I enter "sudo chown fami ~/.local/share/applications". chown is the command that changes ownership of a file.

Also, -I- think that Automatix is a wonderful program for newbies. Azureus works much better when installed via Automatix (for me at least), all of the codecs I wanted were a breeze to get, etc.

---

### Post by rajeev1204 on 2007-04-08
Thats right fami .. Thanks for those commands . Sure makes it faster .

And i agree . this problem has nothing to do with automatix .

Automatix is great for a newbie  . Especially for a 64 bit user .Nothing comes close

---

### Post by HokkaidoHillbilly on 2007-04-08
Sweet!  Thanks for the info, guys!

I'll make sure to try out those terminal commands next time I'm in Ubuntu (had to use XP for something else right now).

Also, I'm not using Fiesty.  I've got Edgy, i.e. 6.10.  Heard that it still has some bugs when installed on a Dell XPS M1210, so I decided to go w/ the stable release for now.

I'll let ya know how it goes!

---

### Post by HokkaidoHillbilly on 2007-04-16
Wow...time sure does fly when you have to re-install Edgy like 5 or 6 times. *grin*

Anyhoo, finally got everything set up and working like it should, so thanks!

---

