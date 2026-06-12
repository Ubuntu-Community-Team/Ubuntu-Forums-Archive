---
title: "How to make Kubuntu look like Ubuntu?"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by MountainX on 2008-03-18
I want to use KDE for its configurability. However, I like the top menu and bottom taskbar of the default Ubuntu GDM. I also like the colors of Ubuntu more than Kubuntu. In fact, I like Nautilus, gedit, etc. I haven't used Konqueror that much yet, but I definitely want to use Firefox 3 for web browsing. I haven't found any KDE themes I like. What should I do to get the flexibiility and customization of KDE while keeping all the stuff I like about the default GDM-based Ubuntu? Thanks

---

### Post by wieman01 on 2008-03-18
Why would you want to have a GDM theme and all other Gnome tools on Kubuntu? Why don't you install Ubuntu right away?

---

### Post by MountainX on 2008-03-18
> **wieman01 said:**
>  Why don't you install Ubuntu right away?

As I said, I want to use KDE for its configurability. What I've read says that KDE is more flexible and more configurable. I want more options and the richest desktop environment. But there is still a bunch of stuff I like about GNOME.

---

### Post by Therion on 2008-03-18
> **MountainX said:**
> ... KDE is more flexible and more configurable. 
Really... How so?

I find Gnome to be quite configurable...  :confused:

---

### Post by wieman01 on 2008-03-18
In terms of customization KDE offers more options, that's true, however, I doubt you will be able to make it look like Gnome. The menu will create an issue for sure. You can change the colors, etc. easily for sure, but the menu and apps will look different.

---

### Post by MountainX on 2008-03-18
> **Therion said:**
> Really... How so?

I find Gnome to be quite configurable...  :confused:

I'm just repeating what I have read.

see [http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)

"Generally, KDE focuses on offering as many features as possible with as many graphical ways as possible for configuring those features. Fans of KDE highlight the functionality it has. Critics of KDE say the menus are too confusing.

Gnome, on the other hand, opts for simplicity and often hides certain configurations in order to achieve that simplicity. Fans of Gnome think the simplicity of Gnome offers a cleanliness that allows the user to get stuff done. Critics of Gnome think it just lacks certain functionality."

Here are some other links I have looked at:
[http://itmanagement.earthweb.com/osrc/article.php/12068_3671906_4](http://itmanagement.earthweb.com/osrc/article.php/12068_3671906_4)
[http://linuxreviews.org/software/desktops/](http://linuxreviews.org/software/desktops/)
[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)
[http://www.illusionary.com/GNOMEvKDE.html](http://www.illusionary.com/GNOMEvKDE.html)
[http://forums.fedoraforum.org/archive/index.php/t-25947.html](http://forums.fedoraforum.org/archive/index.php/t-25947.html)
[http://ubuntuforums.org/archive/index.php/t-422417.html](http://ubuntuforums.org/archive/index.php/t-422417.html)

---

### Post by wieman01 on 2008-03-18
Yes, that's why I prefer it as well. I never quite like Gnome. So let's focus on your original request...

You could use Dolphin rathern than Konqueror. So do I.

Kate will be the replacement for Gedit, however, you could still install 'gedit' afterwards as you find it in the repositories.

Background, colors, etc. well, I don't see an issue here either.

But again, the menu will be a headache as it is fairly static. Unless you install Kbfx for instance:

[http://kde-look.org/index.php?xcontentmode=62&PHPSESSID=e87af9af61bf2497ac4932054f64c6a8]("http://kde-look.org/index.php?xcontentmode=62&PHPSESSID=e87af9af61bf2497ac4932054f64c6a8")

---

### Post by NightwishFan on 2008-03-18
I remember it being hard to use more than one panel.

---

### Post by MountainX on 2008-03-18
> **wieman01 said:**
> 

But again, the menu will be a headache as it is fairly static. Unless you install Kbfx for instance:

[http://kde-look.org/index.php?xcontentmode=62&PHPSESSID=e87af9af61bf2497ac4932054f64c6a8]("http://kde-look.org/index.php?xcontentmode=62&PHPSESSID=e87af9af61bf2497ac4932054f64c6a8")

Thanks. I'll look into kbfx.

But my Kubuntu experience is starting off very poorly. After a clean install I applied all the updates and I got an error. This never happened in Ubuntu. Then I restarted and tried to update again and this time the update program crashed. So I rebooted again and now I get error 15.

Maybe I should just stick with Ubuntu. I thought KDE was just as stable... Anyway, I am getting off topic now.

 If I stick with Kubuntu I think I will take the advice and try kbfx and Dolphin -- and I will probably like Kate.

---

### Post by stchman on 2008-03-18
As I am not an expert on either KDE or Gnome I do find both very configurable.

I can say that it is fairly easy to make Gnome looke like KDE, but I cannot comment on the other way around.

I find Gnome so customizable that it is near dizzying.  Of course then there is gnome-look.org in that you can skin Gnome to look like pretty much anything.

Another good reason to use Gnome over KDE is that most of the Ubuntu resources are geared towards Gnome.  I know that Ubuntu forums is way better than Kubuntu forums.

Just my $0.02.

---

### Post by NightwishFan on 2008-03-18
I always update with the terminal. With that kind of thing I never use the GUI.
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Dark Star on 2008-03-18
To complete the incomplete update do ```
sudo apt-get upgrade -f
sudo dpkg --configure -a
```

Also no neeed to compile KBFX , it is available in repos.. If you want to change KDM themes check this [http://packages.ubuntu.com/gutsy-backports/kdmtheme](http://packages.ubuntu.com/gutsy-backports/kdmtheme) .. KDE is stable but Kubuntu community isn't that dedicated like Ubuntu :p I am also using Kubuntu and the default config.. has nothing.. not even calculator,character map and all :| Not even KDE games :|

---

### Post by sayakb on 2008-03-18
You might install the package ubuntu-desktop. It is not needed that you log in to the session but you can use Nautilus and other tools you want to. Just remember to keep everything orange :D (though personally, I think blue is better!! But yeah, blue looks good until you look at XP => UGLY)

---

### Post by NightwishFan on 2008-03-18
Yeah I do not like Kubuntu at all. Though I can get it the way I want it easy. I mostly use KDE because I get bored fast and I like to constantly change my theme.

---

### Post by scramasax on 2008-03-18
> **MountainX said:**
> I'm just repeating what I have read.

It's true as far as it goes, but I think what you've read is a bad basis to be going on.  Better to try and experience than to go on what you've read.

And well to remember that it's not that GNOME isn't configurable; it's just that the options often aren't presented in the GUI, but you have to drop down to the command line to change the default.

GNOME is the default on most distros now, but a lot of people like KDE and it does, apparently, have a smaller footprint -- and, apparently, KDE 4 while offering more will be better in that regard, too.  So it's personal choice.  And, as I say, you can't go on what you read, anyway.  You have to try both and get experience of them.  Since you like the look of GNOME and it's the default with Ubuntu I'd go with that.  you can always play with live CDs.  Things run slower off a CD, of course, but you get to see what a desktop looks like and what the defaults applications are like.

---

### Post by Dark Star on 2008-03-18
[[IMG]http://www.imgx.org/thumbs/large/13730_qiea7/Desktop4.jpg[/IMG] ]("http://www.imgx.org/view/full/13730_qiea7")[[IMG]http://www.imgx.org/thumbs/large/12900_zawbf/snapshot3.png[/IMG]]("http://www.imgx.org/view/full/12900_zawbf")

Check out my KDE desktop.. I have used Gnome for more than 2 years and now using KDe 3.5.9 with KDE 4.02 ..Can any 1 tell me how to manually install Style and Kwin Windows Decoration in Kubuntu ?

---

### Post by wieman01 on 2008-03-18
> **Dark Star said:**
> [[IMG]http://www.imgx.org/thumbs/large/13730_qiea7/Desktop4.jpg[/IMG] ]("http://www.imgx.org/view/full/13730_qiea7")[[IMG]http://www.imgx.org/thumbs/large/12900_zawbf/snapshot3.png[/IMG]]("http://www.imgx.org/view/full/12900_zawbf")

Check out my KDE desktop.. I have used Gnome for more than 2 years and now using KDe 3.5.9 with KDE 4.02 ..Can any 1 tell me how to manually install Style and Kwin Windows Decoration in Kubuntu ?
Looks nice.

Please open a new thread for your questions.

---

### Post by MountainX on 2008-03-18
> **stchman said:**
> 
Another good reason to use Gnome over KDE is that most of the Ubuntu resources are geared towards Gnome.

That may be the most important reason for me. I'm a newbie, so I rely on the ubuntu forums a great deal.

---

### Post by wieman01 on 2008-03-18
> **MountainX said:**
> That may be the most important reason for me. I'm a newbie, so I rely on the ubuntu forums a great deal.
I never had issues with Kubuntu, however, I think it's a good reason to go for Ubuntu. You don't need another stumbling block.

---

### Post by Xiong Chiamiov on 2008-03-18
Of course, most of the resources can be applied rather easily (since the underlying part is the same), but yes, some things definitely are different.

---

### Post by MountainX on 2008-03-18
> **Dark Star said:**
> 

Check out my KDE desktop..

I like it. Can you tell me where to get the background on the right (the dark sky)?

Also, I like the little utility windows for fs usage, cpu and processes. How do I set those up? Can I get the same load monitoring windows in GNOME too? 

Is there anything for either KDE or GNOME that looks very close to SysInternals Process Explorer? I particularly like the very small taskbar icon that shows CPU load when the app is minimized.

---

### Post by MountainX on 2008-03-19
Wow, this is a harder choice than I thought. I have been using Kubuntu on one computer now for a couple days and there are things about it that I really like. There are also things about it that I do not like.

On the plus side:
1. I like the tool tips that show up everywhere (desktop icons, files, etc.). This is apparently not available in Ubuntu or GNOME.
2. I like the "open terminal here" link in the file/folder browser (Konqueror). I suppose I could add this to Ubuntu (I had a registry entry that provided this feature in Windows).
3. I like the plethora of options/choices. Kubuntu really does seem more feature-rich.
4. It seems like I can "feel" the object-oriented nature of the development behind KDE. Maybe I'm imagining it, but I get this sense of integration and inter-connectedness that GNOME is missing -- and I like it.

On the minus side:
1. I have had repeated problems with updates (adept-manager) that I never had in Ubuntu.
2. I see areas that don't look as polished (debugged) as in Ubuntu.
3. I will have a serious issue with forum support. I am a newbie and I am still on the steep part of the learning curve for Linux. I have already found that Kubuntu adds one more obstacle to getting things done. I can't even figure out how to open the text editor as root, which was one of the first things I learned in Ubuntu --"sudo kate ..." doesn't work. I rely heavily on the Ubuntu forums. Finding support for specific Kubuntu questions requires additional effort.
4. I like most of the basic GNOME apps better.
5. Compiz doesn't work as well in Kubuntu. Compiz is a must-have for me because it is the only convenient way I have found to have a full-screen terminal server client session anchored to its own desktop. Doing this with Compiz enabled makes it so much more convenient. Since I spend a lot of time in the terminal server client, this is important to me. I suppose I might be able to fix this in Kubuntu, but if I stay with Ubuntu I don't have to fix it because it isn't broken.
6. I could go on.

Anyway, it is a tough decision. I have contemplated using both GNOME and KDE, but I hear that can be messy. I don't know if I'm ready for that, as a newbie.

Those are my thoughts. I welcome any other comments or suggestions.

P.S. Dark Star, I'm still hoping you'll answer my question about your screen shots.

---

### Post by Dark Star on 2008-03-20
[http://www.imgx.org/view/full/13117_jfonj](http://www.imgx.org/view/full/13117_jfonj)  Here you go. Sorry for the delay I was busy with my work.

As far as those desklets use Super Karamba in KDE 3.5x and Plamoids in 4.x ;)

---

### Post by MountainX on 2008-03-20
Dark Star - Thank you.

I'm starting to like Kubuntu a lot more now that I'm getting it tweaked. In particular I have compiz working perfectly now. There are still things I like better about Ubuntu, but I'm getting more comfortable in Kubuntu too.

---

### Post by VyperX on 2008-03-20
just install ubuntu dude

---

### Post by MountainX on 2008-03-20
> **Dark Star said:**
> 

As far as those desklets use Super Karamba in KDE 3.5x and Plamoids in 4.x ;)

Where can I get the Super Karamba scripts you use for system performance (such as CPU%, file space, etc.)? Thanks. (And don't work too hard.)

---

### Post by Dark Star on 2008-03-20
Instal  SUper Karamba via ```
sudo apt-get install superkaramba
``` Now open it via **Kmenu - > Utilities **
A new window will open and 1'st option isto get new themes .. Click on your fav and install it . It will d/l the package and will install automatically for you.. or you can check [kde-look]("http://www.kde-look.org/index.php?xcontentmode=38&PHPSESSID=36018aeeee3dab53d3778f55d6893504") .. Double click the widget to activte to desktop . Unlock their position by right clicking and place wherever you want :)

Hope this helps :) Regards

---

