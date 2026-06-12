---
title: "CastPodder install"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2006-03-27
Need some help b/c I'm very new to Ubuntu/Linux world.  However I subscribe to a number of podcasts in the Windows world and want to have access on Linux side.  I've downloaded the CastPodder tarball (I'm just learning about tarballs but my understanding is this is like a zipped file) and have 'extracted' it to a desktop file but now I'm stuck without an install.  I tried alt-F2 and input CastPodder but get an error:
[COLOR="Red"]Cannot display location 'file://CastPodder'
[/COLOR]
Not sure how to proceed with install.  Directions please?  Thanks.

---

### Post by cbudden on 2006-03-27
[QUOTE=flyingsolo]Need some help b/c I'm very new to Ubuntu/Linux world.  However I subscribe to a number of podcasts in the Windows world and want to have access on Linux side.  I've downloaded the CastPodder tarball (I'm just learning about tarballs but my understanding is this is like a zipped file) and have 'extracted' it to a desktop file but now I'm stuck without an install.  I tried alt-F2 and input CastPodder but get an error:
[COLOR="Red"]Cannot display location 'file://CastPodder'
[/COLOR]
Not sure how to proceed with install.  Directions please?  Thanks.[/QUOTE]

I would advise downloading the .deb file instead, and installing with ```

sudo dpkg -i CastPodder.deb

```

After installing the .deb, you will be able to run castpodder from the gnome menu, or by the commend CastPodder


edit

Just tried to get the link to the deb file, but the website is down.

---

### Post by timsch75 on 2006-03-28
If you mean [http://www.castpodder.net/](http://www.castpodder.net/), it is back up, as far as I can tell.  I did not find a .deb file on there.

To answer the first post, read both the README and INSTALL files for your answer.  Unfortunately, there are some prerequisites that are not easy to find, so my tarball install is stalled.  I'll wait for the .deb, or will convert a .rpm if I can find that.

---

### Post by Albalabs on 2006-09-01
The .deb file link is in the center of the page.  It is accessed by clicking on the graphic of TUX and FREEBSD under the DOWNLOAD button.  Hope this helps.

---

