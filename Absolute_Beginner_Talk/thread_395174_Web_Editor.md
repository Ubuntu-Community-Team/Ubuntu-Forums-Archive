---
title: "Web Editor"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by pacco on 2007-03-27
I was wondering which is the best web editor to use with ubuntu, i am use to using macromedia studio which dreamweaver allows you to work with multiple file formats such as php,cgi,etc.

Is the one out there like that that doesn't cost anything?

Thanks in advance
:)

---

### Post by qpwoeiruty on 2007-03-27
If you're looking for something Dreamweaver-like, [NVU](http://www.nvu.com/index.php) does a fair job.

You can
sudo apt-get install nvu
to give it a test

---

### Post by 23meg on 2007-03-27
[http://www.ubuntuforums.org/showthread.php?t=371145](http://www.ubuntuforums.org/showthread.php?t=371145)
[http://www.ubuntuforums.org/showthread.php?t=383207](http://www.ubuntuforums.org/showthread.php?t=383207)
[http://www.ubuntuforums.org/showthread.php?t=314780](http://www.ubuntuforums.org/showthread.php?t=314780)
[http://www.ubuntuforums.org/showthread.php?t=367589](http://www.ubuntuforums.org/showthread.php?t=367589)
[http://www.ubuntuforums.org/showthread.php?t=384388](http://www.ubuntuforums.org/showthread.php?t=384388)

Please do a search before asking questions.

---

### Post by aysiu on 2007-03-27
Gedit works for me.

---

### Post by houstonbofh on 2007-03-27
I use NVU.  However it has been removed from the repositories from Feisty onwards!  And has no replacement!  (The no replacement is what upsets me. Can you tell?)  So, get it before the upgrade, or get it manually after, or try komposer, which is not in the repositories, and is a fork of NVU.

---

### Post by DJ_Peng on 2007-03-28
> **qpwoeiruty said:**
> If you're looking for something Dreamweaver-like, [NVU](http://www.nvu.com/index.php) does a fair job.

I beg to differ. As an old Dreamweaver user I checked out Nvu several; times, both as a Windows user and as a Linux user. Each time I was disappointed in Nvu to the point of removing it. Someone around here suggested [Aptana](http://aptana.org/), although I haven't really used it much since I have DW installed to work under Wine. So far my one complaint about Aptana is that you can't see the code and the preview at the same time, *a la* DW's Split mode, but I may just need to dig through the settings more.

---

### Post by 3rdalbum on 2007-03-28
If Nvu has been removed, it is because it is old unmaintained software.

There is a fork called Kompozer, which you can get from [www.getdeb.net](www.getdeb.net). It apparantly has some new features.

---

### Post by DarkN00b on 2007-03-28
Lately I've been using gedit and opening the saved page in my browser. Save in gedit and refresh in Firefox...lather, rinse, repeat.

I tend to use templates because I'm lazy and I've found that NVU does terrible things to the HTML code. Amaya does better but sometimes doesn't render a page correctly. I suppose if I built the page from scratch I wouldn't have this problem. You might give [Amaya]("http://www.w3.org/Amaya/") a look though. I has many bells and whistles that you might like. Its also the W3C's official web editor.

---

### Post by DSn0wMan on 2007-03-28
Having used GEdit, Kate, Bluefish, NVU, and some others that I cant remember I would have to say that Kate works best for me. GEdit is almost the same, but kate lets you collapse and expand your code which comes in handy. In agree with DarkN00b about NVU.

---

### Post by DJ_Peng on 2007-03-28
Yeah, that was oart of the deal breaker this last time for me, too. Not only did it do trash my HTML code, it doesn't do PHP at all. I'm curious about Adobe's first release of DW, but I may stick with DW 8 since they still don't have a native Linux version available. Why spend money for something to run under Wine when the previous version runs fine and I already own it?

---

### Post by deuchar1 on 2007-03-28
I like Screem, but I tend to do my site development for work under Windows. I use Ubuntu for programming (BlueFish mainly). Screem seems to do the job for basic development alongside the gimp for design.

---

### Post by TURNER on 2007-03-28
Hi.

[Blue Fish]("http://bluefish.openoffice.nl/index.html") would be your best bet, although it does not provide a WYSIWYG editor if this is what you are used to using in Dreamweaver....

If you like to handcode (if you don't already give it a try!), then Bluefish will allow you to code in html, css, php, javascript to name a few.

Give it a whirl! :)

---

### Post by deuchar1 on 2007-03-28
TURNER - how on earth do you get time to handcode? I miss that luxury :(
I used to handcode and BlueFish worked out great for it - but I'm working for a corporation design company now and the high turnaround of work means I have to use disgusting DW templates. I think SMARTY is going to be the main word in my vocabulary from now on - at least that way I can do a little hand coding again!

---

### Post by Cannaregio on 2007-03-28
Gedit and especially bluefish give you the same power that ultraedit gave you in windoze.
And you'll find them on any box you may put your hands on (no minor deed).

A combination bluefish-editing+opera-rendering (much better and quicker than firefox) is the absolute _scalable_ überpower for editing sites, may these be as small and tiny as you want or as large and complex as you may fancy.

Using a frontpage-clone is imho NOT a good idea. Not in the least. It wasn't clever in windows  (of course, given the extra-bloating) and it wouldn't be clever in GNU/Linux either. 
Seems better to newbies, isn't at all. With few exceptions that simply confirm the rule.
Once you learn/ get  used/ appreciate the sheer power of web-'hardcoding' (of course with scripts and macro that YOU prepare in order to shortcut repetitive tasks) you wont go back to that slow, cumbersome and bloated crap frontpage (*et similia*) that all those minor furry animals happily slurp and use to produce sites that all look the boring same  :)

---

### Post by pacco on 2007-03-28
Thank you all for your advice, i will try different ones and see which one i like the best.

---

### Post by houstonbofh on 2007-03-29
> **Cannaregio said:**
> Using a frontpage-clone is imho NOT a good idea. Not in the least. It wasn't clever in windows  (of course, given the extra-bloating) and it wouldn't be clever in GNU/Linux either. 
Seems better to newbies, isn't at all. With few exceptions that simply confirm the rule.
Once you learn/ get  used/ appreciate the sheer power of web-'hardcoding' (of course with scripts and macro that YOU prepare in order to shortcut repetitive tasks) you wont go back to that slow, cumbersome and bloated crap frontpage (*et similia*) that all those minor furry animals happily slurp and use to produce sites that all look the boring same  :)
I could not disagree more.  You see I believe in having more than one tool in my toolbox.  Sometimes I will use a text editor to make a very good web page, or tweak a bad one.  Sometimes I just want to paste a spreadsheet into a table.  A "front page clone" is much faster for this simple task.  One with a good code backend is fantastic.  But I also think everyone should stock there own toolbox with the tools they like.

---

### Post by bvanaerde on 2007-03-29
> **deuchar1 said:**
> I have to use disgusting DW templates.
I know what you mean... in my previous jobs, I had to use those too.
At my current job, we also use DreamWeaver, but we're free to use it as we like. So I'm only using it because of the pretty colors, the easy upload system and the check in/out function (because we work with multiple people on the same project).

At home, I'm using Aptana, which I think is the closest thing to DreamWeaver.

---

### Post by macogw on 2007-03-29
I ssh into my server and use vi

If it has to have clicky buttons instead of text commands for you though, Gedit
If it has to be a WYIWYG, Nvu

---

### Post by TURNER on 2007-03-29
> TURNER - how on earth do you get time to handcode? I miss that luxury

I am currently a self employed web designer, and part time, thus whilst building sites I generally have time in which to handcode and take time with my sites...

It would be nice to be full time in web design, but if it really means designing from DW templates I think id rather not :) 

Arent DW template still based on table designs? or is there CSS alternatives?

> of course with scripts and macro that YOU prepare in order to shortcut repetitive tasks

i agree, DW has the nice "code snippets" tool, but in reality this isn't any better than a text doc with useful code, or perhaps a Blulefish template.

Front-page really is the pits, and the new M$ effort "expression" is almost as bad! If you really have to design with a WYSIWYG editor then go for the alternatives listed in this thread, Front-page (and M$ word) add A LOT of unnecessary code, which may not seem like a big deal to the average eye, but really is in terms of accessibility, file size, and web standards.

If you really must use these tools, at least validate your code, and use the recommendations to improve your page.

> Sometimes I just want to paste a spreadsheet into a table. A "front page clone" is much faster for this simple task.

If you paste a spreadsheet into a HTML doc, and take a look under the bonnet, you will see that it actually generates its own code, its not great code, but its code which a web browser will understand, hence this task is just as easy in a text doc, as it is in Front-page.

I was forced to use FP for a while whilst working for M$, managing an intranet.....its a piece of ****! :) 

> At my current job, we also use DreamWeaver, but we're free to use it as we like. So I'm only using it because of the pretty colors, the easy upload system and the check in/out function (because we work with multiple people on the same project).

I like Dreamweaver, its a cool tool, and I enjoy using it to design.  However bvanaerde if you owned that web design company, and you were trying to save money in this cut throat industry, wouldn't you recommend that Dreamweaver can be sacrificed and replaced with an opensourse editor, rather than spend untold quids, $, or € on dreamweaver licenses?

---

### Post by bvanaerde on 2007-03-29
> **TURNER said:**
> However bvanaerde if you owned that web design company, and you were trying to save money in this cut throat industry, wouldn't you recommend that Dreamweaver can be sacrificed and replaced with an opensourse editor, rather than spend untold quids, $, or € on dreamweaver licenses?

Right now I'm working at a university (in Belgium) as a webdeveloper, and they already had a DreamWeaver licence before I started working there :)
When in MS Windows, DreamWeaver is the best program to use, in my opinion. I have yet to try out Zend Studio though... but that's also a paid program.

Apart from the check in/out function (which prevents a file being edited by more than one person at once), we don't *really* need DreamWeaver at work. So you're right when you say that it's not really necessary to use the program.

And at my previous jobs, they just used a crack to activate the program :lolflag: 
Not really professional...

---

### Post by TURNER on 2007-03-30
> Right now I'm working at a university (in Belgium) as a webdeveloper

Cool really! I am in Germany at the moment, close to Dortmund & Essen, only a stones throw away from Belgium...:) 

Sometimes I really cannot understand why firms purchase expensive products like Dreamweaver, when free alternatives are out there....its not logical at all. Perhaps its down to the human mind....thinking that if something is expensive then it must be good.....thats how they managed to keep selling BMW's afterall :)

---

### Post by Spr0k3t on 2007-03-30
Bump for Aptana.  It's based on the eclipse engine for the user interface.  Great for coding pages by hand

---

### Post by deuchar1 on 2007-03-30
> **bvanaerde said:**
> I know what you mean... in my previous jobs, I had to use those too.
At my current job, we also use DreamWeaver, but we're free to use it as we like. So I'm only using it because of the pretty colors, the easy upload system and the check in/out function (because we work with multiple people on the same project).

At home, I'm using Aptana, which I think is the closest thing to DreamWeaver.


They're 'orrible!
I've managed to find a workaround the company allow which is to build all my sites with multiple PHP includes. It basically allows me to strip everything content-wise from the site leaving only a basic CSS structure. From there I insert everything through the includes, so if they want something done site-wide I can one-stop update the include file. 

Check in/check out is very handy. But god, how I hate it when guys in the office forget to check in files before they go home. Always causes headaches!

We use CVS (well, SVN now) to monitor changes. It's handy because it allows the file merge facility in case someone works on something at the same time as you. I never did understand how it works, but it seems to, so I won't look a gifthorse in the mouth :) 

Turner - don't go full time - it's so not worth it :) 
Freelancing was amazing - I miss it. I got a good rate freelancing and when you go fulltime it drops - plus you have the old 9-5:30 sitting in an office festering when you could be home snacking/taking XBox breaks and watching crap daytime telly. 

The good news is I'm going back to freelancing at the end of April. Anyone interested in any joint venture projects? I'm keen to get my teeth into something new - had my sights set on building a site like MySpace/Faceparty or whatever and promoting it before building on paid areas!

---

### Post by Aetherius on 2007-03-30
Since people here a recommending Aptana, anyone wanna help me with my installation of it? It's messed up with disposal of widgets errors and unable to get current paths errors. doesn't start. tried installing 2/3 different ways via tutorials but no luck..

---

### Post by Spr0k3t on 2007-03-30
Detail me your output of when you try to set up the application.

---

### Post by 23meg on 2007-03-30
> **Aetherius said:**
> Since people here a recommending Aptana, anyone wanna help me with my installation of it? It's messed up with disposal of widgets errors and unable to get current paths errors. doesn't start. tried installing 2/3 different ways via tutorials but no luck..

Did you read [this thread]("http://www.ubuntuforums.org/showthread.php?t=315444")?

---

### Post by dsegarra on 2007-03-30
I like to work with Firefox web developer extensions. Quick, fast and easy. In my opinion better than any WYSIWYG editor.

---

### Post by Spr0k3t on 2007-03-30
If you already have Eclipse set up and running, here is a fool proof way to install Aptana:

[http://www.aptana.com/docs/index.php/Plugging_Aptana_into_an_existing_Eclipse_configuration](http://www.aptana.com/docs/index.php/Plugging_Aptana_into_an_existing_Eclipse_configuration)

---

### Post by bvanaerde on 2007-04-01
> **TURNER said:**
> Sometimes I really cannot understand why firms purchase expensive products like Dreamweaver, when free alternatives are out there....its not logical at all.

It's even worse: when applying for a job, we often get questions like "Can you use DreamWeaver" instead of "Do you know HTML"...

---

### Post by Pathan on 2007-06-03
NVU is a good editor in a glance. i just installed it. Lets check how powerful and  friendly it is.

---

### Post by port on 2007-07-29
Out of all the editors I've tried out,  NVU, Aptana, Amaya, and Bluefish, I really like Quanta + . One thing I really like about it is.. and Im not sure if you can do this in the other editors but you can add custom actions. So you can make an action for tags or scripts you write a lot that aren't on the default actions like insert image or insert table, then you can click that action and it will insert the tag or script for you , you just fill in the properties.

---

