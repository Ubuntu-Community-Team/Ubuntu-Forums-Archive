---
title: "mediatomb... really basic problem"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by 13ojo on 2008-02-10
Howdy.

I set up media tomb etc etc. Works and i've been able to watch my videos etc.

But it chucks them all in the same folder? (all media or something like that). The other option, PC, goes through the folders i have but, when i get to some media in them, i can't open it anymore. Like it's just showing the folders but not the media.

This sucks as i have a very orgarnized by folder stucture for my stuff. And i would like to use that to select what video's i want to watch.

Think 100+ videos lol

---

### Post by happymellon on 2008-06-15
Hi, are you still having this issue?

Quick answer would be to edit you import.js. Should be in your /usr/share/mediatomb/js/ directory, you'll have to sudo edit it and look for the function called addVideo.

As you can see it is empty, hence why there are no folders in mediatomb. Replace with the following:

function addVideo(obj)
{
var dir = obj.location.substring(0, obj.location.lastIndexOf("/"));
dir = dir.substring(dir.lastIndexOf("/") + 1);
var chain = new Array('Videos', dir);
addCdsObject(obj, createContainerChain(chain));
}


This will pull the name of the directory that the file is in. You will have to reimport your videos, but you now have basic folder structure for your videos.

---

### Post by Joeb454 on 2008-06-15
I'm not sure if that user is still using the forums, their last activity was April 19th 2008.

Although I can see how your solution could help others :)

---

