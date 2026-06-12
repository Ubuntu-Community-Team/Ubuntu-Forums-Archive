---
title: "Update Warning"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by ramjet_1953 on 2006-11-28
Hi, Guys!

I got this warning from Synaptic package manager and am not sure what to do about it. 

I decided to ask the forum, as I don't want to break anything.
 See attached screenshot.

Regards,
Roger :-k

---

### Post by taurus on 2006-11-28
What happens if you run these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by ramjet_1953 on 2006-11-28
Before I do that, what worries me is that it's talking about a distribution update.
I'm worried that it might try to update me to Edgy, which I don't want at this time, as I'm perfectly happy with Dapper.

Regards,
Roger :cool:

---

### Post by taurus on 2006-11-28
It will not upgrade you from Dapper to Edgy unless

1.  You modify your /etc/apt/sources.list and change all the dapper to edgy.
2.  You run "sudo aptitude dist-upgrade".

---

### Post by ramjet_1953 on 2006-11-28
I did a bit more fiddling and this is another screen capture from Synaptic.
It appears like I have some sort of a problem with authentication, as it is referring to a key.

Roger :-k

---

### Post by syrleb on 2006-11-28
it wont upgrade to edgy, sorry i cant help you but where did you get your theme? its mad

---

### Post by bodycoach2 on 2006-11-28
Here, here!
I want those icons! Where'd you get them?

> **ramjet_1953 said:**
> Hi, Guys!

I got this warning from Synaptic package manager and am not sure what to do about it. 

I decided to ask the forum, as I don't want to break anything.
 See attached screenshot.

Regards,
Roger :-k

---

### Post by ramjet_1953 on 2006-11-28
Hi, Syrleb!

I'm a "Baby Boomer" and there used to be a very tongue-in-cheek cartoon on TV called Roger Ramjet.
I have had the nick-name of Ramjet since early high school.

Roger :cool:

---

### Post by syrleb on 2006-11-28
haha, ok    that still doesnt tell me where you got your theme

---

### Post by ramjet_1953 on 2006-11-28
Hi, Syrleb!

If you want the Aston Martin picture just go to the Aston Martin website and have a look in the DB9 gallery. I just used GIMP to add the Ubuntu logo.

Roger:cool:

---

### Post by syrleb on 2006-11-28
thanks, but how did you get your icons looking like that?

---

### Post by ramjet_1953 on 2006-11-28
The theme is Nuvola Blue Style Surf.

Roger:cool:

---

### Post by syrleb on 2006-11-28
ok thanks, ill try and get it, ive never experimented with themes so i dont really know what im doing, any advice?

---

### Post by ramjet_1953 on 2006-11-28
Dead easy!

Download the theme, then go to System>Preferences>Theme.
Click on the Install Theme button and tell it where you dowloaded the theme to.
Then just click on it and Viola, you have it!

Roger :cool:

---

### Post by syrleb on 2006-11-28
thanks mate, and sorry to bother ya again, but do you have any particular sites where i can download themes?

---

### Post by nickburns on 2006-11-28
sudo apt-get install gnome-themes-extras


then System >> Preferences >> Themes

---

### Post by ramjet_1953 on 2006-11-28
Try [http://www.gnome-look.org/](http://www.gnome-look.org/)

Roger :cool:

---

### Post by ramjet_1953 on 2006-11-29
Bump

I'd like to get back to the problem in hand.
Does anyone know how to fix this signing key issue?

Roger:rolleyes:

---

