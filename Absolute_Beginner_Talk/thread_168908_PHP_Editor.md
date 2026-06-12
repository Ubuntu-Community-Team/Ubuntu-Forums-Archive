---
title: "PHP Editor"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-05-01
I am a web developer. In windows I used to use Ultra-Edit . and I love it. is there anything similar to it that works on ubuntu?

Thanks

---

### Post by zerhacke on 2006-05-01
Gedit does syntax highlighting on PHP files.

---

### Post by Isoss on 2006-05-01
Actually, I think it's good, but, I also work with SQL syntaxes ... sometimes they are hundreds. let's say I need to edit the table name at once, that will need a colomn select .. does gedit have this kinda selection mode?

---

### Post by zerhacke on 2006-05-01
Not that I know of, but there's a (slower) workaround.  Type out what you want to replace with, highlight it, and hit control X.  Then use FIND in the edit(?) menu, type in what you want to replace, and each time it finds what you want to replace you hit control V.

Slower, but the effect is the same.  Maybe someone else knows a better route to take.

---

### Post by NoWhereMan on 2006-05-01
I don't know but jedit for me is really one of the best editors.

add the following lines to your /etc/apt/sources.list:

deb [http://dl.sourceforge.net/sourceforge/jedit](http://dl.sourceforge.net/sourceforge/jedit) ./
deb-src [http://dl.sourceforge.net/sourceforge/jedit](http://dl.sourceforge.net/sourceforge/jedit) ./

[http://jedit.org/index.php?page=download](http://jedit.org/index.php?page=download)

---

### Post by gingermark on 2006-05-01
Which version of Ultra-Edit do you have?

I just had a quick look, and you might be able to run it with WINE (which allows SOME Windows applications to run in Linux).

EDIT: I am not a web developer, but is [Quanta Plus](http://quanta.kdewebdev.org/) the sort of thing you are looking for?
Here is a screenshot of the PHP editing bit:

---

### Post by Isoss on 2006-05-01
I'll try to install it with wine.

---

### Post by jazzmuzik on 2006-05-01
From what I've read, nothing in Linux compares with UltraEdit. Some folks have been using it for a decade.

I would suggest trying to run UE in wine.

Also, Bluefish will syntax hightlight php and html. It has an opton to insert a few sql commands, so maybe it can highlight that as well.

---

### Post by gingermark on 2006-05-01
[QUOTE=Isoss]I'll try to install it with wine.[/QUOTE]
OK, well apparently versions 12.00 and 10.10a apparently work reasonably. Unfortunately there isn't a lot of info on it, but have a look [here](http://appdb.winehq.org/appview.php?appId=65) before you try in case your version is one that doesn't work.

---

### Post by Borniet on 2006-05-02
I mostly use Kdevelop (Kubuntu) for my PHP, HTML and CSS, and am very pleased with it. For my SQL stuff on MySQL I used Knoda, MySQL Administrator and MySQL Query Browser.

---

### Post by byenary on 2006-05-02
bluefish

---

### Post by Raavea on 2006-05-02
Well I've been pretty lazy recently but I have done some stuff in Screem, which I quite enjoy. I took a look at gPHPedit, but I hated it.

I used to use Notepad2 and occasionally CSEHtml Validator Lite on XP...

---

### Post by ComplexNumber on 2006-05-02
[quote=Isoss]I am a web developer. In windows I used to use Ultra-Edit . and I love it. is there anything similar to it that works on ubuntu?

Thanks[/quote] 
try gphedit. [click]("http://www.gphpedit.org/features.phtml"). or you could try Tulip. [click]("http://tulip.solis.coop.br/us/index.php"). 
i think gphpedit is available in the ubuntu repositories. they're both said to be really good.

---

### Post by Isoss on 2006-05-02
I installed Ultra-Edit with wine but it SUCKS ... I didn't like it, besides it prompts a lotta errors.

I Got blue Fish .. I like it, but I couldn't find anything that is similar to the colomn select that ultra-edit has.

I tried gPHPedit and I didn't like it .. I couldn't download Screem or Tulip ... but I'll try to ... but before I do that I hope that someone knows what I'm searching for and maybe would suggest something.

Thanks.

---

### Post by DirtDawg on 2006-05-02
[Cream]("http://cream.sourceforge.net/index.html") has column select, but I've, er, never used it. I always wondered what it was for.

---

### Post by pannet1 on 2006-05-03
hello guys,

i am new to ubuntu but i have tried trustudio an eclipse plugin. its great for php and eclipse works well for windows as well as linux. its little bit slow but clearly great free tool.

of course one have to seperate the html from php code.

pls let me know if someone is really benefited from this info.

best regards
b karthick

---

### Post by andyjeffries on 2006-06-29
Just to be an awkward bugger, when you guys write things like "I tried gPHPEdit but I hated it", I don't take it all personally but I would like to know what you actually hate so I can consider fixing it :-)

---

### Post by Isoss on 2006-06-29
After all I could get ultraedit to work without any error ... but cream is just much better cuz it can read arabic by selecing the encoding which wasn't an option in ultraedit. Cream is Just what I need. Thanks.

---

### Post by D-- on 2007-03-08
> **andyjeffries said:**
> Just to be an awkward bugger, when you guys write things like "I tried gPHPEdit but I hated it", I don't take it all personally but I would like to know what you actually hate so I can consider fixing it :-)

Edited: (I took a new look at gPHPedit)

OK, sorry for some of my previous comments. It had been a while.

Here's how gPHPedit could be better.

1. Add a way to execute the script, not only check syntax. F5 would be a great way to do this. Syntax check is nice, but a way to actually test my code is kind of necessary.

2. The class browser is not very good. In fact, it's almost kind of bad. I have several files with classes that do not show in the browser. Then I change to a folder and open a file. Instantly, the classes from that file and every other file appear in my class browser. What? It didn't even include those files, it just scanned the whole folder. It also does not update live--if I delete any methods, no changes are reflected. I'm guessing this is some ctags ugliness?

My preference would be the class browser to only show classes in the current file. I would also like it to show define() and include() statements, because locating this is equally important.

3. More advanced colorization options, please. I finally found how the colorization works, and it's kind of uninspired. Personally, I have no need of most of the SQL and HTML stuff. It's cluttering the menu. A way to shut it off would be nice, or else multiple dropdowns for each kind of code that can be mixed together. I would like to see PHP's function coloring brought up to speed with the new functions in 5.2.0.

Ideally, I would like to see an XML file users can edit to configure color options in a way similar to gtksourceview's .lang files. I previously made a .lang file for PHP to let me color every group of functions differently, this way I can flag anything not included in default distributions. It also lets me keep the function names updated for each PHP release. This would also ensure a way to keep gPHPedit current even when you're not putting out new versions.

4. Similarly, an XML way to add things for function completion would rock all. I love your little prompter, but there's some new stuff not in the latest release. Also, a way to link this to a search in the CHM PHP manual using gnochm would be equally lovely.

5. A file browser pane for managing multiple projects. Class manager is great, but I'd love to have some way to view my folder structure because I break up my projects in more than one file, and the tabs don't cut it--neither does scanning random folders for classes.

(Sorry to ressurect this thread. I found it searching for info on eclipse and trustudio, but when I saw the gPHPEdit author was here I wanted to leave my input.)

On a poitive note, your editor is much nicer than TruStudio. TruStudio is pretty, but for projects that don't involve SQL (like those of use who use PHP for CLI applications and GTK2) it's a mess. It flags virtually everything as being undefined just because it relies on an outside library.


Edit 2: I just added a file I sent the gPHPedit author. It contains an updated php-gphpedit.api to drop in /usr/share/gphpedit/ and update all the function descriptions for PHP 5.2.1. Also contains the script I wrote to rip it all from the PHP manual. Figured it's relevant to the thread.

---

### Post by zilverdistel on 2008-07-21
geany is really slick to me ...  it's gtk and features are actually configurable :guitar:

It's in the hardy repository, but a newer version can be obtained on debnet ([geany on debnet]("http://getdeb.net/search.php?keywords=geany"))

---

