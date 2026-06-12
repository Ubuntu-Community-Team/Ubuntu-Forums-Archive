---
title: "Request for Alternative main-menu"
date: 2005-11-20
forum: Art &amp; Design
---

### Post by Malphas on 2005-11-20
Just repeating what I said [here]("http://www.ubuntuforums.org/showpost.php?p=507879&postcount=126").  When I install Ubuntu on people's PCs, one of the first things I do is arrange the Gnome desktop so it's more intuitive to people that have experience with Windows.  I'd like to replace the default main-menu icon with something more like this:

[IMG]http://img.photobucket.com/albums/v113/LoboParamilitary/ubuntumain.png[/IMG]

Obviously, that's appalling, I'm no good at this sort of thing so I just did a quick mock-up that gives you some idea of what it is I'm talking about; basically a similar idea to the start menu in Windows XP or Vista but retaining some of the Ubuntu theme.  A glassy sort of look would be cool, but I have no idea how to do that.  If anyone feels like designing something along these lines you'd be doing me a big favour.

---

### Post by commodore on 2005-11-22
Why should Ubuntu be more like Windows? Maybe Windows should look like GNOME a bit more so Ubuntu users could switch to Windows? Ubuntu is not Windows so this is not needed. And it is not hard to find out where the main menu is located.

---

### Post by Malphas on 2005-11-22
*sigh*  Grow up.

---

### Post by kperkins on 2005-11-22
The easist way to replace it is by taking your image and replacing /usr/share/icons/highcolor/48x48/apps/distributor-logo.png
Like this:

---

### Post by kperkins on 2005-11-22
While _I_ don't want my Ubuntu to look like Windows _You_ can do whatever you please. That's what _free_ software is all about. :D

---

### Post by Malphas on 2005-11-22
[QUOTE=kperkins]The easist way to replace it is by taking your image and replacing /usr/share/icons/highcolor/48x48/apps/distributor-logo.png
Like this:[/QUOTE]
Yeah I know how to do this, perhaps I wasn't completely clear, what I was asking is whether someone that's skilled at graphic design would consider making a better version of the image I made.  I guess it might sound a little arrogant to ask someone to do that for nothing in return but I only meant they this is something they could do if they wanted, which might be of use to others as well as myself.

[QUOTE=kperkins]While _I_ don't want my Ubuntu to look like Windows _You_ can do whatever you please. That's what _free_ software is all about. :D[/QUOTE]
Yes, exactly.

---

### Post by kperkins on 2005-11-22
[QUOTE=Malphas]Yeah I know how to do this, perhaps I wasn't completely clear, what I was asking is whether someone that's skilled at graphic design would consider making a better version of the image I made.  I guess it might sound a little arrogant to ask someone to do that for nothing in return but I only meant they this is something they could do if they wanted, which might be of use to others as well as myself.
[/QUOTE]
Give me a feww and I'll see what I can do.

---

### Post by kperkins on 2005-11-22
Here:

---

### Post by tanari on 2005-11-23
I hate win start button. GNOME menu is very **convenient**

---

### Post by commodore on 2005-11-23
Grow up? I didn't do anything bad. I thought you want to replace the one that's installed by default. That would be a badie. Sorry if I understood wrong.

---

### Post by GazaM on 2005-11-23
I played around with making the a Windows like Main menu button before (not for myself, I like normal gnome layout, but for people who were stuck in the windows way of doing things). The main problem I faced is that there is no way that I know of to remove that little black arrow which appears on the main menu button... VERY annoying. By the way, the proper way to change it would be going into gconf and setting the button there instead of replacing the icon in the theme. If anyone knows how to remove the black arrow PLEASE tell us!

---

### Post by kperkins on 2005-11-24
Where in gconf do you replace it?

---

### Post by GazaM on 2005-11-25
To change the main menu icon using gconf:
go to apps > panel > objects
look for the object with object_type : menu-object
select use_custom_icon and in the custom_icon field enter the location of the icon.

This only works with the 'Main-menu', but this is what I assume you guys want if you are looking for one button for the menu to help ease Windows users in. That little black arrow is so agitating though and pretty much ruins the whole effect, as it doesnt even move to the edge of your button, it always stays in the same position, so on a normal wide button it is right in the middle, very off-putting to say the least. Please tell us how to remove it, and if it's not possible it should be in Gnome 2.14 because it is a trivial feature.

---

### Post by kperkins on 2005-11-25
Thanks for that (learn something everyday), you don't even have to do a killall gnome-panel to see it. :D

I like playing with customizing icons, (though, really, the one I did for the OP is kinda guady for my taste) and that's much easier than mv-ing stuff to the /blah/blah/blah/blah/blah/blah/ folder. :D

As for the arrow, yeah it is kinda off-puting, and not really necessary anyways.

---

### Post by kperkins on 2005-11-25
More on the arrrow.
Seems that gnome developers think that it's user friendly for people coming over from other OSes (see: [http://developer.gnome.org/projects/gup/ut1_report/exploring_desktop.html](http://developer.gnome.org/projects/gup/ut1_report/exploring_desktop.html) )
Which is ridiculous, since the menu bar, and not the main menu, is standard default for gnome panel.  Those distros that use the main menu as default set it up so it's more obvoius anywys.
As for changing it, the only way I've found is to recompile the gnome panel source. (see here: [http://forums.gentoo.org/viewtopic.php?t=121973](http://forums.gentoo.org/viewtopic.php?t=121973) --the instructions are for gentoo, and g-p 2.4, but I think they'd work for 2.12, and Ubuntu, if any one was really that bothered by it.)

---

### Post by GazaM on 2005-11-25
That page on Gnome usability is back in the Gnome 1 days... it's ridiculous that this is still not customisable. I'm not that comfortable with compiling essential stuff like gnome either.

My suggestion would be to file a bug report, if there is none on this already. I'm gonna check it out later when I get the time.

---

### Post by Malphas on 2005-11-30
Hate to bump an old thread but did anyone ever file a bug report on this?  I couldn't find one over at Gnome's Bugzilla.

---

### Post by opticyclic on 2006-03-04
Thank the glory of searching for bringing up this thread from last year ;) 
[QUOTE=Malphas]
.....
 I'd like to replace the default main-menu icon with something more like this:

[IMG]http://img.photobucket.com/albums/v113/LoboParamilitary/ubuntumain.png[/IMG]

Obviously, that's appalling, I'm no good at this sort of thing so I just did a quick mock-up that gives you some idea of what it is I'm talking about;
....
  If anyone feels like designing something along these lines you'd be doing me a big favour.[/QUOTE]

I actually quite like what you have done and am using it now! :) 

Perhaps there should be a contest to see who can design the best/most intuitive main menu icon :-k

---

### Post by lzfy on 2006-03-06
You can use mine if you still need it :)

[IMG]http://img337.imageshack.us/img337/8248/main21wl.png[/IMG]
[IMG]http://img337.imageshack.us/img337/421/main17en.png[/IMG]

---

### Post by Ahriman on 2006-03-06
NICE :)
/me grabs and runs away

cheers, man, they are awesome!

---

### Post by GazaM on 2006-03-06
Nice work Izfy... now if only that little arrow would go away! It's a wonder that bug wasn't sorted months ago. :P

---

### Post by opticyclic on 2006-03-07
[QUOTE=lzfy]You can use mine if you still need it :)

[IMG]http://img337.imageshack.us/img337/8248/main21wl.png[/IMG]
[IMG]http://img337.imageshack.us/img337/421/main17en.png[/IMG][/QUOTE]

Those are reeeaal sweeet! :p

---

### Post by lzfy on 2006-03-07
Tnx guys :)  I think I'll create some more ;)

---

### Post by Ubuntuud on 2006-03-08
Here is mine. It's just a beginning (from a beginner), but I don't want to make it to complicated either, please give yout opinion. I like it, that is one positive vote.

---

### Post by Ubuntuud on 2006-03-08
Oops, something happened with the shadow (to short). I'll correct it, please wait till tomorow.

---

### Post by byen on 2006-03-08
[QUOTE=lzfy]You can use mine if you still need it :)

[IMG]http://img337.imageshack.us/img337/8248/main21wl.png[/IMG]
[IMG]http://img337.imageshack.us/img337/421/main17en.png[/IMG][/QUOTE]
very neat! great job dude!

---

### Post by Ahriman on 2006-03-08
[QUOTE=lzfy]Tnx guys :)  I think I'll create some more ;)[/QUOTE]
Yes Please! :D

---

### Post by lzfy on 2006-03-08
Ok I made two more but I don't know if they're really usefull... but hey they look good right :o 

[IMG]http://img88.imageshack.us/img88/8334/ubuntu9ec.png[/IMG]

[IMG]http://img530.imageshack.us/img530/2131/kubuntu7cu.png[/IMG]
[IMG]http://img130.imageshack.us/img130/5659/kununtu5hv.png[/IMG]

---

### Post by WackToMack on 2006-03-14
I still can't figure out how to change the "Applications" button to one of the ones you boys made. :confused:   Can somebody give me a quick tutorial or something?  Thanks in advance! :D

---

### Post by opticyclic on 2006-03-14
Did you try GazaMs method in this thread?
[http://ubuntuforums.org/showpost.php?p=519310&postcount=13](http://ubuntuforums.org/showpost.php?p=519310&postcount=13)

---

### Post by Malphas on 2006-03-14
Excellent work, lzfy.

---

### Post by kaamos on 2006-03-14
Here is another quick mockup. This should go pretty well with the most Gnome themes
with Tango icons.

[IMG]http://users.tkk.fi/~alaisi/valiaika/menu.png[/IMG]

Attached is the image in png plus the gimp file so you can change the text to your language
or something else entirely. Instructions how to change the image are (again) [here](http://ubuntuforums.org/showpost.php?p=519310&postcount=13).

---

### Post by stanz on 2006-05-04
[quote=kperkins]The easist way to replace it is by taking your image and replacing /usr/share/icons/highcolor/48x48/apps/distributor-logo.png[/quote]
[B]It might be well know- to others.. but i'll say= "Rename the origanal to "old_", or something!
I named it the same and figure i lost it...so to keep it- rename it!"[/B]
 And thats all good...`cept...if your replacement is long or large- it messes up the panel arrangement.
**lzfy's** icons are kewl- but small on the panal...And also- it's needed to change or _get rid of_ default= "Applications - Places - System".
The 'Menu Editor' doesn't do it.
And this...
[quote=GazaM]To change the main menu icon using gconf:
go to apps > panel > objects
look for the object with obje...on so on..[/quote] Kinda took me awhile- to find you are saying..
Open file browser...enable 'show hidden files'...find .gconf in home folder...& don't freak
when things look different!
I see "object_0 thru _7" leading to   xml's...can i insert a 'Dhaaa' here?
:cool:

I'll attach a panal snapshot - notice to the center.. to the right of FFox icon.
I think just having the kewl icon...is enough!

---

### Post by s|k on 2006-07-03
[QUOTE=GazaM]To change the main menu icon using gconf:
go to apps > panel > objects
look for the object with object_type : menu-object
select use_custom_icon and in the custom_icon field enter the location of the icon.

This only works with the 'Main-menu', but this is what I assume you guys want if you are looking for one button for the menu to help ease Windows users in. That little black arrow is so agitating though and pretty much ruins the whole effect, as it doesnt even move to the edge of your button, it always stays in the same position, so on a normal wide button it is right in the middle, very off-putting to say the least. Please tell us how to remove it, and if it's not possible it should be in Gnome 2.14 because it is a trivial feature.[/QUOTE]
I tried looking for 'menu-object' but all I found was 'menu-bar' with gconf-editor

---

### Post by Iandefor on 2006-07-04
[quote=Ubuntuud]Here is mine. It's just a beginning (from a beginner), but I don't want to make it to complicated either, please give yout opinion. I like it, that is one positive vote.[/quote] Ignoring the shadow, it looks alright. One thing: serifs don't go well with a lot of things... in fact, the only instance where they tend to look good is in the main text of a document (imho).

---

### Post by Iandefor on 2006-07-04
[quote=lzfy]You can use mine if you still need it :)

[IMG]http://img337.imageshack.us/img337/8248/main21wl.png[/IMG]
[IMG]http://img337.imageshack.us/img337/421/main17en.png[/IMG][/quote] Nice work. Using it with standard-size GNOME panels, it looks a little small. Do you still have the work file you used (I assume xcf?) so I can edit it more to my liking?

EDIT: Nevermind. I got rid of the alpha-transparency borders, which were making it too small.

---

### Post by opticyclic on 2006-07-19
I had it working in GNOME alright.
How do I achieve the same result in KDE?

---

### Post by PingunZ on 2006-07-20
[http://ubuntuforums.org/showthread.php?t=215970](http://ubuntuforums.org/showthread.php?t=215970)

---

### Post by themerchant on 2006-11-26
I use configuration editor, and I worked most of it out, however when I finally come to apply it, a question  mark is replaced over the main menu bar, and the computer says that (image location) is not found.

---

### Post by themerchant on 2006-11-26
bump help^

---

### Post by brokencrystal on 2006-12-30
> **GazaM said:**
> To change the main menu icon using gconf:
go to apps > panel > objects
look for the object with object_type : menu-object
select use_custom_icon and in the custom_icon field enter the location of the icon.

This only works with the 'Main-menu', but this is what I assume you guys want if you are looking for one button for the menu to help ease Windows users in. That little black arrow is so agitating though and pretty much ruins the whole effect, as it doesnt even move to the edge of your button, it always stays in the same position, so on a normal wide button it is right in the middle, very off-putting to say the least. Please tell us how to remove it, and if it's not possible it should be in Gnome 2.14 because it is a trivial feature.


I HATE that stupid little black arrow!!!  There should be an option in the gconf configuration editor to remove that annoyance!

---

### Post by vgramanathan on 2007-02-06
is there a way to label the gnome main menu with something like 'Main' and not just have the distributor's logo

---

### Post by vgramanathan on 2007-02-10
Check out this:

Start button with Ubuntu logo on a black background
Hides the arrow on the main menu automatically
Replace your custom icon of main menu object in gconf-editor with this image

[IMG]http://www.freewebs.com/vgramanathan/start.png[/IMG]

[http://www.freewebs.com/vgramanathan/start.png](http://www.freewebs.com/vgramanathan/start.png)

---

