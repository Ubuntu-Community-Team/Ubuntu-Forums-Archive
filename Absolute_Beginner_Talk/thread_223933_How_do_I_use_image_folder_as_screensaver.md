---
title: "How do I use image folder as screensaver?"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by Seren Lino on 2006-07-27
I installed Ubuntu on my old laptop, because I was told I need a Linux distro for school. So far I think it's great! :)

But I am kind of girlish, and I want images of my nephiew in my screensaver. There is an option called Image folder (my version is norwegian, so I'm not absolutely sure about the translation here..), but when I select that alternativ, the screen saver is blank (black). I have no option of selecting a folder here (or any other options beside the ones asking if I want my screen locked). 

So I am wondering - is there a certain folder I have to put the files in?

Also, I can't find the drivers for my graphic card (NM2200 [MagicGraph 256AV]) - if anyone has an idea about where I might find it, I would be happy! :)

If these questions are posted in the wrong forum, or there are simular posts, please excuse me. I did a search, but I found no posts who were relevant to my questions.
And if my english sucks, please excuse that too! :D

---

### Post by anodizer on 2006-07-27
Where is this "Image folder" option? Do you use 5.10 or 6.06?

---

### Post by editrix on 2006-07-27
I assume you mean the slideshow screensaver. Gnome removed the ability to configure screensavers, so you can't do it. You can in KDE, or you can install the X screensavers (not sure what it's called). 

Can't help with the Nvidia, except to say you should make your question a separate post if you can't get answers here. But there are many, many questions about Nvidia, so I assume there are answers, too, if you search :-)

---

### Post by Seren Lino on 2006-07-27
I use 6.06 (I think).
And the image folder option is almost at the top. Uhm, that's a bad explanation, I think. I might take a screen shot.
In my norwegian version, it is called "Bildemappe".

---

### Post by Seren Lino on 2006-07-27
> **editrix said:**
> I assume you mean the slideshow screensaver. Gnome removed the ability to configure screensavers, so you can't do it. You can in KDE, or you can install the X screensavers (not sure what it's called). 

Can't help with the Nvidia, except to say you should make your question a separate post if you can't get answers here. But there are many, many questions about Nvidia, so I assume there are answers, too, if you search :-)
Ok, thanks for the answer! :)
Where do I find the X screensavers?

I did a search on my graphic card name, but I found no posts who could help med. Maybe I am a searcher neewbie as well..

---

### Post by ovimunt on 2006-07-27
Why was the option to configure the screensavers removed in Gnome???

---

### Post by mcduck on 2006-07-27
> **Seren Lino said:**
> Ok, thanks for the answer! :)
Where do I find the X screensavers?

I did a search on my graphic card name, but I found no posts who could help med. Maybe I am a searcher neewbie as well..

There are some extra screensaver packages that you can install from Ubuntu repositories, one of these contains GLSlideshow screensaver wich works great for me (part of rss-glx package, I guess). I think it should look for pictures in a 'Pictures' directory inside your home dir, but you can also do what I did and make a link from the directory containing your images to /usr/share/backgrounds:
```
sudo ln -s /home/mcduck/Images/Wallpapers /usr/share/backgrounds/mcduck
```

---

### Post by jimmygoon on 2006-07-27
> **ovimunt said:**
> Why was the option to configure the screensavers removed in Gnome???

agreed.

---

### Post by Lew on 2006-07-27
If you create a folder in your Home folder called "Pictures" then the "Pictures Folder" screensaver will cycle through all of the pictures in the top level of that folder (ie: it won't traverse subfolders).  I discovered this as I have created the same folder structure in my Home folder as on my OS X machines.

Hope this helps.

---

### Post by gingermark on 2006-07-27
I'm a KDE user, and there is a superkaramba theme that can just show a slide-show on your desktop (it's called 'a-foto').

Gdesklets is the GNOME version of superkaramba, and there does seem to be [an equivalent 'desklet'](http://gdesklets.org/?mod=project/uview&pid=25). Of course, I've never used it myself, and if you are using an old laptop it might not be up to Gdesklets anyways, but it might be an option.

---

### Post by mostwanted on 2006-07-27
> **ovimunt said:**
> Why was the option to configure the screensavers removed in Gnome???

They went from X-screensaver to a new "in-house" program called Gnome Screensaver that doesn't have as many features yet. Probably should have waited. It's not part of an evil "remove all features" scheme that some anti-Gnome folks seem to think goes on behind the scenes.

To the OP: I import all my photos into F-Spot which is an excellent photo manager and just use the "create screensaver" option in that program.

---

### Post by Seren Lino on 2006-07-27
Thanks everyone for your answers - some helped, and others I didn't understand anything of.. :cool: 
As I said, I am quite new to Linux (have used RedHat for about 15 minutes a few years ago), but I am above average "user" in Windows, and have had a Mac once, so I am not totaly "blonde"! :D 

Right now, I am on my win pc, so I will take another look at your answers when I'm back on the laptop later to night. Thanks for all help so far, and I'll come back to this post if I still can't make it work! :)

---

### Post by aysiu on 2006-07-27
Actually, in KDE, you don't even need Superkaramba to do a slideshow on your desktop. It's an option in KControl already.

But, yes, this was a stupid move on the part of Gnome developers. It is not a confusing option to allow people to pick what folder they want the slideshow screensaver to come out of.

I ended up doing something like this: ```
sudo mv /usr/share/backgrounds /usr/share/backgrounds.old
sudo ln -s /my/pictures/folder /usr/share/backgrounds
```

---

### Post by Handyman's Special on 2006-07-28
> **Lew said:**
> If you create a folder in your Home folder called "Pictures" then the "Pictures Folder" screensaver will cycle through all of the pictures in the top level of that folder. . . .

Hope this helps.

Hello Lew,

Thanks! It worked for me. I had been looking for a way to accomplish this.

Odd there is no configuring allowed on the Screensavers, but as long as I can use this one, that's cool.

I do miss the clock screensaver but I am getting over it.

Cheers,
Handyman's Special

---

### Post by Clay85 on 2006-07-28
Seren Lino, your english is almost perfect. Much better than most natives I know.

---

### Post by nu2this on 2006-12-30
> **Lew said:**
> If you create a folder in your Home folder called "Pictures" then the "Pictures Folder" screensaver will cycle through all of the pictures in the top level of that folder (ie: it won't traverse subfolders).  I discovered this as I have created the same folder structure in my Home folder as on my OS X machines.

Hope this helps.
Just want to let everyone know this works in Edgy.

---

