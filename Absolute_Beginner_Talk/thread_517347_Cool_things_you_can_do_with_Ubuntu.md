---
title: "Cool things you can do with Ubuntu?"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Phluxed on 2007-08-04
Hi everyone,

I know I know... it seems lame.

I've recently been wanting to switch to Ubuntu full time. I find myself more and more inclined to do so. I got WoW and WC3 Frozen Throne working in Ubuntu with Wine, I've imported all my bookmarks... not a big time fan of GAIM, looking for a new messenger - Mostly for MSN messenger, and Beryl when used properly is more than just fancy, its very efficient.

I am wondering what you guys consider some of the cooler sides of Ubuntu, not just Linux. I've enjoyed the add/remove options, are there some other repositories with more open source software? Are there some cool apps that can seriously change the look of the OS? What other gui customizations are there out there? 

Some sort of desktop computer monitoring information I can have embedded into my desktop?

I've enjoyed trying to get my wireless adaptor working, I was able to do it with Ndiswrapper, which was very neat and a great learning experience. Any sort of neat little tricks or suggestions would be very much appreciated!

---

### Post by Brunellus on 2007-08-04
Consider getting a desklets package-- gdesklets or adesklets.   Also consider conky--a system monitoring program that looks cool and is almost infinitely configurable--if you learn how to hack it. 

Learn vim.  It's a ruthlessly efficient text editor.

Learn to live without X.  I find the default terminal font and keymapping for Ubuntu to be a pain;  hints on how you can customize these are [here](http://ouij.livejournal.com/207594.html).

---

### Post by RudolfMDLT on 2007-08-04
Install Kopete as an IM. Also install superkaramba for some cool desklets.

---

### Post by Acglaphotis on 2007-08-04
Install Amsn or Emesene.

---

### Post by nitro_n2o on 2007-08-04
> **Brunellus said:**
> Consider getting a desklets package-- gdesklets or adesklets.   Also consider conky--a system monitoring program that looks cool and is almost infinitely configurable--if you learn how to hack it. 

Learn vim.  It's a ruthlessly efficient text editor.

Learn to live without X.  I find the default terminal font and keymapping for Ubuntu to be a pain;  hints on how you can customize these are [here](http://ouij.livejournal.com/207594.html).
the ultimate fun is living without X :) thumbs up

---

### Post by Phluxed on 2007-08-04
i dont know what this living without x is... anyone care to explain?

---

### Post by tprzepiorka on 2007-08-04
> **Acglaphotis said:**
> Install Amsn or Emesene.

Not sure about Emesene, but aMSN is great if you're using used to using MSN Messenger. Try to get RC1 from their [website]("http://www.amsn-project.net/"). Also I suggest you check out [this]("http://ubuntuforums.org/showthread.php?p=2307772") thread to find a bunch of great things to install. I really enjoy using AWN, which is a dock.

Other cool things I love about Ubuntu is how you can customize it so much, the updates, and of course the obvious benefits about about cost, security, and performance.

---

### Post by Brunellus on 2007-08-04
> **Phluxed said:**
> i dont know what this living without x is... anyone care to explain?
X is short for the Xwindows system--your graphical user interface.  Living without X means living in the command-line ONLY.

---

### Post by Phluxed on 2007-08-04
> **Brunellus said:**
> X is short for the Xwindows system--your graphical user interface.  Living without X means living in the command-line ONLY.

Oh.. lol as much as I love the idea :P I think I'll stick with the GUI. Learning the command line does seem useful though.

---

### Post by Brunellus on 2007-08-04
> **Phluxed said:**
> Oh.. lol as much as I love the idea :P I think I'll stick with the GUI. Learning the command line does seem useful though.
Command-line time is never wasted.  I have an old laptop here at the house that I use as a command-line machine (mostly);  I find that for certain tasks, the console is really much more efficient.

---

### Post by Phluxed on 2007-08-04
Well, I managed to learn a lot from ndiswrapper's install alone. I wasn't able to auto install it as I had no connection to the box, and therefore I had to do it all command line pretty much. Was the only way I could get it working.

---

### Post by happy-and-lost on 2007-08-04
Screenlets and Avant-Window-Navigator for serious composite eye-candy.

But whatever you do... never *ever* try out Battle For Wesnoth when you have important things to do.

---

### Post by Phluxed on 2007-08-05
Can you maybe give some examples? Home computers seem to be moving away from command line, as displayed by Ubuntu. It's a very user friendly distro of Linux which seems to make it very popular.

Also, keep the ideas coming! :)

---

### Post by nichipet on 2007-08-05
Examples of eye candy? Your best bet is go to YouTube or any other video hosting website and search for Beryl, Compiz, or Compiz Fusion.

---

### Post by Phluxed on 2007-08-05
I actually had meant some examples of where command line only is more useful on a desktop computer.. 

Also, I mentionned I have beryl running.

---

### Post by nichipet on 2007-08-05
> **Phluxed said:**
> I actually had meant some examples of where command line only is more useful on a desktop computer.. 

Also, I mentionned I have beryl running.

Oops! my mistake. I don't know about specific examples, but I know some reasons for why command line is better.

1. No graphics to have a glitch or bug. Sometimes programs crash because of graphical issues. No graphics, no crashes from graphics.

2. Faster. In a similar way, the commands don't have to pass through the graphical interface, they go directly to the system and process quicker.
 
3. More customization. It's not uncommon for programs to have options available only from the command line, or just as easily accessible from the command line.

4. Integration with shell scripting. For example, a script/program to download a website, compare the contents to an old copy of the webpage, assemble a new webpage with annotated differences can certainly be done graphically, but it's fairly easy in command line. Just thinking through it while writing this, I can come up with a skeleton that would be a few steps toward the finished product, all in shell scripting (if anyone is curious, I'm figuring wget the webpage, mv it to a unique file name, diff the two files into a new file, and cat/echo with >> to build a new file).

Ultimately, it's a matter of simplicity. Graphical software is always getting better, but simplified software (sans graphics) that has fewer chances of causing problems while still giving the same features will always trump graphical interfaces for programming, speed, and customization.

---

### Post by Dr Small on 2007-08-05
> **tprzepiorka said:**
> Not sure about Emesene, but aMSN is great if you're using used to using MSN Messenger. Try to get RC1 from their [website]("http://www.amsn-project.net/"). Also I suggest you check out [this]("http://ubuntuforums.org/showthread.php?p=2307772") thread to find a bunch of great things to install. I really enjoy using AWN, which is a dock.

Other cool things I love about Ubuntu is how you can customize it so much, the updates, and of course the obvious benefits about about cost, security, and performance.
I've been trying to figure out how to install AWN on Dapper. any suggestions?

---

### Post by Hobo Joe on 2007-08-05
[Blender]("http://www.blender.org/features-gallery/gallery/images/")

You'll be glad you did. :)


[http://blendernewbies.blogspot.com/](http://blendernewbies.blogspot.com/)
[http://blenderartists.org/cms/index.php](http://blenderartists.org/cms/index.php)

---

### Post by asmoore82 on 2007-08-05
> **nichipet said:**
> Oops! my mistake. I don't know about specific examples, but I know some reasons for why command line is better.

1. No graphics to have a glitch or bug. Sometimes programs crash because of graphical issues. No graphics, no crashes from graphics.

2. Faster. In a similar way, the commands don't have to pass through the graphical interface, they go directly to the system and process quicker.
 
3. More customization. It's not uncommon for programs to have options available only from the command line, or just as easily accessible from the command line.

4. Integration with shell scripting. For example, a script/program to download a website, compare the contents to an old copy of the webpage, assemble a new webpage with annotated differences can certainly be done graphically, but it's fairly easy in command line. Just thinking through it while writing this, I can come up with a skeleton that would be a few steps toward the finished product, all in shell scripting (if anyone is curious, I'm figuring wget the webpage, mv it to a unique file name, diff the two files into a new file, and cat/echo with >> to build a new file).

Ultimately, it's a matter of simplicity. Graphical software is always getting better, but simplified software (sans graphics) that has fewer chances of causing problems while still giving the same features will always trump graphical interfaces for programming, speed, and customization.

add a #5 ...
If you know how to get it done with just the command line, you can do it just as fast from anywhere in the world securely over SSH. while you can forward X GUI apps over SSH, they are not quite as responsive over a home uplink.

---

### Post by nichipet on 2007-08-05
> **asmoore82 said:**
> add a #5 ...
If you know how to get it done with just the command line, you can do it just as fast from anywhere in the world securely over SSH. while you can forward X GUI apps over SSH, they are not quite as responsive over a home uplink.

That's a good point. With some exceptions, if you know how to do it in one shell environment, you can do it in any shell environment. It's not like graphical programs where you might be an expert with Maya but practically have to start over to learn Blender in Linux (do you? I wouldn't know having never used Maya and just mulling over trying some Blender tutorials, it's just an example with names plugged in).

For the record, I use Ubuntu Studio with full graphics (still trying to get Compiz/Beryl to work, close but not yet), but I go to the command line quite often if I think a shell script will do the job.

---

### Post by Phluxed on 2007-08-05
Well, that all makes sense.

I can understand it entirely. That's all about learning Linux and the likes - I'm getting used to Ubuntu because I want to get so used to it, I can swap all the computers in my home to it (6 boxes + a media server). I am concerned about the swap due to compatibility.  My fiance plays WoW a lot, my sister who lives with us is all about how pretty the mac looks etc, and I am working on convincing everyone its a viable switch. I'm trying to put together the best possible looking OS that is low footprint and low usage to show to them so they are for it :)

I saw a page about switching the system over to a mac look entirely, which I think sis would dig, and I played WOW on Ubuntu last night, so my fiance is closing in on letting the switch happen. I am, for my own curiousity trying to put together some cool stuff Windows does not have whilst learning in the process :) 

As great as the command line is, it seems I should learn it more as I go from the GUI than straight command line hammering, which also seems to be a trend that is developing from Ubuntu... 

That being said, KEEP EM COMING :) !

---

### Post by Brunellus on 2007-08-06
> **Phluxed said:**
> Well, that all makes sense.

I can understand it entirely. That's all about learning Linux and the likes - I'm getting used to Ubuntu because I want to get so used to it, I can swap all the computers in my home to it (6 boxes + a media server). I am concerned about the swap due to compatibility.  My fiance plays WoW a lot, my sister who lives with us is all about how pretty the mac looks etc, and I am working on convincing everyone its a viable switch. I'm trying to put together the best possible looking OS that is low footprint and low usage to show to them so they are for it :)

I saw a page about switching the system over to a mac look entirely, which I think sis would dig, and I played WOW on Ubuntu last night, so my fiance is closing in on letting the switch happen. I am, for my own curiousity trying to put together some cool stuff Windows does not have whilst learning in the process :) 

As great as the command line is, it seems I should learn it more as I go from the GUI than straight command line hammering, which also seems to be a trend that is developing from Ubuntu... 

That being said, KEEP EM COMING :) !
you learn nothing from the GUI except how to move a mouse pointer and click.  The command line is where all the real work gets done.  When everything else on your box fails, you have the terminal.  

Recommendation:  buy a good book and read through it while forcing yourself to learn the shell as much as possible.

---

