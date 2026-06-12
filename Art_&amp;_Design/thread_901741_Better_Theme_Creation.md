---
title: "Better Theme Creation?"
date: 2008-08-26
forum: Art &amp; Design
---

### Post by Sanchopinky on 2008-08-26
I've never been really satisfied with most of the themes I've come across. I mean the person who created the theme has it perfectly set up , but when I try to use it the metacity windows are too large or just off a bit.

I read something on Digg.com where a user said that there aren't many variations from Mac/Vista/XP look to GTK themes etc. His reason was that mostly artists created the really imaginative/creative themes and that programmers were in charge of creating GTK themes and such.

Would there be anyway of developing a program like Windowblinds theme creator, but for GTK themes? That way Artists who aren't really familiar with programming can share their ideas and concepts. I figure something like this could really make gnome based distro's even more popular. KDE, Windows, and Mac's are really making it easier for users to customize, I'd hate to see Gnome left behind.

---

### Post by Genius314 on 2008-08-26
There should definitely be a GUI to make GTK themes. I think the confusing gtkrc codes turn away a lot of potential themers.

---

### Post by damis648 on 2008-08-26
> **genius314 said:**
> there should definitely be a gui to make gtk themes. I think the confusing gtkrc codes turn away a lot of potential themers.

+1

---

### Post by Crafty Kisses on 2008-08-26
Yeah something similar to Blender but for GTK themes, that would be awesome.

---

### Post by smartboyathome on 2008-08-26
Well, the problem is that GTK themes can use many engines, theres Clearlooks, Murrine, Aurora, Nodoka, Pixmap, and other engines! Each of these engines has a different set of rules which are used to create their themes. For example, Aurora and Murrine use similar basic sets of rules since Aurora came from Murrine, but Clearlooks uses a completely different syntax. Nodoka even has a different syntax itself, and Pixmap also has a different syntax. In order to be able to work, it would need to support all these engines as well as new ones that might pop up. Windowsblinds only has to support one. Because of all these engines having to be supported, the tool itself would be prone to  bugs, and it would probably have to have backends made for it. The tool itself would be as complicated as GTK themes can be when trying to combine toolkits. I just don't see this happening anytime soon, or very well, but if anyone wants to create something like it go right on ahead.

Also, GTK themes aren't that hard to create if you read through a few themes based off of the different engines and learn the different syntax. The syntax could be improved, though, I can give you that much. Lets hope GTK 3 will take care of that.

---

### Post by TBuck on 2008-08-26
I agree with you on this one. Most themes lack originality and the ones that have it, they just straight up suck. We could definately use some good artists on the themeing scene. Ones that don't rip off other OS's

---

### Post by Sanchopinky on 2008-08-26
@smartboyathome:

I didn't know that they used a different syntax. You say that a program would have to support the different engines, but most of these engines already come pre-installed. To me it seems very possible to have a program that uses whats already been given. For example: download the program , and it will allow you to create themes for the basic engines, and you must addon any different/new engines you want.

Or perhaps a simpler engine to allow artists who don't really have experience coding.

Basically I mean, gnome needs to have a better way for artists to become involved.

Thanks for your help. :)

---

### Post by smartboyathome on 2008-08-27
Talk to GNOME if you want them to improve their theming.

The engines aren't all installed, what I am saying is that it would have to support all these engines, since they use different syntax it would have to take that into account, and it wouldn't be as simple as "Create themes for the basic engines", as it would have to be programmed to recognise which engines were installed etc. It would actually be pretty difficult.

---

### Post by k99goran on 2008-08-27
> **smartboyathome said:**
> The engines aren't all installed, what I am saying is that it would have to support all these engines, since they use different syntax it would have to take that into account, and it wouldn't be as simple as "Create themes for the basic engines", as it would have to be programmed to recognise which engines were installed etc. It would actually be pretty difficult.
Couldn't it just come bundled with all the theme engines it supports?

---

### Post by smartboyathome on 2008-08-27
> **k99goran said:**
> Couldn't it just come bundled with all the theme engines it supports?

Sure, if you only want certain engines to be able to be used, not any new ones nor older ones. If you guys want it, remember you can make it. ;)

---

### Post by MadsRH on 2008-08-27
I don't know if this is useful, but *days_of_ruin* is working on a GUI metacity theme editor.

If you download the latest revision you should be able to help test it.Bear in mind tho, its still far away from being finished. Please post feedback to *days_of_ruin*. Download here:
[https://launchpad.net/mct]("https://launchpad.net/mct")

---

### Post by days_of_ruin on 2008-08-27
> **MadsRH said:**
> I don't know if this is useful, but *days_of_ruin* is working on a GUI metacity theme editor.

If you download the latest revision you should be able to help test it.Bear in mind tho, its still far away from being finished. Please post feedback to *days_of_ruin*. Download here:
[https://launchpad.net/mct]("https://launchpad.net/mct")

Thanks for plugging it:)Have you tried it yet?The save button actually 
refreshes the theme and currently you can't save the theme.Yeah its early.

back on topic:

I have actually thought of making a gtk theme editor
but like smartboyathome said there are a lot of problems with making that.
In gtk you can set a widget to use a different theme than the rest of the 
program but that doesn't seem to work with pixmaps.

---

### Post by Tuxoid on 2008-09-02
yes, different themes use different engines, but what if the theme design GUI had a dedicated engine(s)?

Would that make it possible?

I say this because I would love to theme, but rc files are incredibly confusing.

---

### Post by airtonix on 2008-09-02
i commented somewhere else about this topic before, but i cant find it.

Couple things : 

I found a tool called ginspector : 
> ```
sudo apt-get install ginspector
``` To get an idea of which elements you might need to look at twiddling with firefox use ginspector like so : 

```
g-inspector firefox
``` When you find the g-inspector window (which is quite small & maybe underneath your target application), have a look around in the view menu at the various inspectors.Secondly, for a gtk theme editor to properly support the many engines that exist and the ones that are yet to be created : 

 1 - gtk-engine authors really ought to supply an api documentation for the syntax required for their engines, additionally a syntax definition file for gedit/vim etc would be a great start.
 
2 - an inspector that honours the elements defined by the engine would be very helpful in working out just "what the hell that little bit over there under that little bit i dont know what the heck is called'. ginspector i think already does this but im not sure that the information it exposes is relevant to gtk theming.

3 - I though glade might be a place to start with regards to providing a sandbox enviroment inorder to  gather widget names. 

I dont know but maybe glade should be extended to allow for theme creation?

---

### Post by AJB2K3 on 2008-09-02
> **Sanchopinky said:**
> I've never been really satisfied with most of the themes I've come across. I mean the person who created the theme has it perfectly set up , but when I try to use it the metacity windows are too large or just off a bit.

I read something on Digg.com where a user said that there aren't many variations from Mac/Vista/XP look to GTK themes etc. His reason was that mostly artists created the really imaginative/creative themes and that programmers were in charge of creating GTK themes and such.

*snip*
Rubbish obviously he has never used google.
I was using gtk themes back on win 98 
The main tool was GTKpref now known as GTK Preferance tool.[GTKpref]("http://gtk-win.sourceforge.net/home/index.php/en/Gtk2Prefs")
And to be honest its only slightly harder the xhtml+css2

---

### Post by geoken on 2008-09-04
1. Download a full pixmap theme
2. Replace every element image by image
3. Pat yourself on the back for making a theme without any coding.

---

### Post by lyceum on 2008-09-04
> **geoken said:**
> 1. Download a full pixmap theme
2. Replace every element image by image
3. Pat yourself on the back for making a theme without any coding.

Yes, thanks for that. Artists do not usually like to go that rout, I know I don't, and that is why I have not created a theme myself. 

I think it would be nice to have a program that would work like so:

1. click on your engine of preference.
     a. new engines could be added with updates.
2. add in each image needed (you could make it with GIMP, InkScape or what ever).
     a. there could be a "next" button after each or 
     b. there could be a list of needed images and as you enter an image the program shows image you are using under or next to the item name
3. You would see how the theme looks up to this point in the main window
4. when done you hit a "package" button.
5. If the program wanted to go all out, then there would be a button to login and load your new theme, with a custom image the program created for you, on to gnome-look.org.
6. It would be really cool if the program remembered where previously used images were stored so you could easily mix and match themes you had made. 

That is how I would do it, if I could program. If anyone would like to make this, let me know and I will create a mock-up.

---

### Post by oedipuss on 2008-09-04
Would such a tool absolutely *need* to know all the different engine options , though ? As far as syntax goes, it's usually ' something = something_else ' . An app like that could integrate options from a few of the most widely used engines (murrine, clearlooks etc, perhaps pixmap too) and provide an 'add custom' function that would ask you for the missing or obscure option line and add it directly to the relevant section.

The hardest part, in which a theming app could help the most is identifying the various widgets, classes and subclasses you want to theme differently, and tweaking gtk parameters (such as padding) and colors, which have little to do with the engine specifics. 
It doesn't have to be completely graphical either. I'd be happy with something like that + a code window or tab to tweak the rc file directly.

---

### Post by lyceum on 2008-09-05
> **oedipuss said:**
> Would such a tool absolutely *need* to know all the different engine options , though ? As far as syntax goes, it's usually ' something = something_else ' . An app like that could integrate options from a few of the most widely used engines (murrine, clearlooks etc, perhaps pixmap too) and provide an 'add custom' function that would ask you for the missing or obscure option line and add it directly to the relevant section.

The hardest part, in which a theming app could help the most is identifying the various widgets, classes and subclasses you want to theme differently, and tweaking gtk parameters (such as padding) and colors, which have little to do with the engine specifics. 
It doesn't have to be completely graphical either. I'd be happy with something like that + a code window or tab to tweak the rc file directly.

I do not know enough about coding to say anything about engine options. If tweaking widgets would work just as well, that is fine. As for not completely graphical, if you are making something for artists to use it should look cool, IMHO. I have found that as an artist I tend to judge things (not people) on how they look, fair or not. When looking for which disto I wanted to use, the first thing I looked at was the website, for example. If the website looked bad I figured the distro would not be as good. That does not have to make sense, it is just how I am. The more GUI the less likely artists will fear it, IMO.

---

### Post by Crafty Kisses on 2008-09-05
> **smartboyathome said:**
> Sure, if you only want certain engines to be able to be used, not any new ones nor older ones. If you guys want it, remember you can make it. ;)

You certainly can, and hopefully someone does make it, if you're good enough please take on the project. :)

---

### Post by Genius314 on 2008-09-05
> **geoken said:**
> 1. Download a full pixmap theme
2. Replace every element image by image
3. Pat yourself on the back for making a theme without any coding.

That's what I did. Although I ended up changing some things, so I learned some of the code anyway.
It was hard finding a full pixmap theme, though.

---

### Post by lyceum on 2008-09-06
I was thinking, and this may be dumb, but I am an artist, not a coder. Anyhow, I work with Ruby on Rails and I am studying Ruby right now. Alexandria is coded in Ruby, if I remember correctly. Would it be possible to code a program like the one I described in Ruby? 

If so here is my idea: I am working on a website for artists using FOSS, or wanting to use FOSS. I was thinking of making a program for the site that would allow users to upload their images or uses shared images to make their own themes. By allowing the use of shared art, anyone could make their own. I was thinking of doing more than just Gnome themes, I wanted to let users make their own GDM themes or icon themes as well, again by uploading images or using shared images. 

Does this sound feasible?

---

