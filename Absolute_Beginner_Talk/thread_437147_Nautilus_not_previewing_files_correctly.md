---
title: "Nautilus not previewing files correctly"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by hackle577 on 2007-05-08
I have several videos in ~/vids, ranging in size from 92MB to 177MB. They all use the same video codecs. However, some of them are being previewed and some aren't. My preview settings ("Other Previewable Files") are for local files under 10MB in size. However, *all* of the videos are over 10MB, but only some are being previewed and others are not.

I have tried changing the preview settings and running "touch * " in the directory, but there is still one file that is not being previewed. It is 137MB in size.

First, why are the files being previewed at all if I have the preview threshold at 10MB?

Second, why is the one file still refusing to be previewed? Weird.

---

### Post by David Corrales on 2007-05-08
I have the same problem with getting previews from items that shouldn't be previewed. It's like nautilus simply ignores whatever you set the limit to, and previews all the files it can.

---

### Post by hackle577 on 2007-05-11
Bump. Help?

---

### Post by SeanHodges on 2007-05-13
I'm not sure if anyone here has the answer you're looking for, at least at the moment.

Personally, I have only found that videos do not show a preview if I do not have the correct codec installed, such as old realmedia files (older than version 7). However, I do not usually have more than around 20 videos in a single directory, so perhaps the fact you have a lot of videos in your ~/vids directory might be an indicator to whats going wrong...

I suggest you submit a bug report on Launchpad at this point. I haven't found any existing reports that are similar to what you are experiencing. Also, if you could find a way to get the offending video on-line, and post a link on the report so they can try it themselves, it will make it much easier to reproduce.

---

