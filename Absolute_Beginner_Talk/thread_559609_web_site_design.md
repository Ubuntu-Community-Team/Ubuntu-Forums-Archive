---
title: "web site design"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by ROJIRU on 2007-09-25
My question was to have been : Can I use ubuntu to design my own web site. But the thread titles show that it is possible. However I've been doing a college course using Dreamweaver. So my questions are how do I do it in Ubuntu and are there any packages that will help a computer ignoramous like myself. Thanking you all in anticipation. Rojiru

---

### Post by guymclaren on 2007-09-25
start by learning HTML, dreamweaver sucks.

where do you want to host the site? on your own server?

then you will need to install apache.

---

### Post by dptxp on 2007-09-25
Kompozer - Wysiwyg editor
Bluefish - Available in Add/Remove
Amaya - Advanced one, great but tough as per reviews.

---

### Post by LaRoza on 2007-09-25
> **ROJIRU said:**
> My question was to have been : Can I use ubuntu to design my own web site. But the thread titles show that it is possible. However I've been doing a college course using Dreamweaver. So my questions are how do I do it in Ubuntu and are there any packages that will help a computer ignoramous like myself. Thanking you all in anticipation. Rojiru

Yes, you can use Ubuntu, all you need is a text editor and a browser.

If you want a server, use Apache2:

```

sudo tasksel

```

Select "LAMPP"

Don't use WYSIWYG editors if you are interested in Web design.

Also, you might want to get a Windows machine for testing purposes, test your site in:
* IE (6-7)
* FF (1.5-2.x)
* Opera (9.10 - 9.2)
* Safari (Use the Windows version, also, Konqueror will be just as good)
* Lynx (This is how screen readers and search engines will see your site also)

IE is usually the trouble maker, IE6 is the worst.

---

### Post by erosion on 2008-01-25
> **LaRoza said:**
> Yes, you can use Ubuntu, all you need is a text editor and a browser.

If you want a server, use Apache2:

Don't use WYSIWYG editors if you are interested in Web design.



How can u justify saying that? 
In dreamweaver you can use both code or design mode:confused:
10+ years ago i used to do all my HTML in notepad.
I belive that they are four types of users mac users, unix heads, windows victims.and linux dev heads.  lol
unbuntu server is the best! the last time i installed LAMPP it was so difficult doing all the config' Unbuntu server does it all for you. Very Nice and it makes me very happy.

---

### Post by gvartser on 2008-01-25
wine + dreamweaver

[http://www.frankscorner.org/index.php?p=webdesign](http://www.frankscorner.org/index.php?p=webdesign)


/g

---

### Post by JC Cheloven on 2008-01-26
Hi, you may find useful my recent experiences:

1) AMAYA:
As to the advertisements, one thinks it's to be a fantastic web authoring program. But I think it's simply a mess at the moment. I tried to install it in two computers, and none succeded. In one, on Xfce-Ubuntu, Amaya seems to install but doesn't run: when clicking on Applications->Network->Amaya nothing happens (and no process is launched). On the other computer, with Gnome-Ubuntu, things are worse: Amaya starts but system hangs in a little while. I tried also the newer version 9.55 (not in the repository), with similar results.
Also it poorly uninstalls: The menu entry remains after uninstalling, in both my computers

2) Compozer:
It's a nice web authoring program, although it's not "polished" to a professional degree at the moment, as the author says. I've heard that it compares well with dreamweaver but I'm not sure, as I  never used it.  I hope you'll find compozer useful.

Note.- If you are specially interested in keeping the format of your html code, you may find compozer unconvenient, as it reformats the code to long lines, mostly unreadable in external text editors. Seems to be a bug to be fixed in next releases. As for me, compozer does just well, as I'm not interested in how the (x)html is formmated (sorry to the supporters of the "pure html" argument), although I found useful some reading on xhtml and css sheets. 

Greetings
JC

---

### Post by LaRoza on 2008-01-26
> **erosion said:**
> How can u justify saying that? 
In dreamweaver you can use both code or design mode:confused:


* I never saw generator code from a WYSIWYG editor that was worth using, and almost never valid

* If it is not generating code, it isn't a WYSIWYG editor

* If you are only testing in one rendering app, on one platfrom, you are not a good web developer

---

### Post by PeterJS on 2008-01-26
I a saw suggestion above to learn HTML and code the whole things by hand. If you're going to look in to going that route, I'd suggest going all out and learn PHP along with it, there's not that much more to learn, and the power differential between what you can do in PHP+HTML versus just HTML is huge. And if you learn a bit of PHP it'll make molding an existing frame work to your needs a lot easier.

And if I may be so bold as to plug a specific framework, take a look at  [Drupal](http://drupal.org/)

And please for the sake of the net, what ever you pick make sure it validates.

---

### Post by Dr Small on 2008-01-26
> **PeterJS said:**
> I a saw suggestion above to learn HTML and code the whole things by hand. If you're going to look in to going that route, I'd suggest going all out and learn PHP along with it, there's not that much more to learn, and the power differential between what you can do in PHP+HTML versus just HTML is huge. And if you learn a bit of PHP it'll make molding an existing frame work to your needs a lot easier.

And if I may be so bold as to plug a specific framework, take a look at  [Drupal](http://drupal.org/)

And please for the sake of the net, what ever you pick make sure it validates.
+1
I completely agree.
If you're going to learn HTML, tack Php on along with it. It's not much harder ;)

---

