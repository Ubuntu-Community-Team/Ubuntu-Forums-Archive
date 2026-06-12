---
title: "Firefox Dictionary Location"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by StSteven on 2007-06-28
I accidentally added a misspelled word to the dictionary and have no idea how to remove it.  I can't find the dictionary.  Anyone...anyone...

---

### Post by greg_g on 2007-06-28
I took a look at this website:
[http://cavemonkey50.com/2007/03/edit-firefoxs-spelling-dictionary/](http://cavemonkey50.com/2007/03/edit-firefoxs-spelling-dictionary/)

But I do not personally have that file.  I also didn't manually edit/add anything.  Maybe that helps??

greg

---

### Post by starcraft.man on 2007-06-28
The firefox dictionary location isn't where he specified. I just went and found it. Here is the path I took to get there.

Of course start from in your home/user folder. Then this is how I went:

~/.mozilla/firefox/[COLOR="Red"]xxxxxx.default[/COLOR]/extensions/[COLOR="Blue"]en-CA[/COLOR]@dictionaries.addons.mozilla.org/dictionaries$

The xxxxx I highlighted in red, will be different for you, its a random garble of numbers. The blue represents the dictionary, you may have more than one, my primary one is of course Canadian English as is seen, yours may be different.

Once in the dictionary folder, open the .dic file up with a text editor, and then find the word you want to remove, I believe that is it, then just save out and make sure its still .dic.

---

### Post by greg_g on 2007-06-28
Sorry about the misinformation.  Let this be a lesson, Google doesn't always know exactly what you are looking for, take what it says as recommendations :)

greg

---

### Post by StSteven on 2007-06-28
Actually, mine was right where the site said it would be, not under extensions...thanks...that does it...

---

