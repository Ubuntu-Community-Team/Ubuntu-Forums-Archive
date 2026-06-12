---
title: "Perfect Ubuntu 7.04"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by Brendan Hart on 2008-02-21
Back when 7.04 came out I seen a guide to installing perfect ubuntu, though ive seen one on how to forge it still doesnt work perfect, like menus for movies dont work, some movies dont work at all, java games still crash the browser, and its not really the perfect desktop.

The guide I'm thinking off explains the issues and shows you how to fix them before you have the problems.  It was this person comparing to Fedora, not sure where it is now... :(

---

### Post by jan quark on 2008-02-21
[http://www.howtoforge.org/the_perfect_desktop_ubuntu_gutsy_gibbon](http://www.howtoforge.org/the_perfect_desktop_ubuntu_gutsy_gibbon)

this perhaps

---

### Post by jan quark on 2008-02-21
ops and here for 7.04
[http://www.howtoforge.org/the_perfect_desktop_ubuntu7.04](http://www.howtoforge.org/the_perfect_desktop_ubuntu7.04)

---

### Post by Brendan Hart on 2008-02-21
those ones ive already seen, the one im looking into was made by some guy who was testing it whether it was better than Fedora, and he did all this stuff to get programs working, like DVD's for example, the perfect desktop installation doesnt play dvd's properly I have to do mediubuntu and then do some libdvdcss junk etc, u know because you've probably done it, then he does all the other stuff to get some cool desktop effects that I would love!

---

### Post by jan quark on 2008-02-21
perhaps it is better you tell us what you want to install than searching for one guide to no avail ?

we can help you set up the 3d desktop effects
or whatever you want to have...

---

### Post by Brendan Hart on 2008-02-21
Okiedokies, thanx, Can you help me install Flash? so I can watch youtube vids for example and other flash websites etc

---

### Post by jan quark on 2008-02-21
first use this method

```
sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```

just run this in terminal
should work 

if not

remove it with
```
]sudo apt-get remove --purge flashplugin-nonfree -y
```

and use this guide


[http://laiconic.quotaless.com/tutorial3.html](http://laiconic.quotaless.com/tutorial3.html)

---

### Post by northern lights on 2008-02-21
flashplugin-nonfree should solve your flash problem (make that precious YouTube work...)

You were complaining earlier about movies and the like - if you're concerned about more than flash, I'd recommend installing "ubuntu-restricted-extras" (I think that even includes flash also, not sure). It's available in Synaptic or simply run ```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Brendan Hart on 2008-02-21
Ok that didnt give me any help even the tutorial3.html, I am using amd64 am I still able to install flash plugins it said some where I couldnt, [https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

### Post by Brendan Hart on 2008-02-21
> **northern lights said:**
> flashplugin-nonfree should solve your flash problem (make that precious YouTube work...)

You were complaining earlier about movies and the like - if you're concerned about more than flash, I'd recommend installing "ubuntu-restricted-extras" (I think that even includes flash also, not sure). It's available in Synaptic or simply run ```
sudo apt-get install ubuntu-restricted-extras
```

Its not my "precious youtube", its just me trying to get this OS to work better than Windows XP, If you dont think having flash run on any website an issue and running movies a big thing then your stupid.  Because most people like to watch movies on their computers, especially me because it saves me having to buy a tv because my Monitor is way Bigger then my current tv, and when i used windows I was able to watch tv play movies watch youtube. 

So you need to get this out of your head and your attitude needs to be fixed a little bit.  Now that uve read this you can get back to your "precious" life.

btw ive got restricted extras, one of the first things I did and that plays movies yes but still not all movies and cuts out in between movies with errors

---

### Post by zabien1970 on 2008-02-21
Uh, he didn't say 'you're' precious youtube, he said 'that' precious youtube, run the command he gave you then try youtube and movies again and see if they work

---

### Post by northern lights on 2008-02-21
Jesus Murphy!

Brendan - I'm sorry if I've hurt your feelings. Flash is important for a load of web content. And even if you wanted it only for YouTube (which I didn't mean to say) that'd be fine with me. Heck I certainly use YouTube too - there might be a lot of crap on that site, but there sure enough is a fair amount of watchable content also.

Movies I never even disputed at all - rather I gave you a hint on what could improve 'em.
You knew about restricted-extras before? Fair enough, ignore my post.

Now that I've made you feel better, you might wanna revise your own words a bit?!

Anyways, for the sake of furthering your progress - what formats does your comp not play or have difficulties with? What player do you use? Have you tried VLC?

---

