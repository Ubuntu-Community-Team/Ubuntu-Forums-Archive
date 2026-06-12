---
title: "How can I make Firefox load faster at startup?"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-08-15
How can I make Firefox load faster at startup?  I already did the below setup from Wiki but my Firefox still  take very long to load at startup.  I'm using 8 add-ons programs on FF.  Is there more tweaking one can do?

```

Address Bar -> about:config

Filter: ->
network.dns.disableIPv6 -> true
network.http.pipelining -> true
network.http.pipelining.maxrequests -> 8
network.http.proxy.pipelining -> true


How to load Web site faster in Mozilla Firefox

* Speed Up Firefox Web Browser Tips

* Applications -> Internet -> Firefox Web Browser
* Mozilla Firefox
```

---

### Post by arijarot on 2007-08-15
I don't know if this is true, nor do I remember where I read this, but apparently, installing and using the "regular" firefox for linux (and not using the one that comes preinstalled with ubuntu) is faster for some reason. maybe you could give it a try?

---

### Post by skymera on 2007-08-15
even better.

swiftfox
swiftweasel

or any other animal named alternative i guess

---

### Post by Hazmat. on 2007-08-15
Jingo, you helped me, so i'll help you.

Try swift fox. ([http://getswiftfox.com/](http://getswiftfox.com/))


Lol, wow i just realized it's been posted already but i'll tell you anyways...,i've known this forever, i remembered link for when i got linux.

Ok, i found something that may help you.


This will speed up firefox way faster, i've tested it. I don't know if it only works for windows, or not.

Type this into your browser:about:config locate and change these values, you cannot and don't need to change the variable type.
```

network.http.max-connections :42 (integer)
network.http.max-connections-per-server :21 (integer)
network.http.max-persistent-connections-per-server :22 (integer)
network.http.pipelining :True (boolean)
network.http.pipelining.maxrequests :33 (integer)
network.http.proxy.pipelining :True (boolean)

```


Also create this Integer
```

(rightclick-->new-->integer)

nglayout.initialpaint.delay = 0 (integer)

Add this new boolean
(rightclick--->new-->boolean)

browser.turbo.enabled=True (boolean)

```

~Haz

---

### Post by Mazza558 on 2007-08-15
> **Hazmat. said:**
> .

This will speed up firefox way faster, i've tested it. I don't know if it only works for windows, or not.

Type this into your browser:about:config locate and change these values, you cannot and don't need to change the variable type.
```

network.http.max-connections :42 (integer)
network.http.max-connections-per-server :21 (integer)
network.http.max-persistent-connections-per-server :22 (integer)
network.http.pipelining :True (boolean)
network.http.pipelining.maxrequests :33 (integer)
network.http.proxy.pipelining :True (boolean)

```

[/code]

~Haz

Just a small note - changing the max-requrests value changes the amount of connections to the server by X (X being the value you choose). If you chose max connections to be 8, it's the equivalent of 8 people connecting to the server at the same time. For this reason, it puts more strain on the servers and some smaller websites may block you after a while, especially if you're continually rereshing the page. I don't honeslty recommend having a max connections value at 42 - it'd be hell for less powerful servers.

---

### Post by crimesaucer on 2007-08-15
Read about the proper settings for maxrequests here: [http://kb.mozillazine.org/Network.http.pipelining.maxrequests](http://kb.mozillazine.org/Network.http.pipelining.maxrequests)


Read all of these tweaks suggested by Firefox themselves here: [http://kb.mozillazine.org/Category:Tweaking_preferences](http://kb.mozillazine.org/Category:Tweaking_preferences)

---

### Post by PCFascist on 2007-08-15
I just installed Swiftfox and just my normal mozilla comes up. Strange....

---

### Post by jingo811 on 2007-08-16
Tnx for the swiftfox tip ppl.  A web browser custom built just for my specific CPU brand now that's sexy 	=P~

---

### Post by crimesaucer on 2007-08-16
> **PCFascist said:**
> I just installed Swiftfox and just my normal mozilla comes up. Strange....

I use both Swiftfox and Swiftweasel...can you explain about your problem? You should have a separate Swiftfox icon and it should load your browser with the exact same extensions/themes/bookmarks/about:config settings and userChrome.css as your regular Firefox was....the only thing I had to do with Swiftfox (and not Swiftweasel), was to copy my java plugin and flash plugin to my /opt/swiftfox/plugins folder to make java and flash work. I also had to copy my Ubuntu forum's debsearch.src and debsearch.gif into my /opt/swiftfox/searchplugins to add my Ubuntu Package Search to my Swiftfox and Swiftweasel search engines. (Swiftweasel is located at: /usr/local/swiftweasel/searchplugins)

---

