---
title: "GIMP multiple layer select"
date: 2012-09-13
forum: Art &amp; Design
---

### Post by mathfreak123 on 2012-09-13
Hello everyone!

I noticed that GIMP does not allow multiple layer select currently. There are some plugins that reproduce some of the functionality that multi-layer select provides, but I would like to actually be able to do multiple selections.

[A bit of Googling]("http://gimpforums.com/thread-no-way-to-select-copy-paste-multiple-layers") seems to suggest that there are no plans to implement multi-layer selections. Instead, there seem to be a bunch of inconvenient workarounds. I also remember reading somewhere that, "If you want this feature, implement it yourself." I'm afraid this might be a very daunting task for myself (since I have only taken some introductory courses to C and C++, I am not familiar with the finer details of open source code, and I haven't done it before etc. etc.), but I'm not afraid to dive in to take a look around.

Any guidance for me (whether that would be to download the source code, look at which files, etc.)?

---

### Post by Bucky Ball on 2012-09-13
*Thread moved to **Art & Design***

---

### Post by ofnuts on 2012-09-14
> **mathfreak123 said:**
> Hello everyone!

I noticed that GIMP does not allow multiple layer select currently. There are some plugins that reproduce some of the functionality that multi-layer select provides, but I would like to actually be able to do multiple selections.

[A bit of Googling]("http://gimpforums.com/thread-no-way-to-select-copy-paste-multiple-layers") seems to suggest that there are no plans to implement multi-layer selections. Instead, there seem to be a bunch of inconvenient workarounds. I also remember reading somewhere that, "If you want this feature, implement it yourself." I'm afraid this might be a very daunting task for myself (since I have only taken some introductory courses to C and C++, I am not familiar with the finer details of open source code, and I haven't done it before etc. etc.), but I'm not afraid to dive in to take a look around.

Any guidance for me (whether that would be to download the source code, look at which files, etc.)?

What do you call "multi-layer select"? And what would you want to do with it?

---

### Post by prokoudine on 2012-09-21
> **mathfreak123 said:**
> [A bit of Googling]("http://gimpforums.com/thread-no-way-to-select-copy-paste-multiple-layers") seems to suggest that there are no plans to implement multi-layer selections.
That is incorrect :) There are plans for that. In fact, selection of multiple items is partially done in 2.8, but doesn't work in grid view and, AFAIK, hence isn't even exposed in UI. If you try list view for e.g. brushes, you'll see that you can select several ones, so there's a start.

> **mathfreak123 said:**
> I'm afraid this might be a very daunting task for myself (since I have only taken some introductory courses to C and C++, I am not familiar with the finer details of open source code, and I haven't done it before etc. etc.), but I'm not afraid to dive in to take a look around.

Any guidance for me (whether that would be to download the source code, look at which files, etc.)?

Start with wiki.gimp.org.

---

### Post by prokoudine on 2012-09-21
> **ofnuts said:**
> What do you call "multi-layer select"? And what would you want to do with it?
E.g. select several layers and place them into a newly created layers group. Or move up/down the stack. Totally makes sense.

---

### Post by ofnuts on 2012-09-21
> **prokoudine said:**
> E.g. select several layers and place them into a newly created layers group. Or move up/down the stack. Totally makes sense.

For management, OK. But since the selected layer is also the active layer:

For transforms, that could be another way to implement links.

But for paint tools? Gimp paints all layers or is one layer "more selected" than others?

---

### Post by mathfreak123 on 2012-09-22
> **prokoudine said:**
> That is incorrect :) There are plans for that. In fact, selection of multiple items is partially done in 2.8, but doesn't work in grid view and, AFAIK, hence isn't even exposed in UI. If you try list view for e.g. brushes, you'll see that you can select several ones, so there's a start.



Start with wiki.gimp.org.

Well, that's certainly good to know! I'll check out that wiki later to check things out.

I wanted to mess with GIMP sort of as a little project to continue learning more about programming. What gave me this idea was when I was trying to make an animated GIF, I wanted to remove some layers. I learned that the layers had to be deleted 1-by-1, or through a script that deleted a range of layers. If I wanted to arbitrarily delete several layers, however, the task would have been a bit inconvenient.

---

