---
title: "Keyconfig in Firefox - how do I add my special keys?"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by thedaylights on 2008-01-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/firefox/+bug/24582](https://bugs.launchpad.net/firefox/+bug/24582) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I followed some advice on another [thread]("http://ubuntuforums.org/showpost.php?p=3265183&postcount=30") to map my special keys [back] and [forward] on my Lenovo X60 keyboard. They work in most apps, but just not Firefox cuz it's special that way. I'm trying to assign them using keyconfig now. But I don't know how to use keyconfig. Any help?

I made a file called multikeys in usr/local/bin/multikeys with these entries:
xmodmap -e 'keycode 159=XF86LaunchA'
xmodmap -e 'keycode 234=XF86Back'
xmodmap -e 'keycode 233=XF86Forward'

So I guess the key codes are XF86Forward and XF86Back?

---

### Post by hobo on 2008-01-27
Maybe this link will help.

[http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#Firefox](http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#Firefox)

---

### Post by thedaylights on 2008-01-27
Hobo - thanks but that is where I got the original information. It doesn't say how keyconfig is used.

---

