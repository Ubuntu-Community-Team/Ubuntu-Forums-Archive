---
title: "Mailto Thunderbird not working!!!!"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-11-25
I Can't fix my Thunderbird to open from mailto: "hypertext links". I use xubuntu edgy.

---

### Post by rfruth on 2006-11-25
What web browser opens mailto links now ?  What would you like, Firefox ?

---

### Post by crimesaucer on 2006-11-25
I only have Firefox 2.0 and it won't open Thundebird from mailto: links.

I installed Evolution earlier and it opened up mailto: links but was unable to connect through smtp for some reason.

....and gmail won't open through mailto:links using Thunderbird either, I don't know what to do, I've read some forums, written some new strings and paths and nothing has fixed the problem.

---

### Post by jerrykenny on 2006-11-25
Have you tried both "thunderbird" and "mozilla-thunderbird"  ?

---

### Post by adam.tropics on 2006-11-25
You could always try adding
```

user_pref("network.protocol-handler.app.mailto","/usr/bin/mozilla-thunderbird");
```to your user.js file. (create it if it isn't there)

Or from about:config, adjust 
> 
user_pref("network.protocol-handler.app.mailto", "/usr/bin/mozilla-thunderbird");
user_pref("network.protocol-handler.external.mailto", "true");

---

### Post by crimesaucer on 2006-11-25
for the strings in about:config ? or elsewhere?

---

### Post by crimesaucer on 2006-11-25
I think the external has been set to false, I'm going to change it right now and see,

This is the forum i was reading earlier, it's kind of old: [http://www.ubuntuforums.org/showthread.php?t=22333&page=1](http://www.ubuntuforums.org/showthread.php?t=22333&page=1)

---

### Post by crimesaucer on 2006-11-25
No, it was set to true, it was warn-external and expose that were set to false, are those the correct settings?

---

### Post by crimesaucer on 2006-11-25
Hey Jerry Kenny, did you mean trying to modify the string to /usr/bin/thunderbird instread of /usr/bin/mozilla-thunderbird". I'm going to give that a go right now.

---

### Post by adam.tropics on 2006-11-25
Well, they're the same as mine, so I assume so

---

### Post by crimesaucer on 2006-11-25
Thanks for helping anyway, I might just try to get Evolution working since I only tried to configure it for a few minutes, unless anyone else has an idea?

---

### Post by rfruth on 2006-11-25
Not sure how in Xubuntu but with Gnome System > Preferences > Preferred Applications sets the default web browser & email program, here is mine

[ATTACH]19998[/ATTACH]

---

### Post by crimesaucer on 2006-11-25
Thanks, I'll check it out.

---

### Post by crimesaucer on 2006-11-25
Preferred Applications in xubuntu had Firefox and Thunderbird as default apps, so I'm just wondering how I can fix this mailto: situation.

---

### Post by rfruth on 2006-11-25
I not helping, ya might want to ask on the Xubuntu forum
although I'd bet dollars to donuts someone here knows ...
[http://www.xubuntu.info/e107_plugins/forum/forum.php](http://www.xubuntu.info/e107_plugins/forum/forum.php)

---

### Post by crimesaucer on 2006-11-25
Cool, I'll give them a try since I haven't gotten one response from Firefox forum or Thunderbird forum,

so thanks for the help anyway, latter.

---

### Post by rfruth on 2006-11-25
Does Firefox (not Tbird) know its the default browser ?

[ATTACH]20004[/ATTACH]

---

### Post by crimesaucer on 2006-11-25
You know what, I checked that earlier and it wasn't checked as default, so I checked it's box and restarted, but it didn't do thing. And when I click on the "check now" box, I get no response at all.

I'm thinking something installed weird, since I had some panel disappearances at first, but I'm so happy with my configuration (Beryl and all my apps working perfectly) that I don't want to mess things up. 

I just wish I could fix this or at least get evolution to send mail.

---

### Post by dermotti on 2006-11-26
[http://www.xubuntu.info/e107_plugins/forum/forum_viewtopic.php?372.0#post_374](http://www.xubuntu.info/e107_plugins/forum/forum_viewtopic.php?372.0#post_374)

I got it to work.

---

### Post by crimesaucer on 2006-11-26
I got "mailto" to work too, I realized what my problem was. 

It wasn't that the strings for "about:config" weren't working, it was that when I first installed xubuntu, I had named the computer wrong during installation and had to rename it in the Network-->--General-->--Host name: settings.

So Thunderbird was using my old computer name in configuration for "name" and not allowing the mailto: to work since I had renameed the computer. I feel like a big idiot now.

Thanks for the help anyway.

---

### Post by dermotti on 2006-11-26
In for voice of James T. Kirk

"KHHHAAAAAAAAANNNNN!!!!"

---

