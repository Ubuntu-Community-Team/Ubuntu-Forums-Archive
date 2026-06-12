---
title: "The best linux web-design application"
date: 2011-02-10
forum: Art &amp; Design
---

### Post by Dry Lips on 2011-02-10
Now, I'm a graphic designer who eventually wants
to get into doing some basic web-design as well 
(self promotion and non-profit work). I need your 
opinion about which web-editor you think is the 
best for Linux... Seamonkey, Bluefish or some other
editor? Should WYSIWYG capabilities be considered 
a must when choosing a package to learn from 
scratch? And finally; how essential is  WYSIWYG when
it comes to creating a good workflow from a *designers* 
point of view?

---

### Post by BcRich on 2011-02-11
Hi
I use seamonkey
but Kompozer also seems to be popular [http://kompozer.sourceforge.net/](http://kompozer.sourceforge.net/) it has a built-in site manager.
wysiwig makes learning basics of webdesign easy and many front-end web designers stick with it. it really depends on which field of web design you are interested in, if you r a designer i'm guessing you might be more interested in developing the general "look and feel" of a website? if that is the case, wysiwig editors should do the trick for you, but it's always a good idea to check out the code (html, css, xml, etc) that goes on in the background (but not a necessity or a prerequisite for website designers).
gimp's script-fu slice and imageMap filter/plugin adds some imageready/fireworks slicing and hotspot capabilities to a workflow. i find the slice feature to be particularly useful as it also creates a table for the images it slices in html, which you can then easily embed into a web page.
either way starting in wysiwig editors and tools is a good place to start (and even remain) but you should definitely consider extending your knowledge beyond that if you don't want to have your software make your design decisions for you in the long run.

---

### Post by Dry Lips on 2011-02-11
Thank you for a thoughtful response!
 
You write: 

> “if you r a designer i'm guessing you might 
be more interested in developing the general "look 
and feel" of a website?” That's right, I'm not at all opposed to learning a bit of 
html, but my main concern is to find a way to visualise 
my ideas, not going too deep into the code that's required. 
 
 > gimp's script-fu slice and imageMap filter/plugin
adds some imageready/fireworks slicing and hotspot 
capabilities to a workflow. i find the slice feature to be
particularly useful as it also creates a table for the 
images it slices in html, which you can then easily embed
into a web page.   Interesting! Thanks for the tip! 
I'm new to Ubuntu and open-source software in general. I'm 
used to working with adobe software (although not for web-design), 
but Gimp seems very solid, when you take into consideration
 that it's completely free. It seems as if Inkscape 
(and possibly Scribus, but I haven't really used it much) 
is more immature at the present moment, but given time,
they too can become very good. (One example: It seems 
as if Inkscape has a little trouble working with high-res images...)
 
I've tried Kompozer, wasn't too impressed at first sight... 
I'll definitively try out Seamonkey. (And hey; I like the mozilla guys!)

---

### Post by xtremethegreat1 on 2011-02-12
Try out bluefish. That's what I use both for HTML and PHP development.

sudo apt-get install bluefish

And about the WYSIWYG, I think it is a **must not** when starting to learn from scratch. But if total control is not what you're looking for, then WYSIWYG is for you. Good luck.

---

### Post by Dry Lips on 2011-02-15
I've installed and have briefly tried out both Bluefish
and Seamonkey. I found Bluefish quite intuitive and
easy to use for a non-WYSWYG editor. Seamonkey 
was also quite easy to use for a novice, but is it perhaps
a bit too weak? I see that Amaya 
([http://www.w3.org/Amaya/User/BinDist.html](http://www.w3.org/Amaya/User/BinDist.html)) 
has an Ubuntu distribution available, do anyone know 
why Amaya doesn't show up in the Ubuntu Software Senter?
(Perhaps it isn't used primarily for web design?)

I've also had a little look around at some of the 
web-design packages you can get for Windows... 
It seems as if there is a lack of an open-source 
program for Linux that is an obvious competitor 
with the stuff you can get for Windows. I mean, 
Gimp is already an excellent alternative to Photoshop;
Inkscape and Scribus is beginning to give Illustrator 
and Indesign some serious competition. But at the 
moment I don't think there are any program that 
comes close to being a Dreamweaver-killer. (Or Html-kit killer).
No matter what one thinks of Dreamweaver, 
I think an open-source alternative is needed. Like it or not,
it is a package that many, many designers use.

From a designers point of view, I think one should
ideally be able to do as much design as possible with
as little manual coding as possible. I mean, if I was 
going to design a logo, I would use Illustrator/Inkscape,
not C++. On the other hand I freely admit that I'm
inexperienced when it comes to web-design. 
(I used Dreamweaver for a couple of weeks waaaay back
in the Macromedia days.) When it comes to  WYSWYG, 
I see from reading posts on the topic that many claims
that it produces “dirty” code... **xtremethegreat1** writes:

> And about the WYSIWYG, I think it is a must not when starting to learn from scratch. But if total control is not what you're looking for, then WYSIWYG is for you. Good luck.Design is indeed all about control, so I wonder 
whether there is something in the code that 
WYSIWYG-programs makes, that has negative 
consequences for those who access your site? 
Does “dirty” code cause any real problems, and what
does “total control” mean in the context of web-design?
Finally: Is it theoretically possible to create a piece
of open-source software which is just as easy to 
use as Dreamweaver, (or even notorious web-generators
such as Netobjects Fusion and Web-builder) 
but that also produces clean and nice code? 

Thanks for your contribution!

---

### Post by airtonix on 2011-02-17
WYSIWYG programs typically do not create legible stylesheets, or embed the styles inline with the html which then defeats the purpose of browser caching.

You need to appreciate that creating a HTML & CSS page is not about pixel control.

I suggest you start reading [http://alistapart.com](http://alistapart.com) to become familiar with better HTML & CSS creation techniques.

I too started out creating websites with dreamweaver when it was version 4.

I stopped using it when I realised it was creating more work for me later on (no to mention the frequent loss of work due to the program misbehaving).

I now use gedit with the following plugins
[LIST]
[*] Word Completion,
[*] gMate Plugin Set
[*] Rabbit CVS Git Plugin
[*] External Tools
[*] Find in Open Documents
[/LIST]

You might also like Aptana, which is a very nice package (even if it is based on Eclipse), there's also a portable version for both windows and linux.

Although use gimp and inkscape, I've come to the conclusion that less is more when it comes to graphics and webpages.

---

### Post by the_blue_box on 2011-02-17
I would recommend Kompozer.
you can use the WYSIWYG interface and/or edit the source code (I do both because you can clean up the code as you go along) 
and if you want to use css (I assume you will) it embeds it by default but there is an option to turn it into a separate file/files that's neatly laid out.
Plus a myriad of other brilliant features. 

all-in-all a very good program.

what ever you go for I wish you all the best.

[COLOR=Blue]the_blue_box[/COLOR]

---

### Post by Neon Lights on 2011-02-17
airtonix gives some good advice. I use gedit as well.

Honestly, if you don't want to learn HTML/CSS, unless it's a really simple project, it'll probably be best to draw up your designs and team up with someone who knows it.

If you do want to learn to code, I would say a WYSIWYG editor is a must not as well. [http://alistapart.com](http://alistapart.com) and [http://w3schools.com](http://w3schools.com) are great resources.

---

### Post by Dry Lips on 2011-02-20
**airtonix**:
> 
WYSIWYG programs typically do not create legible stylesheets,
or embed the styles inline with the html which then defeats the 
purpose of browser caching.This was exactly the kind of feedback I was looking for. 
Thank you so much for your kind advice. I see I need to
do some research about style sheets. I found this page that I 
think was impressive: 
[http://www.csszengarden.com/](http://www.csszengarden.com/)

You write about browser caching...  Do I understand you right if 
I assume that the issue here is about reducing bandwidth?

Thanks for the reference to alistapart. I promptly bookmarked it.
There was enough useful information on it to keep me reading for
a while, in addition to that it's also a nice page visually.
I agree that design doesn't necessarily have to be very complex 
in order to please the eye. 

Aptana: I've seen more people that you recommending Aptana. 
I've installed Eclipse and Aptana, as it seemed that the standalone
version didn't run on 64-bit Linux. At least I cannot complain that 
I lack tools powerful enough for the task...  Eclipse seems like 
something of a Behemoth!  But it could be worth the effort to look 
into it, if mastering a program like Aptana saves me time later on.


“Ain't got no pixel control” ;)

---

### Post by Dry Lips on 2011-02-20
[B]the_blue_box
[/B]
Now I've got pretty much all the software worth installing in Ubuntu:
KompoZer, Bluefish, Seamonkey, Plus Eclipse and Aptana... Right now,
I think the way to go is to read up on some resources, and basically 
play around with the different packages in order to find out which one 
that suits me best. I had a little trouble the first time I used KompoZer,
but it could be that running a couple of tutorials would be of help.

---

### Post by Dry Lips on 2011-02-20
**Neon Lights**:
> 
“Honestly, if you don't want to learn HTML/CSS, unless it's a really simple project, it'll probably be best to draw up your designs and team up with someone who knows it.”Of course that's an option... But I guess it's a bit like hiring a chauffeur;
you only do so if you're well situated. (And then again, some of us 
prefers being the driver rather than being passenger;)) 

What I'll do next, is to begin developing my first website; then I could 
post a link here for feedback from more experienced web-designers.
 I'm thinking a basic Ubuntu fan-page could be a nice little project to begin with.

Thanks for the link to w3schools! I'll definitively have a look at it!

---

### Post by marcusbowlerhat on 2011-02-28
Hey, I don't use it any longer but Dreamweaver is still the best WYSIWYG web tool so if you are design driven, this will help keep that nasty code in the background. 

Bluefish is great for code and if you really want to take your designs beyond static pages then you will need to get your hands dirty and this will do the job. 

W3Schools is a great resource for learning the basics, give it a go, you may find it's not as scary as you first thought and the more you learn about how things are put together the more intelligence you have to feed into your design work. 

All the best!
Marcus

---

### Post by Dry Lips on 2011-02-28
> Bluefish is great for code and if you really want to take your designs  beyond static pages then you will need to get your hands dirty and this  will do the job... the more you learn about how things are put together the more intelligence you have to feed into your design work. 
Well, yeah mate! I've come to the conclusion
that learning some HTML is definitively an advantage, 
even if you used an WYSIWYG-editor that never displayed
any code at all. 

Grudgingly I must admit that knowledge is power. ;)

---

### Post by Jose Catre-Vandis on 2011-02-28
Use a WYSIWYG editor to help you find your feet, then move onto code. I used to think Microsoft Frontpage was the bees knees, until I saw what was going on underneath! Yuk!

I used komposer to build up my company's revamped website (which needed  many tables for layout) but unpicking it in a code editor was a nightmare.

Now I generally tend to use Geany as an editor, with a browser window refreshing every 15 seconds if I need that (Firefox reload extension)

Head over to W3C schools for their excellent css reference with examples. Also [www.cssplay.co.uk](www.cssplay.co.uk) is full of ideas, and Stuart is very helpful.

Use GiMP and Inkscape for artwork, and Drupal 7 if you need CMS. Have fun!

---

### Post by Kirboosy on 2011-02-28
I really like using Bluefish. I have found it to be very powerful and very user friendly. I know you are still coding but it makes it easier. 

It has a list of commands that you can use. You can simply start typing a command and often times hit tab to complete filling in everything. It makes it very easy and less time consuming. 

The best part is....its NOT a WYSIWYG editor which is awesome. :)


[Opera Dragonfly]("http://www.opera.com/dragonfly/") is also a cool tool to use (Its included with the opera browser)

---

### Post by Dry Lips on 2011-02-28
**Jose Catre-Vandis** & **Caboose885**:

Thanks for your suggestions! After reading up on HTML,
I think it is not that difficult in itself. Css is more complex,
but clearly a very important aspect to webdesign that I need
to have a closer look at.

Cheers!

---

### Post by JoojiSan on 2012-02-25
I read all posts.
I don't have so much experience in web design and now I am going to start learning the code and I have to choose a good software for novices.
Somewhere in the ubuntu forums I read about BlueGriffon.
What is Your opinion about it?
Which software will You recommended me?

Thank You!

---

### Post by Dragonbite on 2012-02-27
WYSIWYG[LIST]
[*]Kompozer (which is an updated version of Nvu, which is still available but does not include the patches and updates that are in Kompozer)
[*]BlueGriffon
[*]Quanta Plus (KDE)
[*]I haven't tried it, but if I remember right Aptana includes either a WYSIWYG or instant/easy preview (make changes, switch and see preview). Like I said, I haven't tried it yet.
[*]Amaya
[/LIST]

TEXT[LIST]
[*]Gedit
[*]Bluefish
[*]Netbeans
[*]Eclipse
[*](any of the WYSIWYG above)
[*]Geany
[/LIST]

Those are the ones I can think of off the top of my head.

---

### Post by snowz on 2012-02-27
Personally using Bluefish and Geany with the combination of Inkscape and Gimp for the graphics part of the work. Really impressive what open source is capable of.

---

### Post by Isaacgallegos on 2012-02-27
I haven't tried this yet, but I think Inskcape has tools for web design. Inkscape is also my favorite program on Linux.

---

### Post by JoojiSan on 2012-02-28
OK.
Thank You All!
I have to begin and just work. Thank you again!

---

### Post by Dry Lips on 2012-02-29
Huh? How did this old thread of mine get resurrected? 

For the records: I use gedit nowadays.

---

### Post by josephmills on 2012-02-29
Hello there 
I use mono development for all my asp classic asp asp.net and C# and vb/vbscripting. There is no graphics mode like in visual web dev. 

for mysql I use php-myadmin and or mysql admin to write insert statements I use the cli most of the time. 
(mssql still have to use microcrap software need to look more into sql light)

For java I use eclipse
for php html css javascript ajax I use one of the following \
sublime 2 text editor <-- real good 
codeblocks 
Geany 
gedit 
bluefish 
gPHPedit
nano 
well I hope that this helps. Also if any one can tell me what they use for MSSQL not mysql MSSQL that would be cool :)

Oh and for a testing envo I use either 
virtual box 
xampp

---

### Post by Dragonbite on 2012-02-29
> **josephmills said:**
> Also if any one can tell me what they use for MSSQL not mysql MSSQL that would be cool :)

Oh and for a testing envo I use either 
virtual box 
xampp

We use PosgtreSQL on our PHP sites (otherwise it's ASP.NET and MSSQL for the Intranet).  I hear it is probably one of the closest free sql databases out there to compare with MSSQL Server.  I haven't gotten into that yet.

I love how easy it is to get Xampp up and running.

EDIT: I didn't think Monodevelop could handle Classic ASP!  Can it handle VB6?

---

### Post by josephmills on 2012-02-29
> **Dragonbite said:**
> We use PosgtreSQL on our PHP sites (otherwise it's ASP.NET and MSSQL for the Intranet).  I hear it is probably one of the closest free sql databases out there to compare with MSSQL Server.  I haven't gotten into that yet.

I love how easy it is to get Xampp up and running.

EDIT: I didn't think Monodevelop could handle Classic ASP!  Can it handle VB6?

not sure to tell you the truth. but you sure can write/edit classic asp and just run files in browser. but building aspClassic pages with the built in functions of monodev not sure. I wish that I could change the data bases to postgresql but that is not goig to happen (work) I was wondering more about a remote tool for mssql at the office I just use the file manager and [http://appdb.winehq.org/objectManager.php?sClass=application&iId=7218](http://appdb.winehq.org/objectManager.php?sClass=application&iId=7218) 
<-- what a pain there and and or mono

---

### Post by callen41 on 2012-03-03
I use Sublime Text 2.  Its python based and compatible with every major OS.

---

### Post by prokoudine on 2012-03-03
> **callen41 said:**
> I use Sublime Text 2.  Its python based and compatible with every major OS.

Apparently it's C++ with bits of Python :) Ditto on Sublime Text 2.

---

### Post by 23dornot23d on 2012-03-04
Link .... here for Users that want to try it ..... the executable is in the download for 32 bit

seems good so far .... [http://www.sublimetext.com/2](http://www.sublimetext.com/2)

---

### Post by Guilden_NL on 2012-04-24
I designed and launched quite a few websites back in '94-'98 using both text and WYSIWYG editors.  Back then, I used to use vi editor for quick and dirty HTML, but my favorite for years was Hot Dog by Sausage software.

I had the need to get a nice looking site up very quickly this week and I tried a few from Amaya to some WordPress web based editors but believe KompoZer is a great tool for beginners as well as those who know what they are doing, but are not web coding jockeys and they need to do it fast.

On a 10 scale, I give KompoZer an 8.5 and am impressed by their documentation - much better than what I am used to with Linux apps.

It saved my bacon, much like Sausage did 17 years ago.

---

### Post by JoeyCagle on 2012-08-26
Is there a reason no one has mentioned BlueGriffon? BlueGriffon is great, especially for the latest HTML5 developments. And it's based on Kompozer, but a lot better IMO.

---

### Post by spaceshipguy on 2012-09-11
I was very frightened of losing the WYSIWYG interface and using gedit instead. But it is relatively simple to get a small site with simple functionality. 
Some tips on coding here [http://www.w3schools.com/html/default.asp](http://www.w3schools.com/html/default.asp)
These are just the tutorials I Googled up and used. I don't know if there are any better ones.

It's actually quicker and easier to write your own Css and HTML files, rather than WYSIWYG, because when something goes wrong you can work out what it is and so troubleshooting is quicker.

---

### Post by Dragonbite on 2012-09-11
> **spaceshipguy said:**
> It's actually quicker and easier to write your own Css and HTML files, rather than WYSIWYG, because when something goes wrong you can work out what it is and so troubleshooting is quicker.

Plus only what you code is what gets put into the files.  After having used Microsoft FrontPage, I appreciate knowing that only what I put into the code gets into the code.

The WYSIWYG front-end wasn't too bad, then I learned to flip it over and manually enter all of the server-side coding by hand.  That worked for the most part for me.

---

### Post by heavylildude on 2012-09-13
My favorite editor would be Sublime Text 2 :KS I found it as an equivalent to Espresso Mac since I'm back-forth Mac-Ubuntu daily..

---

### Post by heavylildude on 2012-09-13
> **23dornot23d said:**
> Link .... here for Users that want to try it ..... the executable is in the download for 32 bit

seems good so far .... [http://www.sublimetext.com/2](http://www.sublimetext.com/2)

or add via ppa:webupd8team/sublime-text-2 :D

---

### Post by Dragonbite on 2012-09-13
Just found out about [[COLOR="Blue"]_Maqetta_[/COLOR]]("http://r7.maqetta.org/") which is > Visual authoring of HTML5 user interfaces - in the browser!
Maqetta is an open source project that provides WYSIWYG visual authoring of HTML5 user interfaces. The Maqetta application itself is authored in HTML, and therefore runs in the browser without requiring additional plugins or downloads.

---

### Post by raptorak on 2012-09-15
> **Dragonbite said:**
> Just found out about [[COLOR="Blue"]_Maqetta_[/COLOR]]("http://r7.maqetta.org/") which is

That is kind of interesting to me... I've never heard of a web UI designer before. Following the "features" and all is leaving me a bit confused as to how it works or what its purpose is, but definitely looking further into it out of curiosity.

---

### Post by contributor on 2012-09-17
>  I had a little trouble the first time I used KompoZer,
but it could be that running a couple of tutorials would be of help.

Though, if you are using it first time, you may face some difficulties but it is really suitable if you are not interested in knowing the code. Moreover, it is really very easy to use.

---

### Post by Szise on 2012-09-20
I'm not an expert but for me Bluefish is the best.

---

### Post by Dragonbite on 2012-09-20
I would love it if I could get [[COLOR="Blue"]Code Lobster[/COLOR]]("http://www.codelobster.com/") running in Linux.  It is the closest thing I have found for Visual Studio-like PHP IDE with stepping through debugging.

(the PHP feature in VS 2010 is not available in Express either).

---

### Post by Lyfang on 2012-11-12
BlueGriffon, Seamonkey Suite, Kompozer are not found in the Quantal repository! Is there an open source WYSIWYG website editor that also works well with CMS, HTML5, CSS and PHP? Searching for software that is up-to-date. LibreOffice Writer can save a Writer document in HTML format and LibreOffice 3.6 is in the Quantal repository. Amaya works with Lubuntu 12.10 (Quantal Quetzal) but is not in the Quantal repository.

---

### Post by BcRich on 2012-11-12
> **Lyfang said:**
> BlueGriffon, Seamonkey Suite, Kompozer are not found in the Quantal repository! Is there an open source WYSIWYG website editor that also works well with CMS, HTML5, CSS and PHP? Searching for software that is up-to-date. LibreOffice Writer can save a Writer document in HTML format and LibreOffice 3.6 is in the Quantal repository. Amaya works with Lubuntu 12.10 (Quantal Quetzal) but is not in the Quantal repository.

Hi Lyfang,
I'm a big fan of Seamonkey, for me it's much less buggy than Kompozer and far simpler to use. I recall that it was removed from the Precise repos due to the PPA not being maintained but after doing a search I found this [https://launchpad.net/~joe-nationnet/+archive/seamonkey-dev](https://launchpad.net/~joe-nationnet/+archive/seamonkey-dev) which seems to have a Quantal build. I haven't tested it so I can't really recommend it. As Seamonkey is updated regularly I would sugest checking out the official website an downloading a copy from there [http://www.seamonkey-project.org/](http://www.seamonkey-project.org/) that's what I've been doing and it been working fine for me on Precise 12.04. Although Seamonkey does not have a CSS editor like Kompozer, this still works better for me cause I find it easier to edit CSS directly. To be honest I find the Kompozer interface a little confusing :confused: Regarding a PHP WYSIWIG editor I think you'll be hard pressed to find any reputable software resembling that (open or closed). Being a logic-based computer programming language and not a mark-up language g
nerally means the closest you'll get to WYSIWYG is an IDE. I use Netbeans for PHP development but many people also use Eclipse.

---

### Post by Lyfang on 2012-11-12
[SOLVED] up-to-date WYSIWYG website editor. Thanks BcRich! Now I'll use Composer from the SeaMonkey Suite 2.13.2 (package seamonkey 2.13.2-0ubuntu1~quantal), which is also the latest version (2.13.2) from the SeaMonkey project's website. Composer has a feature that can switch between Normal (WYSIWYG mode) and <HTML> Source. LibreOffice 3.6 works too but is mainly an office suite. However if one wants to pass the W3C's HTML validation test one should use the Amaya Web editor (from W3C).

---

### Post by NewAmercnClasic on 2012-11-12
> **Dry Lips said:**
> Huh? How did this old thread of mine get resurrected? 

For the records: I use gedit nowadays.

:guitar:  What about db management?

---

### Post by prokoudine on 2012-11-13
> **Lyfang said:**
> Is there an open source WYSIWYG website editor that also works well with CMS...


Excuse me, but what did you just mean with that? :)

---

### Post by Lyfang on 2012-11-13
> **prokoudine said:**
> Excuse me, but what did you just mean with that? :)
Most CMS work great alone like: Wordpress, Drupal and Joomla. What about redesigning and dealing with a CMS framework? Is there an open source website editor that allows to modify a CMS web template?

---

### Post by Dragonbite on 2012-11-13
I haven't tried it in WINE yet, but CodeLobster offers [[COLOR="Blue"]plug-ins for a price[/COLOR]]("http://www.codelobster.com/order.html").  It is one of the best non-VS IDEs I've used so far (though it doesn't include database support I believe).

Available plug-ins:
[LIST]
[*]CakePHP plug-in
[*]CodeIgniter plug-in
[*]Drupal plug-in
[*]Facebook plug-in
[*]JQuery plug-in
[*]Joomla plug-in
[*]Smarty plug-in
[*]Symfony plug-in
[*]WordPress plug-in
[*]Yii plug-in
[/LIST]
The free version handles HTML, Javascript, CSS and PHP.

---

### Post by prokoudine on 2012-11-15
> **Lyfang said:**
> Most CMS work great alone like: Wordpress, Drupal and Joomla. What about redesigning and dealing with a CMS framework? Is there an open source website editor that allows to modify a CMS web template?

Why do you need it at all? I mean, come on, we are long past the age of Microsoft Frontpage :)

These days people builds website on top of [Bootstrap]("http://twitter.github.com/bootstrap/"), [HTML5 Boilerplate]("http://html5boilerplate.com/") and the like. You only need to customize styles, cut and place graphics.

---

### Post by JoeyCagle on 2012-11-28
It's been a long time since I've been here.

True, BlueGriffon is not in the repository. You'll want to go to bluegriffon.org and download the Ubuntu installer.

---

### Post by Lyfang on 2012-11-29
> **JoeyCagle said:**
> It's been a long time since I've been here.

True, BlueGriffon is not in the repository. You'll want to go to bluegriffon.org and download the Ubuntu installer.
BlueGriffon website didn't include a .deb file to download. I use SeaMonkey Browser for browsing and will try to make a great webpage using SeaMonkey Composer, "Publishing Site Settings..." could include an option to login in and synchronize with CMS, but doesn't.

---

### Post by Lyfang on 2012-12-08
> **prokoudine said:**
> Why do you need it at all? I mean, come on, we are long past the age of Microsoft Frontpage :)

These days people builds website on top of [Bootstrap]("http://twitter.github.com/bootstrap/"), [HTML5 Boilerplate]("http://html5boilerplate.com/") and the like. You only need to customize styles, cut and place graphics.
**Plain HTML** Building from scratch saving a new page using plain static HTML: You can add an external style sheet (CSS) and insert an image. Done. Disadvantage is that plain HTML sites often require more coding for a website to look modern. Open source WYSIWYG website editors include: SeaMonkey Composer and Amaya. I have found SeaMonkey Composer work better than Amaya with Lubuntu.

**Content Management System** I prefer CMS (is dynamic and database driven) when the site needs to be up-to-date and changes often. One disadvantage with CMS is usually higher bandwidth usage. Popular open source CMSs include Drupal, Joomla! and Wordpress. Find a CMS template and start inserting text and images.

**Text editor** Development in editors that work like an advanced text editor gives more control. Great for programmers.

In the end CMS (and HTML5) might win.

---

