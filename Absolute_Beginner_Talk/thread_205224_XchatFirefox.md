---
title: "Xchat/Firefox"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by bekok on 2006-06-28
hey,

I just installed xchat for Irc, but if i go to a site (like packetnews) and click on a link to let it open xchat, it says firefox isn't familiar with opening an url with "irc:".
Does anyone know i can set it up like that if i go to a "irc://" link, it opens in xchat?

danx

---

### Post by mcduck on 2006-06-28
I'm not sure if this works, but this is based on the way I registered lastfm:// protocol in Firefox:

1. Open Firefox and type 'about:config' as address.

2. Right click, select New, Boolean, and set Preference Name to 
'network.protocol-handler.external.irc' and set the value to 'TRUE'

3. Right click again, then select New, String and use 'network.protocol-handler.app.irc' as the Preference Name. (you might need to restart FF before you can do this)

4. set the path to point to xchat binary (/usr/bin/xchat? or simple 'xchat' mifgt work too..)

5. Restart Firefox - you have registered the protocol irc:// with xchat.

---

### Post by sagara on 2008-03-09
bekok, this post will help: [COLOR="Blue"][HOWTO: Open copy and open irc links into Xchat]("http://ubuntuforums.org/showpost.php?p=4484116&postcount=13")[/COLOR]

This is a manual solution to the problem.  I was not able to find a cleaner solution myself.

---

