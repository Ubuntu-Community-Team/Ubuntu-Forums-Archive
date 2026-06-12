---
title: "Mouse and Internet problems"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by abuntoyoutoo on 2007-02-02
I've recently (about an hour ago:) ) installed 6.10 ubuntu onto my computer. Most of it worked straight away, and most of the problems that occurred I could fix. There was two problems that have me stuck though.

1. How do you configure the buttons on the mouse? My mouse has back and forward buttons but they aren't working. Also, it has two buttons next to the scroll wheel that also allow scrolling. However, when these buttons are pressed, sometimes it also acts as a left click and starts selecting text or opening links.

2. Most internet sites are working, but gmail isn't. Also, gaim couldn't connect to my msn hotmail account. This seams like a firewall problem, but I don't even know if I have a firewall :p

Other than that, its been working perfectly. Ubuntu rocks :guitar:

---

### Post by Scarlett on 2007-02-02
I've also been wanting a fix for those mouse buttons.  I've got 6 of them but only two work.

In Firefox, I found an extension that worked with the middle click and pulled up a small Thingie where you could click forward, backward, open new tab, open bookmarked pages and run applications.  It was a pretty decent work-around and I really wish I could remember the name of it.  I had to reinstall everything so I can't really check on it, but if you go about halfway through the miscellaneous section on the FF site you'll find it.  

(Yeah, I'm sorry, that wasn't really helpful.)

---

### Post by jolarson on 2007-02-02
I also have been trying to work out these two problems.  though for me I am at a college, so there are proxy settings for connecting to gmail.  since other things also sometimes don't like to work.

---

### Post by klytu on 2007-02-02
> **abuntoyoutoo said:**
> 
 
1. How do you configure the buttons on the mouse? My mouse has back and forward buttons but they aren't working. Also, it has two buttons next to the scroll wheel that also allow scrolling. However, when these buttons are pressed, sometimes it also acts as a left click and starts selecting text or opening links.
 
Other than that, its been working perfectly. Ubuntu rocks :guitar:
 
If you haven't done so already, try a search of the forums for your specific make and model of mouse. If it's a Logitech mouse, check out the info [**[COLOR=red]here[/COLOR]**]("http://www.ubuntuforums.org/showthread.php?t=219894"). The info on the Logitech mice is for Ubuntu 6.06, but it should be useful for 6.10 as well. 
 
You might also find [**[COLOR=red]this[/COLOR]**]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Mice") is helpful.

---

### Post by abuntoyoutoo on 2007-02-03
> If you haven't done so already, try a search of the forums for your specific make and model of mouse. If it's a Logitech mouse, check out the info here.
Thanks for that link, it helped to get my mouse mostly working. I also found [[COLOR="Blue"]**this**[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=332256&highlight=logitech") useful.

I'm still having problems with my internet though. It is strange how 90% of sites work, but a couple rare ones like gmail and [http://help.ubuntu.com/](http://help.ubuntu.com/) don't. Also, the dictionary program never connects to the server.  It reports an error "Connection failed to the dictionary server at dict.org:2628" every time.

I am connected through a router which is shared with another computer running windows xp. That computer can access all the sites properly.

I really have no idea how to to fix this problem. Is there a program like ipconfig in ubuntu? I would really appreciate the help with this as I've hit a dead end with this problem.

Edit: addons.mozilla.org also doesn't work. I'm not sure if this helps but there must be some connection between all the sites that don't work

---

### Post by klytu on 2007-02-05
> **abuntoyoutoo said:**
> Thanks for that link, it helped to get my mouse mostly working. I also found [[COLOR="Blue"]**this**[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=332256&highlight=logitech") useful.

I'm still having problems with my internet though. It is strange how 90% of sites work, but a couple rare ones like gmail and [http://help.ubuntu.com/](http://help.ubuntu.com/) don't. Also, the dictionary program never connects to the server.  It reports an error "Connection failed to the dictionary server at dict.org:2628" every time.

I am connected through a router which is shared with another computer running windows xp. That computer can access all the sites properly.

I really have no idea how to to fix this problem. Is there a program like ipconfig in ubuntu? I would really appreciate the help with this as I've hit a dead end with this problem.

Edit: addons.mozilla.org also doesn't work. I'm not sure if this helps but there must be some connection between all the sites that don't work

You can try: ```
gnome-nettool
``` to get some information. Do you have firestarter or some kind of firewall running in Ubuntu? If so, check the settings there as well. I have a set-up similar to yours, connecting through a router which is shared with another computer running WindowsXP. I don't run a firewall in Ubuntu so I am not familiar with using it. My router itself is set-up to block certain ports, but I have no problems with any of the sites you mention on either computer.

---

