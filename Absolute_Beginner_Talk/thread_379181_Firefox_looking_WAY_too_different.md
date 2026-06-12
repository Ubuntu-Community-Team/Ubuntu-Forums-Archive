---
title: "Firefox looking WAY too different"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by mackyman on 2007-03-08
Heya all! Again...

I just installed firefox on my new computer, and now tries to fix some stuff that have been going on, on all my earlier Ubuntu/Kubuntu installs.

In firefox, many thinks looks way to different from windows, and that's really annoying to not know how the page looks on the viewers computer as a web developer.

These things have been coming up all the time:

1. Even thou I have the msttcorefonts installed, and use verdana on a page, the font is slightly larger on my Kubuntu install than on windows, and with menu's, that's irritating (2 line menus is **NOT** nice).
SOLVED: Installed the msttcorefonts package

2. When using different inputs, they look different. Like 
<input type="file" .... behaves really different. When setting width to 100%, it sets the textarea too 100% instead of the textarea AND the browse for file button too 100%, wich is quite annoying... 
I solved a problem with the checkboxes looking ridiculous from searching these forums, but can't find anything about type="file". 
All sorts of buttons looks strange too... Can I change these buttons back somehow?

And these stuff only show up in Firefox, not Opera or IE (No, I ain't surfing in IE, I just preview my pages there. So I ain't suicidal ;) )

Thanks in advice//

Markus

[EDIT] ARG! My previous installation of mstcorefonts seemed not to have worked... Installed them again and it worked....[/EDIT]

---

### Post by jms1989 on 2007-03-08
What verison of firefox and ubuntu are you using?

---

### Post by mackyman on 2007-03-08
I'm on Kubuntu 6.10 Edgy with firefox 2.0.0.2.

But it has been like this since I began using Ubuntu dists... Ie, about Ubuntu 5.10 with firefox ~1.5

---

### Post by undertakingyou on 2007-03-08
> **mackyman said:**
> Heya all! Again...

And these stuff only show up in Firefox, not Opera or IE (No, I ain't surfing in IE, I just preview my pages there. So I ain't suicidal ;) )



I do the same thing with my web-development. I just check it in those other browsers so that everything looks the same across platforms.  I haven't noticed the second problem on ubuntu though, can you give a URL to your sight so I could look?

---

### Post by jms1989 on 2007-03-08
> **mackyman said:**
> I'm on Kubuntu 6.10 Edgy with firefox 2.0.0.2.

But it has been like this since I began using Ubuntu dists... Ie, about Ubuntu 5.10 with firefox ~1.5

Can I ask that you give us a screenshot of the problem?

---

### Post by mackyman on 2007-03-08
Shure...

And thx btw for the short notice help

Attached a screenshot

---

### Post by jms1989 on 2007-03-08
It like it's a coding error in the file. Possibly something directed only to firefox browsers.

Btw, I looked at the site on my browser and it's showing the same thing. The problem could be in the code itself.

EDIT: I looked at it on Opera 9 and everything appears fine. I attached a file of what it looks like on Opera 9.

---

### Post by undertakingyou on 2007-03-08
OK, now I fully understand you.  Firefox just displays that stuff differently.  To overcome this I had to do the following ```
<input name="pic" type="file" style="width: 350px;" [COLOR="Red"]size ="55"[/COLOR]>
```

So, if you have your style width tag, that will take care of IE and Opera, but firefox seems to ignore this.  Set your size tag for FireFox.  I don't know if it will accept a 100% value or not.  Try it out and see if that helps.

---

### Post by Repent on 2007-03-08
Looks just fine on my FireFox.


[IMG]http://i17.tinypic.com/2hxq5y0.png[/IMG]

---

### Post by jms1989 on 2007-03-08
Um, Repent, it's not showing the problem area. The problem is where the "browse" button is.

---

### Post by mackyman on 2007-03-09
The funny stuff is that in windows (wich I developed the page in), on firefox it displays the site correctly...

And as I scanned trough my main css file, I atleast found one place where I had forgotten a ;, so I will check that and se if it corrects the file.

And btw, can you change those darn ugly styled buttons? I hate that button style... If you can't, I will shurely design all my own buttons henchforth...
And for some reson my button pic's don't display... But I guess I have to scan trough the code again... And change all those buttons to links with buttonlike images...

---

### Post by jms1989 on 2007-03-09
I don't see any buttons styles, because I don't know what to look for.

Btw, where is your target audience located?

---

### Post by mackyman on 2007-03-10
Button styles, the way the buttons look.. .Hate that look...

And my target audience is swedish ppl, and the most of the probably on Windows/Mac computers, so they won't be harmed of that the page don't look as intended on Linux, but I like to make it look correct there too.

And as I now are going to start develope my pages on linux, I want it too look the same as in windows, so I know how they see the page...

And I didn't think that firefox on windows/linux showed the pages different... It's the same browser after all...

---

### Post by Repent on 2007-03-10
lol....I'm sorry my bad.

---

