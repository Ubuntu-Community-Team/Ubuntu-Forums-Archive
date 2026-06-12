---
title: "Multimedia HELL (Totem go home!)"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by mybootorg on 2006-05-05
Ok, I give up. I don't get it.  Why are multimedia and file associations such a complete pain the arse in Ubuntu -- when everything else is so relatively simple?

Example.  I have an XVid of last week's Lost TV episode on my desktop in avi/xvid format.  If I click on it, the ever helpful, overachieving Totem tries to launch and then throws an error because it doesn't support the format.  Thanks Totem, would you mind buggering off please?

I right click on the file, choose Properties, then the "Open With" tab.  There are nice radio buttons here that appear to let me set the default app for this file format.  Except that if I try to change it, I find they're pretend Fischer-Price buttons.  They do not work.  (The same goes if I'm logged on as root.)

So I google Ubuntu file associations and learn about the defaults.list file. I replace every occurance of Totem with Kaffeine - my multimedia favorite so far.  I killall gnome-panel and nautilus to make sure it sticks...  click on my Lost episode and... Totem comes up and throws another error.  AHHH!

I'd up and uninstall Totem at this point just to be rid of it.  Cept, as you know, it's tied into Gnome desktop and I'd have to uninstall that too, according to Synaptic.

Anyone have any suggestions?

---

### Post by dermotti on 2006-05-05
Do you have the Xvid codec installed?

---

### Post by joshrobinson on 2006-05-05
totem is a piece of poop for me to

try mplayer or vlc.. they should be in the repositories
you will need to grab the win32codecs for mplayer to make sure the file works

---

### Post by dermotti on 2006-05-05
[http://www.ubuntuforums.org/showthread.php?t=138889&highlight=multimedia+script](http://www.ubuntuforums.org/showthread.php?t=138889&highlight=multimedia+script)

This script worked wonders for my multimedia woes

---

### Post by mybootorg on 2006-05-05
Hey guys,

To clarify, yes, I have the XVid codec installed. I can choose Open With Kaffeine and the file plays just fine.  **It's the DEFAULT APPLICATION (association) for this file type that's become such a pain in the butt for me.**  Totem won't get lost.  Nor can I promote Kaffeine (my favorite movie app) to be default using any of the documented methods.

Off topic PS: I've used mplayer on my Pocket PC before -- it's fantasic.  Except in Ubuntu, for whatever reason, the video stutters.  Kaffeine just works.

---

### Post by nanotube on 2006-05-05
well, try
```
sudo apt-get install totem-xine
```
that oughtta fix you up and make totem actually play it. :)

as to the default applications - when you right click on your file, select properties, go to the openwith tab, and there select the app that you want to be the default. but dont just "select" it - make sure to click the actual radio button. otherwise it doesn't /actually/ select it. are you sure you did that?

---

### Post by mybootorg on 2006-05-05
Thanks. Totem-xine cleared up many of the totem errors.  However, let's say I like Kaffeine enough and am fed up enough with Totem that I want Kaffeine to handle most video types?  How do I make totem go away?

When I right click on a file, choose properties, then the "Open With" tab, sometimes there are radio buttons, sometimes there are not. Seems random to me.  But when there are radio buttons, I cannot seem to affect them in any way no matter how much I clickity-click.

I must be affecting them though, because suddenly my desktop XVid file is opening with Kaffeine as I'd been failing to accomplish earlier tonight.

Question though - when I put a commerical DVD into my DVD player and closer 'er up, guess who autoplays my DVD?  That's right.  That damned Totem guy.

Totem is no longer in my Default.list.  I can't perform a Properties / "Open With" on an inserted DVD.  So how do I make Totem turn loose of this too?  And have Kaffeine auto-play my DVDs?

---

### Post by mybootorg on 2006-05-05
Ok, I found yet another place where multimedia application defaults live.... *sigh*

Here's the solution, sort of:

Go to Applications / System Tools / Configuration Editor

Tree down to:

desktop > gnome > volume manager

Scroll down in the right panel and you'll see all kinds of autoplay defaults... many of them being bogarted by none other than Mr. Totem.  Damn him...

Thanks for the help, folks.

PS: Kaffeine has a bug where it won't autoplay DVDs.  So don't bother trying to 'kaffeine -p -d /dev/cdrom' because it's not going to work.  Be satisfied that by entering kaffeine as the default autoplay, at least it pops up and you're one click away from watching your movie.

---

### Post by ade234uk on 2006-05-05
Why are codecs such a load of poop? The reason like many other things is Microsoft own some of them and therefore they cannot be automatically installed.

Why dont you try Automatix, you can install the lot with this little beauty.

---

### Post by mybootorg on 2006-05-05
[QUOTE=ade234uk]Why are codecs such a load of poop? The reason like many other things is Microsoft own some of them and therefore they cannot be automatically installed.

Why dont you try Automatix, you can install the lot with this little beauty.[/QUOTE]

Well, the purpose of this post... and reading back through I guess I didn't do a very good job of making it clear... was to inquire why it's so tough to change the default application that launches for a given file type.

To be fair, this is still kind of a pain in Windows XP to this day.  The settings window for doing so can be a little confusing because for each file type there can be a number of varying action such as Open and Play.  And just like Linux, each application may require special command line switches to make either of those actions happen.

As much as I love Ubuntu, if it's going to succeed at being "Linux for Human Beings" then it's going to need a GUI System Administration applet that:

1) Allows you to see what programs are launched by default for a given file type.  Offers you the known installed programs that are alternatives.  And allows you to edit and change them easily.

2) Allows you to see autoplay default applications in the same way.  And easily change them.

A one-stop-shop for file associations and default apps, if you will. As opposed to the two different places mentioned in my post and the somewhat dubious File / Properties / "Open With" method.

Now as for codecs, codecs are somewhat of a problem in Windows as well.  Take all the variations of DiVX as one good example.  These video files will not play in Windows Media Player.  WMP will offer to download the codec, then error out.  And unless you happen to know what DiVX is and Google a download source, you're up a creek without a paddle.

I used Automatix early on to find everything I needed.  And since then, I've found several scripts people have written that download and install every codec you could possibly need, and workarounds for problem codecs as well.  There are a couple three of them floating around.

---

### Post by Jason_25 on 2006-05-05
It's not hard to do.  Right click the file. Go to properties.  Choose the file type tab :rolleyes:

---

### Post by mybootorg on 2006-05-05
[QUOTE=Jason_25]It's not hard to do.  Right click the file. Go to properties.  Choose the file type tab :rolleyes:[/QUOTE]

Au contraire, Pierre... :rolleyes: The actual method is Right click on file / Properties / Open With.

Then if you're lucky, you see the possible applications that can handle the file.  If you're lucky, you have radio buttons next to each application that look like you can click them and change the association.

If you're like me, these radio buttons don't work -- or for some reason they're not there.  Clicking on them seems to suggest they're pretend as you can't seem to get them to change -- along the lines of a toy dashboard for a car with a steering wheel and horn.  You can do all the honking and steering you want but you're still sitting on the floor going nowhere.

Even if you are successful in making a change under Properties/ "Open With", the old default *may still launch* because it's cached somewhere in the OS and you'll have to killall gnome-panel and nautilus to make the change stick.

This is not "for human beings".  Just suggesting that so that it can be improved.

---

### Post by Jason_25 on 2006-05-05
I haven't seen any of the problems you described.  It's childishly simple as is.

---

### Post by zerhacke on 2006-05-05
[QUOTE=mybootorg]Au contraire, Pierre... :rolleyes: The actual method is Right click on file / Properties / Open With.[/QUOTE]
There IS a way to do exactly what Jason25 said.  There's an open with tab on the properties menu.  It works perfectly fine for me, too.

---

### Post by patrick295767 on 2006-05-05
Try my script from here : [http://www.ubuntuforums.org/showthread.php?t=160070](http://www.ubuntuforums.org/showthread.php?t=160070)   or [http://www.ubuntuforums.org/showthread.php?t=157589](http://www.ubuntuforums.org/showthread.php?t=157589)
You 'll see how much u 'll like totem :-) 

Greetz

---

### Post by mybootorg on 2006-05-05
[QUOTE=Jason_25]I haven't seen any of the problems you described.  It's childishly simple as is.[/QUOTE]

Childishly simple?  Maybe for someone that's been using Ubuntu or some other Linux for a long time.

The fact of the matter is that file associations in Ubuntu are anything but childishly simple.

Example: if I want Kaffeine to be my default DVD player and for autoplay too, here's what I have to do:

First off, you cant right click on the DVD icon on the desktop and associate it with anything.  With me so far?

Second, you might think you need to edit your defaults.list. So you make the adjustments there.

If you think you're done, you're not. Because the Autoplay portion of the file association is kept by the Configuration Editor.

Even after trying to change the association from three different angles, you may not be done.  Nautilus or gnome-panel may be caching the old association so you have to killall both.

Does all of the above seem childishly simple to you?  Comfortable that all of your non-Linux using friends could pick this up and figure it out in 5 minutes?

Keep an open mind. What's childishly simple for you, is not childishly simple for everyone.  That does not make you a genius necessarily, but it does mean you've had far more experience with Ubuntu.

And PS: I guess I'm the only person with the radio buttons problem under File Properties / Open With.  But it's followed me from Breezy to Dapper.  I guess I'll have to go with a fresh install when Dapper gets out of beta.

---

### Post by remarks on 2006-05-07
I'm hearing what you are saying.  My searching for the same problem has lead me to your post.  Totem has taken over all my audio associations even though I prefer a couple of other apps.  I can easily right button on the file and go to "open with" and the desired app will be used but that option doesn't become the default for the next time I open the same file type again.

---

