---
title: "how to change fonts in opera?"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-03-08
how to change fonts in opera for LINKS alone?
it appears too bold.see the screenshot

---

### Post by oliviacond on 2008-03-09
i think the problem lies on the whole font not just the link font only.
try to use serif.

---

### Post by olejorgen on 2008-03-09
I suppose you know about preferences -> web pages. To only change link fonts, I think you'll have to write a user css file.

---

### Post by adi_das on 2008-03-11
Where is Sans Serif Fonts in Opera?

---

### Post by st0n3cutt3r on 2008-03-11
it's giving extra weight to the search term you used!

You searched for "ubuntu" so every time ubuntu appears on the page, google automatically makes it bold so that it is easier for you to notice.

---

### Post by adi_das on 2008-03-11
No i tried all the terms that i wanted to.

---

### Post by st0n3cutt3r on 2008-03-11
what do you mean?  that screen shot only shows **ubuntu** bold over and over again.  The rest of the links are exactly the same weight as the rest of the font.

---

### Post by adi_das on 2008-03-11
Look at this snapshot. The search query is so bold.

---

### Post by st0n3cutt3r on 2008-03-11
you can create a stylesheet in a text editor containing the following code:
```
a {font-weight: normal !important}
```
and then save it as what_ever_you_want.css and point opera to it in **Tools** < **Preferences...** < **Advanced** (tab) < **[Style options...]**(button) < **Display** (tab)    and then at the bottom there's a field with a **[Choose...]** (button) next to it.  Click **[Choose...]**, navigate to your newly created .css file, click **[Okay]**, and you should be set.

---------------------------------------------------------------------------------

Just for the record, the issue is not Opera though, it's Google.

---

### Post by adi_das on 2008-03-11
I tried in yahoo, aol and ask. But its looks same

---

### Post by st0n3cutt3r on 2008-03-11
did you try in firefox?

I would not be surprised at all if most search engines hilighted the search term in that way. It's kind of a no-brainer, and very convenient. 

It's possible that websites could override the CSS that I gave you, but short of hacking Opera or doing something crazy with linux to prevent it from ever showing bold text (perhaps deleting the bold face for all of your fonts?) I don't think you can force it in any other way...

You could always use Opera's zoom feature to zoom out...   (just press **-** )

---

