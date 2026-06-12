---
title: "Any way to change the Main Menu icon??"
date: 2007-02-01
forum: Art &amp; Design
---

### Post by mattmagician on 2007-02-01
I'm working on a Vista theme and was wondering if there was any way to edit the main menu icon so i can edit it. thanks
(see pic for my theme so far and the icon in question)

---

### Post by bruenig on 2007-02-01
The main menu icon is located at /usr/share/icons/hicolor/48x48/apps/distributor-logo.png

---

### Post by mattmagician on 2007-02-01
when i try to save it it says:
permission denied.

how do i save it then?

---

### Post by BoneSaw on 2007-02-01
are you trying to save it as root?

---

### Post by bruenig on 2007-02-01
To move the old icon out of the way
```
sudo mv /usr/share/icons/hicolor/48x48/apps/distributor-logo.png /usr/share/icons/hicolor/48x48/apps/distributor-logo.png.old
```

To put the new icon in
```
sudo mv /path/to/new/icon /usr/share/icons/hicolor/48x48/apps/distributor-logo.png
```

---

### Post by jincast90 on 2007-02-03
I've always wondered about this myself. I wish there was an easier way to change it though.. I'll probably try it out soon.

---

### Post by mattmagician on 2007-02-03
Figured i'd share the end result. now im working on the trash bin.

---

### Post by funkenstein on 2007-02-06
hey there, how's the theme coming along? When can we have a shot at it? And where will it be available from?

cheers, yme.

---

### Post by ComplexNumber on 2007-02-06
> **mattmagician said:**
> Figured i'd share the end result. now im working on the trash bin.
you will have to go through all the instances of the trash icon in the theme, but its not necessary for you to change the linked trash icons.

---

### Post by lavaramano on 2007-02-06
i wonder why in the world would ANY gnu/linux user use a Windows Vista Theme?
i mean, you must be insane or something to do something like that..

besides, isn't *illegal* to make a theme like this? 
(windows logo, etc etc, i think that has copyright or something similar.)

---

### Post by CarpKing on 2007-02-07
> **lavaramano said:**
> besides, isn't *illegal* to make a theme like this? 
(windows logo, etc etc, i think that has copyright or something similar.)

It isn't illegal at all.  However, distributing it (i.e. giving it to the rest of us) very well might be.

---

### Post by kalel on 2007-02-07
these are buttons that i made for the main menu in gnome.

To use you have to edit wiht gconf-editor

/apps/panel/objects/

find the object wiht the name "menu-object" an set the path to the button.png (or the others buttons) in custom_icon and checl use_custom_icon

---

### Post by Garyu on 2007-02-09
> **kalel said:**
> these are buttons that i made for the main menu in gnome.
To use you have to edit wiht gconf-editor
/apps/panel/objects/
find the object wiht the name "menu-object" 

I've been trying to figure out how to replace the "Applications | Places | System" text with icons... But I haven't found a way to do this. I tried looking at gconf-editor as you propose, but there is no "menu-object" in /apps/panel/objects. I tried looking around in other places, but no menu-objects. Could you make a more detailed post with instructions for Edgy Eft?

---

### Post by Oki on 2007-02-09
> **lavaramano said:**
> i wonder why in the world would ANY gnu/linux user use a Windows Vista Theme?
i mean, you must be insane or something to do something like that..

besides, isn't *illegal* to make a theme like this? 
(windows logo, etc etc, i think that has copyright or something similar.)


Because he likes it perhaps? 

Illegal; that depends on where you live. If the answer is yes, I would not be the first to tell Micrsoft that copy so much; [http://www.youtube.com/watch?v=3QdGt3ix2CQ&eurl=](http://www.youtube.com/watch?v=3QdGt3ix2CQ&eurl=)

---

### Post by Mateo on 2007-02-14
neither of the suggested methods worked for me.... help!

---

### Post by mk04 on 2007-02-16
> **bruenig said:**
> To move the old icon out of the way
```
sudo mv /usr/share/icons/hicolor/48x48/apps/distributor-logo.png /usr/share/icons/hicolor/48x48/apps/distributor-logo.png.old
```

To put the new icon in
```
sudo mv /path/to/new/icon /usr/share/icons/hicolor/48x48/apps/distributor-logo.png
``` 

I did this, but the icon did not change. I tried logging out and logging in again. No go, any ideas?

I also tried "killall gnome-panel" and I tried remove the main menu and adding back to the panel. I got nothing.

---

### Post by ComplexNumber on 2007-02-16
if the icon theme that you've selected doesn't have its own icon for the main menu, it will get it from one of the icon themes that it inherits (usually gnome, Tango, or Human(on ubuntu anyway)). th actual icon that you need to change is the start-here icon thats found in places. for example, 
/usr/share/icons/Human/scalable/places/start-here.svg
or
/usr/share/icons/Human/48x48/places/start-here.svg
or
/usr/share/icons/Human/24x24/places/start-here.svg


.....depending upon the size of the panel.




the icon(ie distributor-logo) that some of you are trying to change is a link that links to to the start-here icon.

---

### Post by wxnker on 2007-02-18
Nice suggestions and it works but is there any way to remove the small arrow above the start-here icon? I'm talking about the small default black arrow that shows that this button opens a menu.

How did you make the black panel? I like it. If possible would you share this with the rest of us? Not the icons/buttons. Just the panel (background) :D

---

### Post by lyceum on 2007-02-20
is their a way to log in as root to just edit the root files? I know that sudo is the way to go, but accessing the root files would be the easiest (and most dangerous) way.

---

### Post by ComplexNumber on 2007-02-20
> **lyceum said:**
> is their a way to log in as root to just edit the root files? I know that sudo is the way to go, but accessing the root files would be the easiest (and most dangerous) way.
'gksudo nautilus' on the commandline. anyway, what makes you think editing roots home directory is going to achieve anything?

---

### Post by lyceum on 2007-02-20
> **ComplexNumber said:**
> 'gksudo nautilus' on the commandline

Awesome, thanks! I will now go properly mess everything up :D

---

### Post by strabes on 2007-02-20
The icon's location changes depending on the icon theme you're using. See my blog post here: [http://strabes.wordpress.com/2006/10/16/change-the-menu-bar-logo-on-ubuntu-dapper/](http://strabes.wordpress.com/2006/10/16/change-the-menu-bar-logo-on-ubuntu-dapper/)

---

### Post by ComplexNumber on 2007-02-21
> **strabes said:**
> The icon's location changes depending on the icon theme you're using. See my blog post here: [http://strabes.wordpress.com/2006/10/16/change-the-menu-bar-logo-on-ubuntu-dapper/](http://strabes.wordpress.com/2006/10/16/change-the-menu-bar-logo-on-ubuntu-dapper/)
there's only 1 problem. its not the distributer-logo that is the 'root' main menu icon. its the start-here icon. if you notice, the distributer-logo is merely a link to the start-here icon.

---

### Post by naseem on 2007-02-22
hello i'd like to know how to get rid of the icon in the menu bar since I placed one I like in the texture of the bar itself, if I just remove the default icon from folder /apps/distributor-logo.png  it pops up an error icon

---

### Post by ComplexNumber on 2007-02-22
> **naseem said:**
> hello i'd like to know how to get rid of the icon in the menu bar since I placed one I like in the texture of the bar itself, if I just remove the default icon from folder /apps/distributor-logo.png  it pops up an error icon
please read the post above yours.

---

### Post by naseem on 2007-02-22
I just dont see where it sys it, if I delate the start-here icon it replaces it with an error icon something like this "?" 
I just wont to get rid of it, and live the menu bar without ubuntu icon

---

### Post by squidmaster on 2007-02-22
looks good man.
i like the vista theme i think that it's very clean.

think about changing the transparency of the task bar.

---

### Post by ComplexNumber on 2007-02-22
> **naseem said:**
> I just dont see where it sys it, if I delate the start-here icon it replaces it with an error icon something like this "?" 
I just wont to get rid of it, and live the menu bar without ubuntu icon
what icon theme are you using? i have most of the icon themes so i can look into it for you.

---

### Post by naseem on 2007-02-23
hello I have humility, but whot I wont to do is get rid of teh default icon, so that I can stay with my custo icon in the bar texture underneath, see pics

---

### Post by smellydog on 2007-02-23
> **lavaramano said:**
> i wonder why in the world would ANY gnu/linux user use a Windows Vista Theme?
i mean, you must be insane or something to do something like that..

besides, isn't *illegal* to make a theme like this? 
(windows logo, etc etc, i think that has copyright or something similar.)Well, i suppose people make a windows vista theme for the same reason they would create a Mac OS X them... just cuz they can!  I think that for the copyright infringement issue, you would have to sell it to make profit from it whereas the proceeds are not going to Microsoft.  Besides which, i do believe that Microsoft has bigger fish to fry than to worry about someone making a windows theme for their computer.  Just my thoughts...

But i am wanting to know how you changed the bottom panel to get that textured effect with the glossy black and grey.

---

### Post by smellydog on 2007-02-23
Whoops... i should have read the other two pages to this post!  so i am new!

---

### Post by ComplexNumber on 2007-02-23
> **naseem said:**
> hello I have humility, but whot I wont to do is get rid of teh default icon, so that I can stay with my custo icon in the bar texture underneath, see pics
that would mean changing the following icon to that of your chosen icon:
/usr/share/icons/gnome/scalable/places/start-here.svg


it would also mean that if you selected another icon theme (for example, PF-Icons or Human), you would have to change the start-here icon in that too. some icon themes have their own start-here icon. if they don't have one, they usually that in gnome or the icon theme that it 'inherits'. just do a search for "start-here"  on /usr/share/icons to see where they are. i have lots of icon themes, so  107 instances of the start-here  are found (but these also inlcude  different sized icons within the same icon theme)

---

### Post by naseem on 2007-02-23
hy I did a workaround I removed the menu bar and replaced with the main menu bar which has just one icon, replaced the /usr/share/icons/gnome/scalable/places/start-here.svg
with one I like better, but still it's a workaround is it possible to have just menu bar without icon?(this is what I was wondering since the beginning)


[PHP]But i am wanting to know how you changed the bottom panel to get that textured effect with the glossy black and grey.[/PHP]
if this is refered to the pics I posted, I made it with jimp, since the ubu grey logo is a png and not an svn so I couldn't  use it.
just found the logo in gnome loock org, resized it and put it in a texture of the size of the gnome bar, then I loaded it from the bar menu "left click on the bar"

---

### Post by ComplexNumber on 2007-02-23
> is it possible to have just menu bar without icon?yeah, just make your own icon that has no image and that is transparent. i've done one for you (beelieve it or not, there is actually a 128x128 icon there, but it has no image and is transparent)

---

### Post by naseem on 2007-02-24
ok that is a good idea! which program do i need:)

---

### Post by ComplexNumber on 2007-02-24
> **naseem said:**
> ok that is a good idea! which program do i need:)
i don't understand. which program to do what?

---

### Post by RawMustard on 2007-04-27
Is it hard coded in feisty?  Coz I've changed every single instance of start-here.png, start-here.svg and anything else that looks like the ubuntu logo and the damn thing is still there :(

Funny thing is, if I go to add to panel window my custome logo shows in there, but when I drag a new menu bar to my panel that damn ubuntu logo pops right back up again ](*,)

---

### Post by ComplexNumber on 2007-04-27
> **RawMustard said:**
> Is it hard coded in feisty?  Coz I've changed every single instance of start-here.png, start-here.svg and anything else that looks like the ubuntu logo and the damn thing is still there :(

Funny thing is, if I go to add to panel window my custome logo shows in there, but when I drag a new menu bar to my panel that damn ubuntu logo pops right back up again ](*,)
i've been doing some theming recently. it is the  distributor-logo(or what it points to)  is what you need to change.  in some cases, the  distributor-logo is a link to either thestart-here or gnome-main-menu icon. if you don't have a distributor logo, create it by linking to the icon that you want it to be.

---

### Post by RawMustard on 2007-04-27
Well, start-here points to distributor-logo in all the icon folders as well as novel-button.
I've also changed gnome-main-menu, I can't find another icon on my system that even remotely looks like ubuntu's and the damn thing is still there. I wonder if it might be cached somewhere?

---

### Post by ComplexNumber on 2007-04-27
> **RawMustard said:**
> Well, start-here points to distributor-logo in all the icon folders as well as novel-button.
I've also changed gnome-main-menu, I can't find another icon on my system that even remotely looks like ubuntu's and the damn thing is still there. I wonder if it might be cached somewhere?
yes, but it depends upon which distributor-logo(ie in which theme) that your current theme is using. if your theme doesn't have the distributor-logo(icon or link), then it will use that of one of the themes that it inherits. have a look in the index.theme file within the icon theme and look at the themes that it inherits. if it doesn't have a line that says "Inherits=<icon thme>", then it will use either gnome, Tango, Human, or hicolor.

---

### Post by RawMustard on 2007-04-27
I don't think you're understanding me.  I've changed every instance of distributor-logo, start-here, novel-button, gnome-main-menu, ubuntu-logo and any other ubuntu icon in every theme and every folder on my whole freaking system and it's still there  ](*,)

It has to be hard coded into the menu-bar applet.  The main-menu applet shows my icon, but the menu-bar applet shows the ubuntu icon.

---

### Post by ComplexNumber on 2007-04-28
> **RawMustard said:**
> I don't think you're understanding me.  I've changed every instance of distributor-logo, start-here, novel-button, gnome-main-menu, ubuntu-logo and any other ubuntu icon in every theme and every folder on my whole freaking system and it's still there  ](*,)

It has to be hard coded into the menu-bar applet.  The main-menu applet shows my icon, but the menu-bar applet shows the ubuntu icon.
i'm understanding you perfectly  because i understand the problem. the problem is that you're not understanding the problem. 
its not hard coded in.

---

### Post by RawMustard on 2007-04-28
Ok so let me get this straight.  If you replace every instance of the ubuntu logo icon with a different graphic but maintain the same name throughout the whole system.  for example, in every icon folder under /usr/share/icons or any theme folder under ~/.icons you rename distributor-logo.png to distributor-logo.old.png and place your own distributor-logo.png in it's place, including any other icon such as start-here.png or gnome-main-menu.png, you will still see the ubuntu icon?  I mean, if I do a search for *.png *.svg or *.xpm all instances of the ubuntu icon have been replaced with my own graphic. So where does this icon come from then?

And no, I'm not an American, there's no need for such an insult!

---

### Post by ComplexNumber on 2007-04-28
>  And no, I'm not an American, there's no need for such an insult!its not an insult, but a fact. there is obviously something that you are misunderstanding.  if there is an icon called distributor-logo in the icon theme that you are using, it will use it. the theme isn't exactly going to develop a mind of its own and decide for itself whether to use it or not. 
also, make sure that the extension is the same as the one thats used within that directory.

---

### Post by josephus on 2007-04-28
do you have to update the icon-theme.cache in order for this to work?

---

### Post by ComplexNumber on 2007-04-28
> **josephus said:**
> do you have to update the icon-theme.cache in order for this to work?
no. the icon-theme-cache is there just to speed up the laoding of the icons in the theme.

---

### Post by josephus on 2007-04-28
another solution to this is to create your own custom theme which includes only the distributor logo icon and then make it inherit the rest of icons from the theme you normally use.

---

### Post by alterpinguin on 2007-04-28
> **ComplexNumber said:**
> no. the icon-theme-cache is there just to speed up the laoding of the icons in the theme.

some people may say it is not hardcoded - but i would do so. I had to update the icon-theme.cache file to get the icon-change on the desktop. After one changed the different start-here.png and svg files it is necessary to do as root the cache update manually or the old icons will stay there and used still from there. For the Human theme it is: gtk-update-icon-cache --force /usr/share/icons/Human
and check the change of the /usr/share/icons/Human/icon-theme.cache to ensure your update worked. The new cache is loaded at windowmanger start (i did not check if a simple panel restart is enough).

---

### Post by yabbadabbadont on 2007-04-28
I have been able to change it in the past by changing/removing the distributor-logo.png file but, like reported above, it doesn't work with feisty.  See the attached screenshot for details.  Please note that I went so far as to reboot the machine after renaming the distributor-logo.png file and removing the icon cache files and it is still the Ubuntu logo.  The next thing I will try is to replace the logo file with one of my own to see if it has any effect.

---

### Post by ComplexNumber on 2007-04-28
> **alterpinguin said:**
> some people may say it is not hardcoded - but i would do so. I had to update the icon-theme.cache file to get the icon-change on the desktop. After one changed the different start-here.png and svg files it is necessary to do as root the cache update manually or the old icons will stay there and used still from there. For the Human theme it is: gtk-update-icon-cache --force /usr/share/icons/Human
and check the change of the /usr/share/icons/Human/icon-theme.cache to ensure your update worked. The new cache is loaded at windowmanger start (i did not check if a simple panel restart is enough).
i don't have the icon-cache file in any of my themes, yet the above still works for me. and here are some screenshots of my distributor-logos (note: i've modified many themes to my liking, so the standard theme isn't quitethe same as the ones i've got).
 i could go on and show every single icon theme that i have, how much more convincing do people need? 

in fact, just for the sole purpose of proving my point, i have just this minute renamed the previous distributor logo to distributor-logoOLD and assigned a random icon to it, and which you can see in screenshot 4 & 5. also note that i don't have any icon-theme-cache's in my icon themes because for large icon themes, the icon-theme-cache would take up more space that the icon them itself with very little improvement in speed. so i deleted them all.

---

### Post by yabbadabbadont on 2007-04-28
> **ComplexNumber said:**
> i don't have the icon-cache file in any of my themes, yet the above still works for me. and here are some screenshots of my distributor-logos (note: i've modified many themes to my liking, so the standard theme isn't quitethe same as the ones i've got).
 i could go on and show every single icon theme that i have, how much more convincing do people need? 

in fact, just for the sole purpose of proving my point, i have just this minute renamed the previous distributor logo to distributor-logoOLD and assigned a random icon to it, and which you can see in screenshot 4 & 5. also note that i don't have any icon-theme-cache's in my icon themes because for large icon themes, the icon-theme-cache would take up more space that the icon them itself with very little improvement in speed. so i deleted them all.

Your profile lists you as using Edgy.  Is this still true?  What you have listed isn't working for me in Feisty.  What did work was using the gconf-editor to change the properties for the "main-menu" object.  I had to set the two custom_icon related entries.  I would guess that when the devs built gnome-panel for Feisty, they built in the Ubuntu logo.  It has been a while since I have built gnome-panel from source  (back in my Gentoo days), but I remember there being a configure option allowing you to do this.

---

### Post by ComplexNumber on 2007-04-28
> **yabbadabbadont said:**
> Your profile lists you as using Edgy.  Is this still true?  What you have listed isn't working for me in Feisty.  What did work was using the gconf-editor to change the properties for the "main-menu" object.  I had to set the two custom_icon related entries.  I would guess that when the devs built gnome-panel for Feisty, they built in the Ubuntu logo.  It has been a while since I have built gnome-panel from source  (back in my Gentoo days), but I remember there being a configure option allowing you to do this.
yes, edgy. everything is working fine in edgy so i don't really have any need to update yet.


anyway, the chances are, the icon whch controls the main menu icon in feisty has probably been changed. try having a look at the gnome-main-menu icon. if it doesn't exist, create one in a theme to see if it has the desired afefct.

---

### Post by yabbadabbadont on 2007-04-28
> **ComplexNumber said:**
> yes, edgy. everything is working fine in edgy so i don't really have any need to update yet.


anyway, the chances are, the icon whch controls the main menu icon in feisty has probably been changed. try having a look at the gnome-main-menu icon. if it doesn't exist, create one in a theme to see if it has the desired afefct.

Nope, that doesn't work either.  EDIT: gnome-main-menu **is** the Ubuntu logo everywhere I've found it.  Just FYI.
```
/home/daffy $ find .icons
.icons
.icons/bubba
.icons/bubba/24x24
.icons/bubba/24x24/places
.icons/bubba/24x24/places/gnome-main-menu.png
.icons/bubba/16x16
.icons/bubba/16x16/places
.icons/bubba/16x16/places/gnome-main-menu.png
.icons/bubba/48x48
.icons/bubba/48x48/places
.icons/bubba/48x48/places/gnome-main-menu.png
.icons/bubba/22x22
.icons/bubba/22x22/places
.icons/bubba/22x22/places/gnome-main-menu.png
.icons/bubba/32x32
.icons/bubba/32x32/places
.icons/bubba/32x32/places/gnome-main-menu.png
.icons/bubba/index.theme
/home/daffy $ cat .icons/bubba/index.theme 
[Icon Theme]
Name=bubba
Comment=bubba
Inherits=gnome
Example=x-directory-normal

# Directory list
Directories=16x16/places,22x22/places,24x24/places,32x32/places,48x48/places

[16x16/places]
Size=48
Context=Places
Type=Fixed

[22x22/places]
Size=48
Context=Places
Type=Fixed

[24x24/places]
Size=48
Context=Places
Type=Fixed

[32x32/places]
Size=48
Context=Places
Type=Fixed

[48x48/places]
Size=48
Context=Places
Type=Fixed
/home/daffy $ find /usr/share/icons/gnome -name "gnome-main-menu*"
/usr/share/icons/gnome/32x32/places/gnome-main-menu.png
/usr/share/icons/gnome/24x24/places/gnome-main-menu.png
/usr/share/icons/gnome/22x22/places/gnome-main-menu.png
/usr/share/icons/gnome/scalable/places/gnome-main-menu.svg
/usr/share/icons/gnome/16x16/places/gnome-main-menu.png

```
I killed gnome-panel and let it restart.  No change.  I even removed the gnome-main-menu.svg in scalable, since I hadn't provided my own icon for it, and killed gnome-panel.  No change.  Like I said before, I was only able to change it by changing settings for the menu object using gconf-editor.  It's not really a big deal, but I thought that it would be good to point this out regarding Feisty.

---

### Post by ComplexNumber on 2007-04-28
its not necessary to restart the panel for that particular change to take effect.

---

### Post by josephus on 2007-04-28
i've looked through the source code and it looks for distributor-logo and not gnome-main-menu

i just created my own theme with just the distributor logo while inheriting the rest from gnome and it works.

---

### Post by yabbadabbadont on 2007-04-28
> **josephus said:**
> i've looked through the source cold and it looks for distributor-logo and not gnome-main-menu

i just created my own theme with just the distributor logo while inheriting the rest from gnome and it works.

:oops:

That appears to work as long as you provide it in all the possible sizes.  Since I don't have a way to make it scalable, I had to change the size of the panel to be the same as the icon I used, then it showed up...  ugh.  :lol:

Edit: I had resized the icon to 16x16, 22x22, 24x24, 32x32, and 48x48.  It was just that my panel wasn't any of those sizes...  give me a moment while I extract my foot from my mouth.  :D

---

### Post by ComplexNumber on 2007-04-28
>  That appears to work as long as you provide it in all the possible sizes.not necessary. just make it available in the largest possible size or in the scalable directory. it will scale it down when appropriate. there are rarely any problems with this. i say rarely because, depending on the theme, problems may occur with (say) the menubar (eg the icon appearing overly large).

---

### Post by yabbadabbadont on 2007-04-28
> **ComplexNumber said:**
> not necessary. just make it available in the largest possible size or in the scalable directory. it will scale it down when appropriate. there are rarely any problems with this. i say rarely because, depending on the theme, problems may occur with (say) the menubar (eg the icon appearing overly large).

I had it available in all the sizes I listed above.  My panel is 21 pixels high.  It did not use it until I changed the size of the panel to match one of the sizes I provided.  It didn't do any scaling as I didn't have the icon available in svg format for the scalable directory.

Edit: Or were you saying that it would have scaled down to 21 pixels if I had provided a 128x128 png?

---

### Post by ComplexNumber on 2007-04-28
> **yabbadabbadont said:**
> I had it available in all the sizes I listed above.  My panel is 21 pixels high.  It did not use it until I changed the size of the panel to match one of the sizes I provided.  It didn't do any scaling as I didn't have the icon available in svg format for the scalable directory.
ok, i'll put the theory to the test. i tested it upon the Tango and nuoveXT themes because they have lots of different sized directories. the results are in the screenshots.
maybe its different in feisty, but i very much doubt it.

---

### Post by RawMustard on 2007-04-28
Look guys, the problem isn't with the "main menu"  It's with the "menu bar"  They're both different applets.  I can change the icon for "main menu" but not for the "menu bar"

@ComplexNumber

All your screen shots show you having the "main menu" applet on your panel, what happens when you replace it with the "menu bar"  I reckon in feisty the "menu bar" is hard coded!

I'm not stupid, I understand all that you have said, you are confusing the two applets I think!

[ATTACH]31200[/ATTACH]

---

### Post by ComplexNumber on 2007-04-28
> All your screen shots show you having the "main menu" applet on your panel, what happens when you replace it with the "menu bar" I reckon in feisty the "menu bar" is hard coded!ok, i've tested it on the same themes as my last post. the results are in the screenshots (to avoid messing up my main panel, i've created a new panel and added a menubar to it).

screenshot 1  - nuoveXT used the distributor-logo for the menubr, but it didn't scale it down well (see my earlier comment about this occurring with some themes). i suspect that this may have something to do with the index.theme file.

screenshot 2 - when i chose an icon that is close to the size of the panel, it used the distributor-logo perfectly.

screenshot 3 - tango used the distributor-logo for the menubar, but ONLY when i the distributor-logo is the NEXT SIZE DOWN from the size of the panel. if i went 1 size up, it wouldn't use it.

screenshot 4 - in this, i used lila because, unlike tango and nuoveXT, it only has a scalable directory. lila used the distributor-logo for the menubar successfully.

---

### Post by josephus on 2007-04-28
OK.  I'm pretty sure that they use the same icons, so something weird is going on with your system.  Have you tried downloading icon packs from gnome-look.org?  I just downloaded this

[http://www.gnome-look.org/content/show.php/Ubuntu_HumanAzul?content=37099](http://www.gnome-look.org/content/show.php/Ubuntu_HumanAzul?content=37099)

and unpacked it in the ~/.icons directory.  Give that a try and let us know what happens.

---

### Post by yabbadabbadont on 2007-04-28
> **ComplexNumber said:**
> ok, i'll put the theory to the test. i tested it upon the Tango and nuoveXT themes because they have lots of different sized directories. the results are in the screenshots.
maybe its different in feisty, but i very much doubt it.

Gee, I guess you know best.  After all, I'm only the one sitting in front of my computer looking at it.  What do I know...  :p :)

---

### Post by kpolice on 2007-04-29
The button will always use the 24 px icon, depending on the size of your panel, and if there isn't one then it will look for the scalable one or will scale any of the available. 

This is how GTK works, and also if the icon theme that you use inherits from another one that has the icon at 24px then it will use this instead of yours. If you have a bigger panel it will look for the best match.

---

### Post by ComplexNumber on 2007-04-29
> **kpolice said:**
> **The button will always use the 24 px icon,** depending on the size of your panel, and if there isn't one then it will look for the scalable one or will scale any of the available. 

This is how GTK works, and also if the icon theme that you use inherits from another one that has the icon at 24px then it will use this instead of yours. If you have a bigger panel it will look for the best match.
....except in cases where the index.theme  perhaps needs correcting (eg nuoveXT, etc). it seems strange that nuoveXT didn't use the icon from the theme that it inherits instead (in the case of my setup, Aero). Tango was using the 22x22 icons in the above case.

---

### Post by RawMustard on 2007-04-29
Ok, My chosen icon theme was mist.  Mist did not have start-here.png, gnome-main-menu.png, or distributor-logo.png.  It inherits these from /usr/share/icons/gnome  In gnome icons dir, I had replaced all instances of these icons with my own, infact I had done it for all the icon theme files, however, the ubuntu logo continued to plague me :(

How to fix:  Simply move or delete icon-theme.cache in your chosen icon theme dir and all will be well :)

Does edgy have this file?  I never saw it in dapper, having bypassed edgy and upgrading right to feisty.

Thankyou guys, I thought I was going mad there for a minute  ](*,)

---

### Post by ComplexNumber on 2007-04-29
> **RawMustard said:**
> Ok, My chosen icon theme was mist.  Mist did not have start-here.png, gnome-main-menu.png, or distributor-logo.png.  It inherits these from /usr/share/icons/gnome  In gnome icons dir, I had replaced all instances of these icons with my own, infact I had done it for all the icon theme files, however, the ubuntu logo continued to plague me :(

How to fix:  Simply move or delete icon-theme.cache in your chosen icon theme dir and all will be well :)

Does edgy have this file?  I never saw it in dapper, having bypassed edgy and upgrading right to feisty.

Thankyou guys, I thought I was going mad there for a minute  ](*,)
thats another reason why the icon-theme-cache needs to be deleted(permanently).
 if you have the (for example) snowish theme installed, check the size of the icon-theme-cache file :shock:

---

### Post by cst05001 on 2007-05-03
en, but How can I change the icon in KDE?

---

### Post by cst05001 on 2007-05-03
I try to change the KDE icon,HoHo

---

### Post by revertex on 2007-05-05
dude, if you want to screw up things, at least do it the easy way.

instead of edit every icon theme you have, just use gconf-editor to change the start menu icon.

open gconf-editor, select menu > edit >find mark "search also in key value" checkbox option  and search for "menu-object".

in this key, mark "use_custon icon" checkbox, and change "custom icon" path.

---

### Post by ggratto on 2007-05-06
I have found that the main menu and the menu bar icons are not the issue it is the deafault gnome icons that seem to be changed.  Go here [http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=gnome-icon-theme](http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=gnome-icon-theme)  (I am currently using "GNOME Desktop icon theme 2.18.0-2: al ")   install the icon pakage and you will be back to the default gnome icons then you can correctly use gf config as disscussed else where in this thread to modify as you want.

---

### Post by rsambuca on 2007-05-28
> **revertex said:**
> dude, if you want to screw up things, at least do it the easy way.

instead of edit every icon theme you have, just use gconf-editor to change the start menu icon.

open gconf-editor, select menu > edit >find mark "search also in key value" checkbox option  and search for "menu-object".

in this key, mark "use_custon icon" checkbox, and change "custom icon" path.

That doesn't find anything for me.

---

### Post by pedro_cesar on 2007-09-21
Not really, I'm working on the same thing, maybe we could get in touch.

---

### Post by yun4 on 2007-10-20
> **ComplexNumber said:**
> if the icon theme that you've selected doesn't have its own icon for the main menu, it will get it from one of the icon themes that it inherits (usually gnome, Tango, or Human(on ubuntu anyway)). th actual icon that you need to change is the start-here icon thats found in places. for example, 
/usr/share/icons/Human/scalable/places/start-here.svg
or
/usr/share/icons/Human/48x48/places/start-here.svg
or
/usr/share/icons/Human/24x24/places/start-here.svg


.....depending upon the size of the panel.




the icon(ie distributor-logo) that some of you are trying to change is a link that links to to the start-here icon.

I've tried replacing is png in 
/usr/share/icons/hicolor/48x48/apps/distributor-logo.png
and other place places mentoned above and still no luck
and now it shows not the original distributor-logo.png but a missing icon any idea why?

btw this is a clean install of gusty

---

### Post by smartboyathome on 2007-10-20
You have to put all the icons (ie: 16x16, 22x22, 24x24, etc) into their respective folders, or they won't replace. Alternatively, you can make one big icon and put it in scalable as distributor logo,svg.

---

### Post by yun4 on 2007-10-20
I did and its still the same

---

### Post by smartboyathome on 2007-10-20
just wondering, but what is the size of your panel?

---

### Post by yun4 on 2007-10-20
i think its 24pix u can see it in my post where i include a ss of my desktop 

post #73

anyway i've replace all distrbutor-logo i can find at all sizes, and also does it matter if the size isn't correct? I only have a 24x24 and 48x48 icon and i just replace them with whichever is the closest

---

### Post by smartboyathome on 2007-10-20
it does matter, actually (I think). Try making them the exact size, and see if this makes a difference.

---

### Post by yun4 on 2007-10-21
still nothing, and i've tried installing your iBlack theme (which should replace the original distributor-logo.png) but ended up displaying the original ubuntu icon

---

### Post by dustintinsley on 2007-10-21
hace you ran the command "gtk-update-icon-cache"?  i ran into this problem once when i had replace the distributor logo in the Human theme and ran "gtk-update-icon-cache /usr/share/icons/human"

---

