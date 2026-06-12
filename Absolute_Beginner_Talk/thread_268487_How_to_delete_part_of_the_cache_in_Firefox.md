---
title: "How to delete part of the cache in Firefox?"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by woodlandjustin on 2006-09-30
I'm having a problem with the yahoo mail page, and I think it may be caused by the cache? So I want to check by deleting only the cache for the yahoo mail page. How do I do that? I did a search in "computer" for "cache" and it came with 0 results, so I have no idea where the folder is.
Thanks
Justin

---

### Post by gvgerman on 2006-09-30
I don't believe it is possible to delete part of the cache with Firefox. Clearing the entire cache doesn't hurt or break anything; it just means the browser will have to pull all items off the web vs. part of the information out of the cache.

You can specifically delete cookies.  Select Edit > Preferences > Privacy > Cookies (tab) > View Cookies (button).

Your problem may be that the ability to display certain web elements are not yet loaded on your system, such as the Macromedia / Adobe Flash Player.

---

### Post by klytu on 2006-09-30
> **woodlandjustin said:**
> I'm having a problem with the yahoo mail page, and I think it may be caused by the cache? So I want to check by deleting only the cache for the yahoo mail page. How do I do that? I did a search in "computer" for "cache" and it came with 0 results, so I have no idea where the folder is.
Thanks
Justin

You can try:

```
sudo updatedb
```

Wait for that to finish, then do:

```
locate cache | grep firefox
```

This should lead you to a directory that has a weird combination of numbers and letters with a ".default" extension where your firefox cache lives. However, I don't think you'll be able to use that information directly to do what you want as far as deleting just a specific part of the cache.

---

### Post by aysiu on 2006-09-30
Sure it's possible.

Just go to /home/*username*/.mozilla/firefox/*profilename*/Cache and find the pages you want to delete.

Honestly, though, why not just clear out your whole cache? Are you on dial-up?

---

### Post by klytu on 2006-09-30
> **aysiu said:**
> Sure it's possible.

Just go to /home/*username*/.mozilla/firefox/*profilename*/Cache and find the pages you want to delete.

Honestly, though, why not just clear out your whole cache? Are you on dial-up?

I actually tried this before responding to the original poster, but I couldn't figure out how to delete specific pages. 

*Off Topic: Aysiu, I enjoyed reading a lot of your interesting essays [here]("http://www.psychocats.net/essays/"). Nice web pages!*

---

### Post by aysiu on 2006-09-30
> **klytu said:**
> I actually tried this before responding to the original poster, but I couldn't figure out how to delete specific pages. Do you mean when you right-clicked and tried to move to trash, you were unable to? Did you get an error message? 

> *Off Topic: Aysiu, I enjoyed reading a lot of your interesting essays [here]("http://www.psychocats.net/essays/"). Nice web pages!* Thanks.

---

### Post by klytu on 2006-09-30
> Do you mean when you right-clicked and tried to move to trash, you were unable to? Did you get an error message? 

No, I mean I was unable to figure out what specific parts of the cache corresponded to any particular web page. My cache folder contains a number of images and a number of files with encrypted names. I could delete files, but I was unable to determine what web pages those files corresponded to.

---

### Post by aysiu on 2006-09-30
Apart from sorting by file type, I think I see how the cache would get too big to handle.

I would just delete the entire cache. Even on dial-up, it can't take that long to reload pages.

---

