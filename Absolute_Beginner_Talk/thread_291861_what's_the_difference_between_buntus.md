---
title: "what's the difference between *buntus?"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by insub2 on 2006-11-03
I don't like brown.  But I love ubuntu.  So i was considering using a *buntu variation for superficial reasons.  but i don't want to be limited.

edubuntu is top choice 'cause it uses GNOME.  aside from logo and that it comes with educational packages (which i'll probably remove) is there any limitations?  ...anything i can't do in edubuntu that i can do in ubuntu?

xubuntu's colors and logo look better to me than edubuntu and i am kinda curious to the Xfce desktop enviroment looks pretty good, too.  One thing i like a lot about gnome is how easy it is to update the look of it using [art.gnome.org]("http://art.gnome.org/").  is there something comparable in Xfce?  also is there anything i can't do with xubuntu that i can do with ubuntu?  I figured I could install xubuntu and if I wanted GNOME, i could install it.  How would that effect the load screen and such?


p.s.
i should mention i am going to to a fresh install regardless of what i end up going with (including ubuntu).

---

### Post by Sef on 2006-11-03
Ubuntu and Kubuntu are both full desktops for computers with at least 256 ram.  Ubuntu uses Gnome and Kubuntu uses KDE.  Xubuntu is a lightweight desktop for older machines that have less than 256 ram.  Edubuntu is made for schools; hence all the packages for networking and thin clients.  

Note for nonNorthAmerican English Speakers: In North American English, school goes from nursery school (pre-kindergarten) through university.)

---

### Post by seshomaru samma on 2006-11-03
> **insub2 said:**
> I don't like brown.  But I love ubuntu.  So i was considering using a *buntu variation for superficial reasons.  but i don't want to be limited.

edubuntu is top choice 'cause it uses GNOME.  aside from logo and that it comes with educational packages (which i'll probably remove) is there any limitations?  ...anything i can't do in edubuntu that i can do in ubuntu?

xubuntu's colors and logo look better to me than edubuntu and i am kinda curious to the Xfce desktop enviroment looks pretty good, too.  One thing i like a lot about gnome is how easy it is to update the look of it using [art.gnome.org]("http://art.gnome.org/").  is there something comparable in Xfce?  also is there anything i can't do with xubuntu that i can do with ubuntu?  I figured I could install xubuntu and if I wanted GNOME, i could install it.  How would that effect the load screen and such?


If you want to try XFCE just install it like this:
```
sudo aptitude install xubuntu-desktop
```

Then log out and choose XFCE from the session options in the GDM screen.
My experience is that if you tweaked the machine to your liking with Gnome than using XFCE is a good fast option. But if you install XFCE first (=Xubuntu) then it's quite difficult to do certain things. For example to connect to a Windows box. In Gnome I can do it with a few clicks of the mouse but in Xubuntu you need some terminal work. 
Changing themes in and appearance in Gnome is much easier and there are more options to choose from.
As far as I know , Edubuntu is Gnome with a few extra packages. There is nothing you can do with Gnome that you can't do with Edubuntu.

---

### Post by K.Mandla on 2006-11-03
Not to be snotty, but why not just change the colors? If you love Ubuntu and your computer can handle it, a facelift seems like the obvious idea.

---

### Post by NeoLithium on 2006-11-03
Definitely; it's actually easier just for convenience  to change the colors, than remove a bunch of applications you don't want.  I myself don't like the brown color either; but you might be surprised how easy it is to get rid of anything like that, and make a nice custom look with virtually any preferred color... :)

---

### Post by insub2 on 2006-11-03
> **K.Mandla said:**
> Not to be snotty, but why not just change the colors? If you love Ubuntu and your computer can handle it, a facelift seems like the obvious idea.

Actually, I have already changed the colors.  I don't suppose many will agree with me on this, but I don't like the brown Ubuntu logo on start up and am willing to do a little extra work to get rid of it.  If you know of a way to change the logo and text color and all that on the first screen, please share.  But I am going to do fresh install for Eft anyway and I figured I might as well try something new.  I just played around with Xfce and that looks pretty and I like it (aside from the programs freezing and the panels disappearing which I guess has something to do with running GNOME too).

What I want to know is what is the difference between the *buntu distros and how that effects funtionality...the programs I can run.  I mostly use firefox, gaim, inkscape, the gimp, gedit, xsane, tvtime, k3b, and a few others.

---

### Post by monkeydust on 2006-11-03
> **insub2 said:**
> Actually, I have already changed the colors.  I don't suppose many will agree with me on this, but I don't like the brown Ubuntu logo on start up and am willing to do a little extra work to get rid of it.

Nope, I totally agree. I quickly got tired of the brown, and now have a blue wallpaper, blue start up splash, blue GDM log in menu and a custom BOOT splash. It's a matter of taste, seems 50% love the brown, seem 50% want to go with something else. The point of Linux is you can customise!

> If you know of a way to change the logo and text color and all that on the first screen, please share. 

While you you are still using Dapper you can use any 640x480, 16 colour image you want, using the following tutorial:

[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

Personally, I'm using Usplash Minimal, which is Orange, rather than brown, and has none of the words flying past at the bottom. Just looks a lot neater (to me).

The details for usplash minimal are here:

[http://ubuntuforums.org/showpost.php?p=1013184&postcount=13](http://ubuntuforums.org/showpost.php?p=1013184&postcount=13)

And it looks like this:

[http://www.ffnn.nl/media/external/ubuntu/usplash/minimalistic-working-full.jpg](http://www.ffnn.nl/media/external/ubuntu/usplash/minimalistic-working-full.jpg)

> But I am going to do fresh install for Eft anyway and I figured I might as well try something new. 

Eft has a new boot-up system and I'm not sure how it configures. Aparently it's a bit more straightforward to customise, but I haven't played with it myself yet. The stories about Eft being awful to upgrade has put me off.

> What I want to know is what is the difference between the *buntu distros and how that effects funtionality...the programs I can run.  I mostly use firefox, gaim, inkscape, the gimp, gedit, xsane, tvtime, k3b, and a few others.

Shouldn't affect any of those programmes. If the Distro you use doesn't have it pre-installed, it should just be a case of using apt-get or Synaptic to pull it in.

Maybe inaccurate on a few points (I'm new too), so please correct me where wrong.

David

---

### Post by insub2 on 2006-11-03
thank you monkeydust!!!


Has anybody who uses/used Xubuntu care to post???

---

### Post by dangermouse28 on 2006-11-20
I've tried the USplashCustomizationHowto but it just doesn't work - I'm stuck with brown 'n orange boot up screen!

---

### Post by Gaweph on 2006-11-20
I think the current (edgy) boot up screen looks very nice

Its pretty muich black, with the cool new shiny logo, and a little orange progress bar.  

It is nt that bad is it?

---

### Post by Bartender on 2006-11-20
I tried Xubuntu last week and thought the standard blue desktop was pleasant.  They left out some of the geegaws that you might take for granted.  Such as dragging and dropping icons to the desktop, automated modem dialer, etc.  With a little work you can add some of these things back in again.  But it seems to me that at some point you're just tying extra baggage onto an OS that wants to run free if you know what I mean.
  
My Linux PC (sig) has enuf RAM but the processor is slow.  Xubuntu was noticeably more responsive than GNOME or KDE when mousing around and apps seemed to load about 20 to 40% faster.

Automatix works with Xubuntu.  My guess is a person would want to add some things to the basic install, but if you've got a slower PC make smart choices.  For instance, F-Spot would probly be a better choice than Picasa.

---

