---
title: "A good html editor for Ubuntu"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by Jim_in_Germany on 2008-04-06
Evening,

Could somebody please tell me a good HTML editor which is bundled with Ubuntu (Gutsy 7.10).
I have worked for the past few years with Dreamweaver, so the closer it is to that, the better (in case there is more than one editor bundled).

Many thanks in advance.
Jim

---

### Post by billgoldberg on 2008-04-06
Go to applications -> Add/Remove and search for "html"

Make sure you enable "all available applications" in the top right corner.

---

### Post by uidb4056 on 2008-04-06
An interesting web authoring tool available from synaptic repositories is kompozer

---

### Post by Jim_in_Germany on 2008-04-06
Hi, 
Thanks for the quick reply.
I found quite a few:
Screem
Bluefish
Quanta Plus
Geany
Amaya
gPHPedit
etc.

Do you (or anybody else) have an opinion about which is better?

Ta.

---

### Post by Oldsoldier2003 on 2008-04-06
> **Jim_in_Germany said:**
> Evening,

Could somebody please tell me a good HTML editor which is bundled with Ubuntu (Gutsy 7.10).
I have worked for the past few years with Dreamweaver, so the closer it is to that, the better (in case there is more than one editor bundled).

Many thanks in advance.
Jim

I like Bluefish
```
sudo apt-get install bluefish
```

---

### Post by Jim_in_Germany on 2008-04-06
Bluefish looks cool. It describes itself as an advanced HTML editor. Groovy :-)
What's interesting about Kompozer?

---

### Post by Oldsoldier2003 on 2008-04-06
> **Jim_in_Germany said:**
> Bluefish looks cool. It describes itself as an advanced HTML editor. Groovy :-)
What's interesting about Kompozer?

the cool thing about bluefish is you can use it for more than html editing. it has syntax highlighting for fast and dirty code writing... it's not an IDE though

---

### Post by billgoldberg on 2008-04-06
> **Jim_in_Germany said:**
> Hi, 
Thanks for the quick reply.
I found quite a few:
Screem
Bluefish
Quanta Plus
Geany
Amaya
gPHPedit
etc.

Do you (or anybody else) have an opinion about which is better?

Ta.

 I tried Amaya last week (creating a little webpage for the network) and it crashed on me (and took X with it)  and was very hard to use. I ended up doing it in gedit (installed by default).

But from what I've heard, bluefish is quite good.

---

### Post by SunnyRabbiera on 2008-04-06
Kompozer is pretty good for a WYSIWYG application, if you are familiar with dreamweaver and have little HTML experience then Kompozer will suit you.
I never had a problem with Kompozer, you should give it a try.

---

### Post by Jim_in_Germany on 2008-04-06
Hi,

Thanks for that.
I just installed it and got going. It looks really good.
Unfortunately, straight away I noticed that the "View in Browser" button doesn't work.
Do you know if you have to specify which browser to view it in anywhere?

---

### Post by Jim_in_Germany on 2008-04-06
Answered my own question:
[http://ubuntuforums.org/showthread.php?t=485246](http://ubuntuforums.org/showthread.php?t=485246)

Cheers

---

### Post by Jim_in_Germany on 2008-04-06
Hi,

Just realised that there is no WYSIWYG function in Bluefish.
Is there another editor packaged with Ubuntu with this feature?

Thanks
Jim

---

### Post by qamelian on 2008-04-06
> **Jim_in_Germany said:**
> Hi,

Just realised that there is no WYSIWYG function in Bluefish.
Is there another editor packaged with Ubuntu with this feature?

Thanks
Jim
Although I haven't used it for a while, I believe Quanta has a visual mode that, if not true WYSIWYG, should be close enough if you really need that kind of functionality. I've never like That style of HTML development myself because, in the long run, I find WYSIWYG web design is actually much slower for me then hand-coding everything. I usually spend more time fixing what WYSIWIG editors break than actually developing pages!

---

### Post by Oldsoldier2003 on 2008-04-06
> **qamelian said:**
> Although I haven't used it for a while, I believe Quanta has a visual mode that, if not true WYSIWYG, should be close enough if you really need that kind of functionality. I've never like That style of HTML development myself because, in the long run, I find WYSIWYG web design is actually much slower for me then hand-coding everything. I usually spend more time fixing what WYSIWIG editors break than actually developing pages!

+1 Wysiwyg editors tend to output sloppy and (very often) invalid code.

---

### Post by .nedberg on 2008-04-06
You could try eclipse with aptana. Read about aptana on aptana.com. Install eclipse from synaptic.

---

### Post by Jim_in_Germany on 2008-04-06
Hi,
You are indeed correct, wysiwyg editors are sloppy, but when it comes to making a (largish) table for example, or repositioning an image they are a lot easier. 
I will try out the editors you suggest.
Thanks muchly

---

### Post by finferflu on 2008-04-06
I'd say learn to use Vim. It's the best editor I've ever found. And if you learn it, you'll find yourself with an omnipotent text editor. Don't let the flashy stuff blind you, look for functionality. And I assure you Vim is ultra functional. If you don't like typing in a terminal, just install the GTK fronted, Gvim. 
Vim is very extendable, so you can look for specific HTML plugins with a [simple search](http://www.vim.org/scripts/script_search_results.php?keywords=html&script_type=&order_by=rating&direction=descending&search=search).
It might have a steeper learning curve than other editors, but it's worth all the time it takes.

---

### Post by SunnyRabbiera on 2008-04-06
> **Jim_in_Germany said:**
> Hi,

Just realised that there is no WYSIWYG function in Bluefish.
Is there another editor packaged with Ubuntu with this feature?

Thanks
Jim

well as I said there is kompozer, its in the repositories and easy to get.

---

### Post by bloodorange on 2008-04-06
I've just installed Bluefish and got on really well with it.  I don't know much about website coding, but managed to build a simple site - [www.bloodorangeonline.com](www.bloodorangeonline.com).  Before that I'd only used Frontpage, in the bad old days when I used Windows.

---

### Post by linuxlizard on 2008-04-06
Other than Kompozer, I don't think you will find much in the way of a wysiwyg editors.
Kompozer is pretty good though- it puts out pretty clean code compared to say frontpage in windows.

kompozer, bluefish and quanta are the big ones to be sure and check out.

---

### Post by Jim_in_Germany on 2008-04-06
I went for Amaya which totally kicks, but it crashed when I tried to use the full screen command.
Then I installed Kompozer which was exactly what I was looking for.
So, thanks for the good recommendation.

Regarding VIM I only deffed off my Windows Vista 4 days ago and converted to Ubuntu, so the learning curve is steep enough at the moment :-) I did use VIM under Windows though and it was ok.

Regarding Blood Orange - nice site. I just had a quick look.

---

### Post by oskar2000 on 2008-04-06
On Bluefish:
> **Jim_in_Germany said:**
> Hi,

Thanks for that.
I just installed it and got going. It looks really good.
Unfortunately, straight away I noticed that the "View in Browser" button doesn't work.
Do you know if you have to specify which browser to view it in anywhere?

Yup, that happened with Gutsy. I filed a bug report that was rejected - they said it was someone else's fault. You can set the command in the preferences and make a hotkey though.

And -1 on the WYSIWYG editors. It's a travesty what these things have done to the web.
You said they make it easier to edit large tables - that's the point! you should not be making large tables for layout. Use CSS!

---

### Post by hvac3901 on 2008-04-06
> **Jim_in_Germany said:**
> Hi,

Thanks for that.
I just installed it and got going. It looks really good.
Unfortunately, straight away I noticed that the "View in Browser" button doesn't work.
Do you know if you have to specify which browser to view it in anywhere?

I just use the "preview" button on the bottom of the page in current edit. If you have trouble with Komposer you could use "Nvu" basically the same program, Komposer is supposed to be the newest, but i have noticed some troubles with Komposer i didn't have in NVU.

---

### Post by Jim_in_Germany on 2008-04-06
I knew someone would say that, so thanks.
I agree you shouldn't use tables for your layouts - not good.
However, there are some occasions when you need a normal table, visible in your html doc, so as to present a large quantity of information in a clear and concise way.
Cheers nonetheless.

---

### Post by apostate on 2008-04-06
> **Jim_in_Germany said:**
> Bluefish looks cool. It describes itself as an advanced HTML editor. Groovy :-)
What's interesting about Kompozer?

Bluefish is possibly more powerful, but it is an IDE for html coding, not a design studio like Dreamweaver. There is no WYSIWYG view.  Kompozer is ok, it has a few annoying traits but it is very like Dreamweaver in how it functions. It has some pretty nice wizards and such, as well as a pure HTML view. You may like it for that reason.

---

### Post by Triggerhapp on 2008-04-06
> **finferflu said:**
> I'd say learn to use Vim. It's the best editor I've ever found. And if you learn it, you'll find yourself with an omnipotent text editor. Don't let the flashy stuff blind you, look for functionality. And I assure you Vim is ultra functional. If you don't like typing in a terminal, just install the GTK fronted, Gvim. 
Vim is very extendable, so you can look for specific HTML plugins with a [simple search](http://www.vim.org/scripts/script_search_results.php?keywords=html&script_type=&order_by=rating&direction=descending&search=search).
It might have a steeper learning curve than other editors, but it's worth all the time it takes.

+1

---

### Post by apostate on 2008-04-06
> **oskar2000 said:**
> On Bluefish:


Yup, that happened with Gutsy. I filed a bug report that was rejected - they said it was someone else's fault. You can set the command in the preferences and make a hotkey though.

And -1 on the WYSIWYG editors. It's a travesty what these things have done to the web.
You said they make it easier to edit large tables - that's the point! you should not be making large tables for layout. Use CSS!

You can set your Browser to one that actually comes with Ubuntu...  :-)

Edit -> Preferences -> External Programs

Use the string for Mozilla, and just replace the name of the browser with Firefox.

Cheers.

---

### Post by Jim_in_Germany on 2008-04-06
Thank you ladies and gents,
I am currently editing my site with Kompozer.
The WYSIWYG view is quite good.
The code view is terrible.
I will keep trying various editors until I come up with the one that suits me best.
It seems they are all good for their purpose, but there is a slight compromise inherent in each one.

By the way, what's all this +1 and -1?
Have I missed sth?

---

### Post by Triggerhapp on 2008-04-06
+1 = agree
-1 = disagree

not as deep as some people might asume :)

---

### Post by oskar2000 on 2008-04-07
> **Jim_in_Germany said:**
> I knew someone would say that, so thanks.
I agree you shouldn't use tables for your layouts - not good.
However, there are some occasions when you need a normal table, visible in your html doc, so as to present a large quantity of information in a clear and concise way.
Cheers nonetheless.

Yeah, that might have come across too harsh...
There are little helper programs for tables and such, though - that aren't all that different from their WYSIWYG counterparts

---

### Post by Crafty Kisses on 2008-04-07
I'd personally use Bluefish, or perhaps Kompozer.

---

### Post by Jim_in_Germany on 2008-04-07
Hi Oskar2000,

No drama - I'm basically of the same opinion as you.
I always try to make sure my code validates and is standards compliant.
I also love and make very good use of css.
There are however definitely times when a wysiwyg editor is good though.
I thought of another example today:
If you have a long doc and have to edit part of it, I find it very helpful to highlight the part I want to change in the wysiwyg view, then change to source and carry on working.
Is there a linux based editor that does that?
Now that would be luxury :-)

Jim

---

