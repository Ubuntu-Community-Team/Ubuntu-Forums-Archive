---
title: "[SOLVED] Firefox dropdown remove button"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by farueulogy on 2008-03-26
Does anyone know how to make the button circled below disappear?

I **don't** want to clear the address list or anything - I just don't like the button.
[IMG]http://lh6.google.com/albertblack/R-pcb1GsCqI/AAAAAAAAAGo/ufekWHrWBu0/s800/Screenshot.png[/IMG]

---

### Post by kolisikepu on 2008-03-26
But it's on all browsers, IE7, Firefox, etc....

---

### Post by farueulogy on 2008-03-26
> **kolisikepu said:**
> But it's on all browsers, IE7, Firefox, etc....
Don't like it.

I figure there has to be an extention/skin option to remove it.

---

### Post by y-lee on 2008-03-26
Hmmm never thought about it, but it can be done :)


To do so you need to add the code below to your **userChrome.css** file if you have one. 


```
/* hide the dropmarker in the Address url toolbar */
.autocomplete-history-dropmarker {
  display: none !important;
}
```

If you don't have one you got to create one see [UserChrome ]("http://kb.mozillazine.org/UserChrome.css") for info on doing that.

Note this file is found** /home/username/.mozilla/firefox/xxx.default/chrome** where *username* is your username and *xxx *is a seemingly random string of characters and *default* is your FireFox profile name

Also note the mozilla folder  is hidden so enable view hidden folders in your file manager to find it.

Hope this helps :)

Edit: this works in Firefox 2.0.* I can make no promises for FF 3.0, I think they redid the location bar so I'm not sure if this will work. My guess is it would tho ;)

---

### Post by DJ_Peng on 2008-03-26
I seem to remember seeing an extension that does it. You could ask at the Mozillazine Forums (link in my sig). If anyone knows of how to get rid of it, someone there will.

---

### Post by y-lee on 2008-03-26
> **DJ_Peng said:**
> I seem to remember seeing an extension that does it. You could ask at the Mozillazine Forums (link in my sig). If anyone knows of how to get rid of it, someone there will.

I looked for an extension but went for the userchrome thing since i found it first and it worked for me, now of course i gotta undo this change cause I actually use that drop down menu :lolflag:

An extension would be nice tho so if anyone finds one let us know :)

---

### Post by DJ_Peng on 2008-03-26
I'd definitely suggest posting a request in the Extensions and Themes section of Mozillazine to let people know you're looking for it. It may not get made immediately, but that's the best place to put a bug in someone's ear.

---

### Post by farueulogy on 2008-03-26
> **y-lee said:**
> Hmmm never thought about it, but it can be done :)


To do so you need to add the code below to your **userChrome.css** file if you have one. 


```
/* hide the dropmarker in the Address url toolbar */
.autocomplete-history-dropmarker {
  display: none !important;
}
```

If you don't have one you got to create one see [UserChrome ]("http://kb.mozillazine.org/UserChrome.css") for info on doing that.

Note this file is found** /home/username/.mozilla/firefox/xxx.default/chrome** where *username* is your username and *xxx *is a seemingly random string of characters and *default* is your FireFox profile name

Also note the mozilla folder  is hidden so enable view hidden folders in your file manager to find it.

Hope this helps :)

Edit: this works in Firefox 2.0.* I can make no promises for FF 3.0, I think they redid the location bar so I'm not sure if this will work. My guess is it would tho ;)

perfect solution - all fixed :)

---

### Post by y-lee on 2008-03-26
Cool. 

Glad it worked, go ahead and mark this as solved.

Btw you can also remove the go button, i think it is an about:config hack. I did it once but didn't care for it and switched back. One of the reasons I love firefox is because it is so very customizable once you learn the ins and outs of the various config files, not to mention the thousands of add ons :)

---

