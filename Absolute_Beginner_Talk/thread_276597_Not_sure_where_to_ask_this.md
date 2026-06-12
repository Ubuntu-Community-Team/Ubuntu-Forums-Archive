---
title: "Not sure where to ask this"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by binatice on 2006-10-13
I was looking at an article on Lifehacker, here is the [link]("http://www.lifehacker.com/software/skype/schedule-a-wake-up-call-with-skype-204425.php").
But it only gives intructions for Mac OS X and Windows. Would there be a way to do this with Ubuntu?

---

### Post by xyz on 2006-10-13
Hi,
I don't use Skipe, so I'm not sure this is what you're looking for!
But here is what I found:
[http://www.macosxhints.com/article.php?story=20051103212758617](http://www.macosxhints.com/article.php?story=20051103212758617)
Let me know...
Is this stricly for Mac?

---

### Post by alexfittyfives on 2006-10-13
Hi,

Although that's a shell script (and thus should work) the line:

> osascript -l AppleScript -e "tell application "Skype" to get URL "callto://$1""

is it trying to do something with applescript which is an apple only scripting language.

I thought that you might be able to change that line to:

>  skype-callto-handler --session "callto://$1"

but that doesn't seem to work, I get the error:
> ERROR: Failed to connect to DBUS daemon!

Which seems to be due to [skype using an old DBUS version]("http://forum.skype.com/lofiversion/index.php/t64059.html"). (from Skype forums)

Anyone know another way? This woud be a cool little hack...

Alex

---

