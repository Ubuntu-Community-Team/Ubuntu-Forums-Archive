---
title: "Mockups Wanted!"
date: 2009-12-11
forum: Art &amp; Design
---

### Post by tretle on 2009-12-11
I decided to start this thread to try and get some progression from a designers point of view on how nautilus live folder previews might look and work on a design level.

Disclaimer - Live folder previews are different to previews with a tool like gloobus, live folder previews give someone a visual idea of the files which are contained in folders usually by placing thumbnails on top of folders. This allows someone to glance over a series of folders to get some idea of the contents. 
Whereas gloobus is more of a previewer, you specifically point something at gloobus to find information about it rather than find information spatially about the contents of a series of folders at the same time.

So mockups of how these folders might look is the main object of this thread.

Here are some pre-existing solutions which might inspire you.

[IMG]http://img230.imageshack.us/img230/5808/pantallazohu0.jpg[/IMG]- mockup? if someone knows speak up.

[IMG]http://img257.imageshack.us/img257/2709/131009folderpreviewquic.png[/IMG]- osx quicklook

[IMG]http://img192.imageshack.us/img192/2848/vistahidenameeasteregg3.jpg[/IMG]- vista

---

### Post by Exodist on 2009-12-11
Sadly Vista or Win7 folders have the best viewing so far.

---

### Post by Psumi on 2009-12-11
> **Exodist said:**
> Sadly Vista or Win7 folders have the best viewing so far.

Uh, KDE has similar viewing.

---

### Post by Exodist on 2009-12-11
> **Psumi said:**
> Uh, KDE has similar viewing.
I admit KDEs is better then Gnomes and I am a Gnome user. But they both suck compared to Vistas. M$ invested a crap load of money in designers to come up with the new folder look. I am not a M$ fan boy by any means, trust me.. But their investment paid off.  :-|

---

### Post by tretle on 2009-12-11
Its really important to get feedback guys, its one thing to code a solution but its another to code one that is easy for icon designers. 

I was thinking the transparent folder lid would probably be the best approach to take when it comes to icon design. It would require 2 parts to the folder icon, the front and back. 

In my honest opinion implementing it in a similar way to windows would be a pain for icon designers and that method doesn't portray that much useful info to the user to begin with.

I like new kde folder previews but the fact they are on top of the folder rather than inside it slightly annoys me. 

I like how the thumbnails are arranged on the top image and I am thinking that creating a cairo animation to cycle through the thumbnails with the scroll wheal might be the best approach to take.

You could also create a cairo animation for the windows way of doing things but it wouldn't work as well visually in my view to a sprawled out deck of cards like effect.

---

### Post by oedipuss on 2009-12-13
I like the first one . The transparent folder might not scale very well, I haven't used mac os to see how it is for small sizes, or if it's for quicklook only. Vista also looks better only for larger icon sizes. 
The first approach would look relatively nicer for smaller icons too, especially if the thumbnails scale disproportionately to the size of the icon. Smaller icons could show fewer but relatively larger thumbnails.

---

### Post by tretle on 2009-12-13
> **oedipuss said:**
> I like the first one . The transparent folder might not scale very well, I haven't used mac os to see how it is for small sizes, or if it's for quicklook only. Vista also looks better only for larger icon sizes. 
The first approach would look relatively nicer for smaller icons too, especially if the thumbnails scale disproportionately to the size of the icon. Smaller icons could show fewer but relatively larger thumbnails.

I like the first one too but my worry is that if there is a cairo animation so that people can scroll through the contents of the folder they might try and click on the image/album etc directly thinking it would open the content when in reality it should open the folder. If the front of the folder was transparent then the user would not assume such a thing.

Here are some reasons why I like the idea of animating the folder preview on scroll.

#1 It might default to the first three files in the folder and the user might want to see if a specific set of files are in the folder.
#2 It would be designed to remember the scroll position so over time it learns what the best previews are to use for folders.
#3 There has been a bug filed for audio previews to extend the functionality to allow for fast forward and rewinding using scroll, being able to dynamically choose the thumbnails shown with scroll of folder contents seems like the most consistent thing to do.

---

### Post by oedipuss on 2009-12-13
Would a small visual clue such as this be enough to hint that the previewed file is inside the folder? I imagine it somewhat like vista, just with less space wasted to the folder icon itself. 
If requiring a two part render is hard to implement, then perhaps the folder could be 'opened' at a right angle, not overlap with the images but still suggesting they're 'inside' it.

Also, that's more or less what I meant with disproportionately scaling the thumbnail to the icon .

---

### Post by SonnHalter on 2009-12-13
here's my contribution. :P the preview should happen when you mouseover the folder

---

### Post by DeadSuperHero on 2009-12-14
Here's mine. It's a bit simplistic, but I personally think people would like it from a usability standpoint.

It would function using OpenGL and Clutter. Functionally, it shows a tree-branch sort of hierarchy of the entire filesystem, with a simplified layout. It makes simple distinctions between system files and user files.

When a folder is selected, OpenGL acceleration causes the icon to grow, and other icons on that level to shrink and move to the side, eventually fading out to make more space for lower or higher files. By dragging the slider, one can make the folders grow and shrink up and down. 

I just figured that this would be a unique approach to file management, and would also give an easy approach to seeing exactly *what* is in your folders without messy navigation.

Edit: Oh yes, I hadn't thought of a way to indicate which files are which in navigation. Initially, I thought perhaps mousing over a file would give a bubble with its name, but for now I'm not so sure.

---

### Post by MadsRH on 2009-12-14
> **Exodist said:**
> Sadly Vista or Win7 folders have the best viewing so far.

Yes, MS did some nice work, but I really like the new KDE too.

I like this feature:
[IMG]http://thepadi.com/wp-content/uploads/2009/01/windows7-virtual-folders.jpg[/IMG]

Preview Mockup:
[IMG]http://fc01.deviantart.com/fs26/f/2008/112/0/7/Windows___Real_Live_Previews_by_Renn_Louie.png[/IMG]

I did **not** create this!

---

