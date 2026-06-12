---
title: "Desperate look foor a good php editor"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by PingunZ on 2006-07-10
I'm learning php and I dont want a retared editor like bluefish that only highlights half of my tags
I tried :: gedit, emacs, nvu, jedit, bluefish, screem, gphpedit, ...
the one I preferred most was gphpedit ...
but its still not really what I'm looking for
What I'm looking for is ::
:: syntax highlighting ( difficult to write that :) ) with customizable colors
:: I dont want this line in the middle of the screen 
 a very simple look so no hundreds of toolbars
something like gedit with decent highlighting ...

Anyone got a solution ?

Grtz PingunZ

---

### Post by annda on 2006-07-10
i like kate (and i run it under gnome, although it's a kde editor).

the only problem i've had (for some time now actually) is buggy auto indentation - it seems to switch all the time to xml mode and for some reason indents too eagerly and too much.

syntax highlighting is really good and i like the autocompletion plugin, so it remembers my function and variable names. not perfect but nice. give it a try.

---

### Post by tribaal on 2006-07-10
Hum I know you already tried, but I use gedit.

My very first reaction when I lauched it to code some php was something like "eeeeeeerk...". I agree, synthax highlighting (you're right, difficult to write ;) ) is really ugly by default. But once I tweaked it a little bit it works wonders.

Maybe you should try fiddling around with the colors a little? It really did everything for me.

Here's my config file for PHP highlighting, maybe it'll give you ideas...

```
<?xml version="1.0"?>
<gconf>
        <entry name="Variable" mtime="1150103693" type="string">
                <stringvalue>2/#6e6c6d74f1c6/#000000000000/0/1/0/0</stringvalue>
        </entry>
        <entry name="Bash@32@Line@32@Comment" mtime="1150103655" type="string">
                <stringvalue>2/#0909ffff0000/#000000000000/0/0/0/0</stringvalue>
        </entry>
        <entry name="C@43@@43@@32@Line@32@Comment" mtime="1150103651" type="string">
                <stringvalue>2/#0909ffff0000/#000000000000/0/0/0/0</stringvalue>
        </entry>
        <entry name="C@32@Block@32@Comment" mtime="1150103647" type="string">
                <stringvalue>2/#0909ffff0000/#000000000000/0/0/0/0</stringvalue>
        </entry>
        <entry name="HTML@32@Block" mtime="1150103598" type="string">
                <stringvalue>2/#2e2e8b8b5757/#000000000000/0/0/0/0</stringvalue>
        </entry>
</gconf>

```

(to "install" just put the file in ~/.gconf/apps/gedit-2/preferences/syntax_highlighting/PHP )

Hope you'll find your grail, mate ;)

- trib'

PS: Somebody PM me to explain how you make a textbox of a fixed height with a scrollbar in theses forums please :(

---

### Post by Kilz on 2006-07-10
I love screem for editing php. Its in synaptic, or 
```
sudo apt-get install screem
``` will install it. It dose take a few days to grow on you.

---

### Post by brentoboy on 2006-07-10
use kdevelop

I just pulled up one of my php files in it, and the highlighting looks good.

---

### Post by tribaal on 2006-07-10
Man, you really made my day (well, night :)).

I'm apt-getting it right now, it looks so sweet. :)
Forget my bloody syntax highlighting file, go for screem ;)

Cheers

- trib'

---

### Post by PingunZ on 2006-07-10
Well I opened my .php files in it and its the best till now ( screem ;) )
but I'm sure there are better editors :p

Grtz PingunZ

---

### Post by PingunZ on 2006-07-11
Screem ftw :)
When you remove all the bars and edit the colors its really nice 
but only one question left, how do I remove the gray bar in the middle ?

Grtz PingunZ

---

### Post by andyjeffries on 2006-07-11
> **PingunZ said:**
> Screem ftw :)
When you remove all the bars and edit the colors its really nice 
but only one question left, how do I remove the gray bar in the middle ?

Grtz PingunZ

Hi PingunZ, what was wrong with gPHPEdit?

The latest version is very stable: [.deb in this thread]("http://www.ubuntuforums.org/showthread.php?t=190399&page=2&highlight=gphpedit")

The grey line at 80 chars can be removed using Edit|Preferences|Show Right Hand Edge Guide

Cheers,


Andy

---

### Post by Tanjerine on 2006-07-11
i've been a loyal jEdit user for a few years but recently, I've noticed that it's been getting really slow on my machine (for whatever reason, but recently, its been due to the number of files i have open in it.) 

anyway, i'm glad i found this thread. will try out a bunch of the editors suggested and see which one i like more. will try to give feedback. :cool:

---

### Post by andyjeffries on 2006-07-11
> **Tanjerine said:**
> i've been a loyal jEdit user for a few years but recently, I've noticed that it's been getting really slow on my machine (for whatever reason, but recently, its been due to the number of files i have open in it.) 

anyway, i'm glad i found this thread. will try out a bunch of the editors suggested and see which one i like more. will try to give feedback. :cool:

Good man.  Most free software authors love giving software away for free, but it's a bit depressing when you read people saying "I don't like {your-software} so I'll use something else" without saying what they don't like or why it was a bad experience for them.

To be honest, I wrote my editor to scratch my itch and most of the features in there are because I'd use them - but I've made lots of tweaks to it that other people have asked for.

---

### Post by PingunZ on 2006-07-11
gphpedit :: check syntaxes ==> crash :D

Its the second best till now ..
1) screem
2) gphpedit
3) kate

---

### Post by andyjeffries on 2006-07-11
> **PingunZ said:**
> gphpedit :: check syntaxes ==> crash :D

Its the second best till now ..
1) screem
2) gphpedit
3) kate

Can you try gphpedit's latest version (either compile from source from [www.gphepdit.org](www.gphepdit.org) use the deb [here]("http://www.ifokkema.nl/gphpedit-0.9.91_0.9.91-1_i386.deb").

I use it for 14+ hours per day and it doesn't crash on a syntax check here (I'm using the PHP5 CLI binary).

---

### Post by damianubuntu on 2006-07-11
I used to use SCITE, mainly in Windows, and some in Breezy and found it quite good, but recently it seems to be so slow, and crash a bit under dapper, so I'm pleased to read this thread.  Anyone have any comments on SCITE?

---

### Post by Bagnaj97 on 2006-07-11
I use Quanta+ for my php/(x)html/css stuff

---

### Post by sitara on 2006-07-11
Quanta Plus works for me too.

---

### Post by faswad on 2006-07-11
> **Bagnaj97 said:**
> I use Quanta+ for my php/(x)html/css stuff

I would have to agree. Quanta+ is by far the best PHP editor i've used.

---

### Post by Tanjerine on 2006-07-12
> **damianubuntu said:**
> I used to use SCITE, mainly in Windows, and some in Breezy and found it quite good, but recently it seems to be so slow, and crash a bit under dapper, so I'm pleased to read this thread.  Anyone have any comments on SCITE?

Tried it for a bit, but found it a bit of a pain to configure and couldnt, or maybe didnt have the patience to, look for proper documentation on it. Usually, with editors, I would like to be able to configure them by going to the preference/settings menu and clicking on the stuff i would like to change. And i just couldnt figure it out this morning. Will try it again tomorrow.

---

### Post by Tanjerine on 2006-07-12
> **andyjeffries said:**
> Good man.  Most free software authors love giving software away for free, but it's a bit depressing when you read people saying "I don't like {your-software} so I'll use something else" without saying what they don't like or why it was a bad experience for them.

To be honest, I wrote my editor to scratch my itch and most of the features in there are because I'd use them - but I've made lots of tweaks to it that other people have asked for.

So far so good with gPHPEdit. I'm still trying it out (as in, while i am replying to this) and i like what i see, though i would love to see an easier way of changing the background/foreground colors. But it's really just a matter of getting used to something, i suppose. Will let you know if I find any "deal breakers" for me.

---

### Post by mech7 on 2006-07-12
Can any of these editors hold up against ZEND Studio or PHPED ?

---

### Post by MrHorus on 2006-07-12
> **mech7 said:**
> Can any of these editors hold up against ZEND Studio or PHPED ?

I would recommend Zend hands down any day.
Sure it's not free nor is it open source but it is an absolute bargain at $100 for a personal lscence.

---

### Post by OrganicPanda on 2006-07-12
well i find most of them are ok but none really stand out as special, the only one i will give extra credit to is quanta+ because it highlights both php and html when they are used in the same document which is very helpfull, pitty its a kde app which doesn't look so hot in gnome plus my network locations aren't set in kde so i have no ftp there.

gphpedit kept crashing while opening documents from ftp so thats no good to me

my favourite all round so far is screem but i cant get it to highlight html and php in the same document

well theres my 2 cents

---

### Post by mech7 on 2006-07-12
Yeah I really like Zend too.. but I was hoping that perhaps there was a free opensource version like Zend which has all the same cool features ^_^ 

> **MrHorus said:**
> I would recommend Zend hands down any day.
Sure it's not free nor is it open source but it is an absolute bargain at $100 for a personal lscence.

---

### Post by altonbr on 2006-10-02
I don't know what you guys are talking about because gEdit and Screem both do not allow multiple lines of indenting or highlighting $variables inside print("$statements");

I was a notepad++ man when I was using Windows

---

### Post by leinuz.basher on 2007-07-27
Try Using Bluefish it works great with php/javascript/css/(x)html/xml and PL's

---

### Post by Pitt Stains on 2007-08-04
Screem looks ok to me so far, but I am having a hard time figuring out how to connect to my remote site.  I am used to Dreamweaver in Windoze, where I can view local files and remote files side by side.  Screem either doesn't do anything like this or I haven't been able to figure it out.  Anyone have any luck with this?

---

### Post by altonbr on 2007-08-28
gEdit in Gusty is now so stacked full of goodies, I'd have to recommend it whole-heartedly come it's stable release in October!

[http://ubuntuforums.org/showthread.php?p=3269797](http://ubuntuforums.org/showthread.php?p=3269797)

---

### Post by Tips on 2007-10-30
> I'm learning php and I dont want a retared editor like bluefish

Try gvim -- it's well worth the effort learning it.  Once you learn the commands it is very fast and efficient.

---

### Post by Hopworks on 2007-10-30
I like SciTE myself, for editing almost any language script. I have used DreamWeaver also, but I don't like the load time in Winblows.

One thing I haven't found is a way to test a PHP script using an immediate window like using VBA in Micro$oft office, with variable watches, break points, etc. I probably just missed something while looking for an IDE, or not exploring all the possibilities with sciTE. Right now, I just code more carefully, and when I save it, it's on my LAMP server. After that, it's a matter of refreshing my browser that is pointed to that script. I just got use to it.

---

### Post by Incense on 2007-10-30
> **Bagnaj97 said:**
> I use Quanta+ for my php/(x)html/css stuff

+1

---

### Post by Tips on 2007-10-30
Doesn't PHP eclipse have those break point features?  I think it might...

---

### Post by sevenearths on 2008-03-22
I like the layout of Eric, its just a pity that it only doesn't ruby and python. No PHP :(

..

you might want to check out this [link]("http://midnighthax.com/phpeditors.php") for some decent php editors

---

### Post by Dusal on 2008-05-07
How is Quanta?
I'm trying linux my first time by ubuntu. I like it :guitar: I using dreamweaver until now. Just now I trying to use quanta. It's very simple and I like it :lolflag:

---

### Post by tomchuk on 2008-05-08
Komodo hasn't been mentioned here and is a very powerful PHP/Perl/Python IDE. It has integrated debugging for those languages and a firefox plugin for JS debugging. Though I have to say that because the debugger for php runs over xdebug, it is not nearly as interactive as debuggers for other languages/platforms, and stepping through code can get a little tiresome. Generally I can get to the root of the problem quicker with some print_r's than I can by using the debugger.

I dropped the $300 on Komodo, but have gone back to Vi for everything but debugging when I need it. I get everything I need out of an editor and I don't need to change the way I work if I'm working locally or remotely on a server. Although I have to hand it to Komodo, their Vi keybindings are spot on. Also, I generally prefer to fill my screen with a bunch of terminals running Vi, mysql, etc. than to do everything though a tabbed IDE with debug panes, file and class browsers, menu bars and all that stuff that gets in the way.

All the developers I worked with at my last job came on board using Zend, Komodo, Notepad++ and TextMate on Windows and Mac. When I left a couple months ago, they were all converted CLI nuts using Ubuntu and Vi ;) Just like the command line, there is a steep learning curve in mastering vi or emacs, but the investment in time you put into learning a powerful tool will be repaid tenfold in productivity.

---

### Post by Incense on 2008-05-10
> **Dusal said:**
> How is Quanta?
I'm trying linux my first time by ubuntu. I like it :guitar: I using dreamweaver until now. Just now I trying to use quanta. It's very simple and I like it :lolflag:

I really dig quanta. I spend way too much time in it these days, but it does what I need it to do beautifully. I'm temped to try out the CLI VI stuff though...

---

### Post by kkathman on 2008-06-15
If you are into using k-applications in your gnome install, the best php editor I have seen in the linux community is Quanta plus.  Its available in the repos I believe for almost every version of *buntu.

As for gnome, gedit with its editor tweaks (well documented in the web) is very good.  

Cheers!

---

### Post by Tips on 2008-06-15
> **kkathman said:**
> If you are into using k-applications in your gnome install, the best php editor I have seen in the linux community is Quanta plus.  Its available in the repos I believe for almost every version of *buntu.

I like Quanta+ also.  I'm not sure if it was mentioned already, but there is a [list of Linux editors and Web development tools]("http://tips.webdesign10.com/using-linux-for-web-design-and-development-ubuntu") on my site.  (probably needs updating)

I've tried them all but settled on Gvim because it's the fastest to work with and it's easy to use for other tasks also, like integrating with Firefox with the [It's All Text extension]("http://tips.webdesign10.com/forums/f73/its-all-text-firefox-extension-296.html").

---

### Post by zabaksmers17 on 2008-06-20
> **Tips said:**
> Doesn't PHP eclipse have those break point features?  I think it might...

I agree that Eclipse has more features than every other editor. And it is a powerful tool for every language: c++, java, php. All you have to do is install the appropriate plugins.

And it's freeware!

The downside: yes, it needs a lot of cpu and memory resources :)

To get it, start here: [http://www.eclipse.org/pdt/](http://www.eclipse.org/pdt/)

---

