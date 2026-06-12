---
title: "Pop3 thunderbird and Firefox2 on xubuntu"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-11-21
Hello, my Thunderbird won't open when I click onto an email link on a web page. I am unable to open the Thunderbird "Compose Letter" app directly from an email link. For example, my Thunderbird won't open when using craigslist.

Can I fix this, I'm using xubuntu 6.10.

Thanks.

---

### Post by crimesaucer on 2006-11-21
still unable.

---

### Post by kc8hr on 2006-11-21
> **crimesaucer said:**
> Hello, my Thunderbird works fine on my applications menu, but it won't open from my Webpedia toolbar's email checker, and it won't open from any other email extension or toolbar, and most importantly, it won't open when I click onto a link on a web page to send a letter.

My Webpedia email checker will show how many emails I have in the in-box, and it will show new mail when it comes in, but when I click on the email box, nothing happens. gmail and yahoo mail will both open fine.

I am also able to send mail, but when I click on a link in a web page with someones email address on to contact them, nothing happens and I have to do it manually.

Can I fix this, I'm using xubuntu 6.10 with Beryl.

Thanks.Nothing to it. In Firefox or Mozilla, type 'about:config' into the address bar, then right click anywhere on that page. Select New>String, and add the following: 

network.protocol.handler.app.mailto <enter>
path-to-thunderbird<enter>

You should be good to go. Also, make sure that Thunderbird is the default mail program in Gnome.

Good Luck!
Tim

---

### Post by crimesaucer on 2006-11-21
It didn't fix the problem, thanks anyway. Anybody else able to help?

---

### Post by crimesaucer on 2006-11-22
***Bump.***

So the question still is: How can I enable my thunderbird "compose letter" to open from an email address link in a web page. And also open the inbox from an extension or toolbar on Firefox2, for example, the email notifier on the Digg toolbar.

---

### Post by kc8hr on 2006-11-22
> **crimesaucer said:**
> Thanks, but it didn't work for some reason. 

I'm on xubuntu 6.10 using beryl. How would I see if my xfce has Thunderbird as my default email?

Thank you.Sorry, it's been awhile since I have used XFCE. I don't remember.

---

### Post by crimesaucer on 2006-11-22
Thanks for the help anyway.

---

### Post by crimesaucer on 2006-11-24
Just reopening this topic since the problem hasn't been fixed yet.

---

### Post by crimesaucer on 2006-11-24
I apologize for so many posts, but nobody has had a way to fix this from this forum, the Mozilla Firefox forum, and the Mozilla Thunderbird forum.

---

### Post by AmandaKerik on 2007-02-01
I'm not sure of a solution, but I can understand your frustration...

Have you looked into the Firefox add-ons for this? I know there's one that pulls up the web version of gmail / yahoo / hotmail when you rightclick on a mailto (e-mail link)...

If you have Thunderbird open, does it still act clueless when you click on an e-mail link? I have a shortcut to TB in my top bar.

And you are right - it should be bringing up a compose page with the click. It's probably some arbitrary setting hidden somewhere that's turned it off. 

I don't know if the people here just need more info, or they just don't know how to answer and have "left it open for others to answer" ... which can seem like a deafening silence or even a snub. :( 

Keep looking for a solution... I hope you find it (and share it).

I hope this has helped a bit,
Amanda

---

### Post by crimesaucer on 2007-02-01
Thanks for caring, I did fix this back in November and I should of posted that if you change the name of your computer in the Network Process Manager (liker it shows you how to do in the wiki page), then the Thunderbird app will still have your old computer's name in the "your name" dialog box. And if you have the wrong name there, the mailto link doesn't work.

And if you're completely an idiot like me, when you change that name to your new computer's name, and you mis-spell it, and then think you had done everything correctly, you will drive yourself crazy trying to figure out what the problem was.

---

### Post by AmandaKerik on 2007-02-02
I wouldn't have figured out that connection... Congrats

---

