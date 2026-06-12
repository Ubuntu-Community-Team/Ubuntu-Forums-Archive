---
title: "Where are the Internet Video Streams I watch, located in my Ubuntu?"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-08-09
Hello!

I sometimes watch Internet Video Streams on the Internet.

In order to watch them, these Streams have to Download in my Ubuntu.

Inside which folder do they reside into?

I would like to back them up, but I do not know where to locate them...

Thanks.

---

### Post by Paerez on 2006-08-09
they usually go to /tmp. Just open your home directory and navigate up to the root, then open "tmp".

---

### Post by dvarsam on 2006-08-10
> **Paerez said:**
> they usually go to /tmp. Just open your home directory and navigate up to the root, then open "tmp".

I went into the "/tmp" you suggested & found nothing...

I visited the site [http://www.ubuntuvideo.com/](http://www.ubuntuvideo.com/), watched some of their Tutorials & I would like to save a couple of them into my PC.

How can I do that?

Any ideas?

Thanks

---

### Post by Paerez on 2006-08-10
for the google video ones, click the icon in the bottom right and click "go to google video". Then, once the stream opens there, click on Download (even though it says windows/mac, it works fine in linux).

For the other ones, there is no direct download link, but if you are feeling adventurous, click on View->Page Source. Then, search for "dailymotion" which is the other stream on that page. Then, you will find the url:
[http://www.dailymotion.com/swf/4Hj4yEHIWd69p1TYB](http://www.dailymotion.com/swf/4Hj4yEHIWd69p1TYB)
If you try to download that, it fails :( but you can at least save the link and open it in firefox so it is much larger. This is because dailymotion doesn't offer a direct file download.

At least you can get the google video ones.

The reason these are not it tmp is because they are not pure video streams. It is actually Flash doing the streaming.

---

