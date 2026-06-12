---
title: "Hi everybody"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by Caligula on 2006-04-11
I'm just switching to Ubuntu, 
I had other problems as well so somebody else is installing it for me, but soon you're gonna need to put up with my questions...;) 

I know it's not going to be easy, it's not going to be an all-nice experience, and I come prepared.

I see this as a great oppurtunity to learn new things, widen my knowledge, and so on...

So I'm just going to wait and see, keep an open mind, and I'm sure I going to get through it better than where I started. 

And to my first question...
Does Ubuntu support Hebrew writing(I only want the ability to write in hebrew, not hebrew menus...)?
If it doesn't automatically, how do I configure it to work? Is it possible at all?

And the second -and last for now- question;
Could somebody please elaborate a bit about this ndsiwrapper fo windows drivers? because I'm using a laptop(compaq evo n115) and a wireless USB card(D-Link DWL-G122). Is there a driver for Ubuntu or do I need to Install the ndsiwrapper? or do I need to buy a whole new card?

That's all for now...
Thanks,
Josh

---

### Post by mostwanted on 2006-04-11
I've seen screenshots of Gedit in Hebrew with text going from right to left and all that jazz, so there must be a Hebrew locale setting somewhere for you to discover :)

Edit: and there was (one post down). About the wifi, you can look up hardware support on the Ubuntu wiki!

---

### Post by vxj9219 on 2006-04-11
This thread might help

[http://www.ubuntuforums.org/showthread.php?t=70794](http://www.ubuntuforums.org/showthread.php?t=70794)

---

### Post by play0r on 2006-04-11
i can easily answer your first question. if you want to write easily in hebrew i suggest getting the hebrew version of openoffice.org available here: [http://he.openoffice.org/](http://he.openoffice.org/)
or you can add hebrew support to your X configuration by replacing the following line:
        
        Option "XkbLayout" "us"
with
        Option "XkbLayout" "us,il"
        Option "XkbOptions" "grp:alt_shift_toggle,grp_led:scroll"

once you've done that restart X & viola! whenever you want to switch back to english or hebrew, just use the left_alt_shift combination. also, when you're using hebrew your scroll lock led should be on if you use this option. ;)   

as for your second question, i'm quite inept when it comes to wireless devices since i'm completely wired lol. :-#    
if your wifi doesnt work out of the box, you'll most likely have to use ndiswrapper afaik. theres plenty of documentation & howto's on how to use it i'm sure, & with any luck someone around here will help you out along the way.

good luck,
play0r

p.s.
i like your motivation for switching operating systems, just remember... learning is a journey, not a destination. :D

---

### Post by Caligula on 2006-04-11
[QUOTE=play0r]i can easily answer your first question. if you want to write easily in hebrew i suggest getting the hebrew version of openoffice.org available here: [http://he.openoffice.org/](http://he.openoffice.org/)
or you can add hebrew support to your X configuration by replacing the following line:
        
        Option "XkbLayout" "us"
with
        Option "XkbLayout" "us,il"
        Option "XkbOptions" "grp:alt_shift_toggle,grp_led:scroll"

once you've done that restart X & viola! whenever you want to switch back to english or hebrew, just use the left_alt_shift combination. also, when you're using hebrew your scroll lock led should be on if you use this option. ;)   
:D[/QUOTE]

Thanks, but I'm fairly new to Ubunto and linux in general, so basically I have no idea what you just wrote...:confused: 

Could you elaborate somehow on how to do this? is there any detailed HowTo with screenshots and everything? that would of course be the best...

Thanks everybody!

---

### Post by htinn on 2006-04-11
I suggest you read this for how to setup your wireless USB:

[http://www.ubuntuforums.org/showthread.php?t=106846](http://www.ubuntuforums.org/showthread.php?t=106846)

---

