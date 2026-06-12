---
title: "I broke something already"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by T4K3Z0U on 2007-09-08
I was trying to install a media player to work with wma. I think it was exaile. Well exaile does nothing when I try open it so I found another advice on a wma player which needed me to go into add/remove area. When I clicked on the add/remove button, I got this message.

[IMG]http://i33.photobucket.com/albums/d51/kiwi_samurai/Screenshot-gnome-app-install.png[/IMG]

What does it mean and how do I fix it?

I'm sick of going into windows just to use a media player.

---

### Post by alienexplorers on 2007-09-08
Get into terminal and type:
> sudo apt-get update
sudo apt-get install -f

---

### Post by overdrank on 2007-09-08
> **T4K3Z0U said:**
> I was trying to install a media player to work with wma. I think it was exaile. Well exaile does nothing when I try open it so I found another advice on a wma player which needed me to go into add/remove area. When I clicked on the add/remove button, I got this message.

[IMG]http://i33.photobucket.com/albums/d51/kiwi_samurai/Screenshot-gnome-app-install.png[/IMG]

What does it mean and how do I fix it?

I'm sick of going into windows just to use a media player.

Hi I would suggest going to the terminal and using the commands given in the error
```
sudo apt-get update 
```
the terminal is located under applications, accessories, terminal and post back here if any errors.

EDIT too slow

---

### Post by ORBiTrus on 2007-09-08
> **T4K3Z0U said:**
> I was trying to install a media player to work with wma. I think it was exaile. Well exaile does nothing when I try open it so I found another advice on a wma player which needed me to go into add/remove area. When I clicked on the add/remove button, I got this message.


Not that this is relevant, but Exaile is based off of Quod Libet.  So is Listen.  All of them use the gstreamer framework, so if you can play in Exaile, you should be able to play in Rhythmbox et al.

---

### Post by T4K3Z0U on 2007-09-08
> **overdrank said:**
> Hi I would suggest going to the terminal and using the commands given in the error
```
sudo apt-get update 
```
the terminal is located under applications, accessories, terminal and post back here if any errors.

EDIT too slow

LOL I'm a jackbutt, didn't even see the fix it code there. :oops:

---

### Post by T4K3Z0U on 2007-09-08
> **ORBiTrus said:**
> Not that this is relevant, but Exaile is based off of Quod Libet.  So is Listen.  All of them use the gstreamer framework, so if you can play in Exaile, you should be able to play in Rhythmbox et al.

exaile doesn't deem to work. Rythmbox just won't play wma files. 

could anybody give me code for a player that does work?

---

### Post by avik on 2007-09-08
> could anybody give me code for a player that does work?

Use VLC or mplayer:

```
sudo apt-get install vlc
```

or

```
sudo apt-get install gmplayer
```

I think you might need the restricted codecs.  I forget what they are, but someone else should be able to point you in the right direction.

---

### Post by overdrank on 2007-09-08
> **avik said:**
> 

I think you might need the restricted codecs.  I forget what they are, but someone else should be able to point you in the right direction.

These links will help with the formats
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)

---

### Post by lisati on 2007-09-08
> **T4K3Z0U said:**
> LOL I'm a jackbutt, didn't even see the fix it code there. :oops:

The "fixit codes" are the parts beginning with "sudo". You have to use "terminal" from the "Applications"->"Terminal" message.

---

### Post by T4K3Z0U on 2007-09-08
> **avik said:**
> Use VLC or mplayer:

```
sudo apt-get install vlc
```

or

```
sudo apt-get install gmplayer
```

I think you might need the restricted codecs.  I forget what they are, but someone else should be able to point you in the right direction.

Terminal said it couldn't find gmplayer.
I installed vlc but no sound from pc

---

### Post by rsambuca on 2007-09-08
sudo apt-get install ubuntu-restricted-extras

This will install what you need.

---

### Post by T4K3Z0U on 2007-09-08
> **rsambuca said:**
> sudo apt-get install ubuntu-restricted-extras

This will install what you need.

Ok I just got this screen and don't know what to do with it.
[IMG]http://i33.photobucket.com/albums/d51/kiwi_samurai/Screenshot-t4k3z0uTAKEZOU-7.png[/IMG]

Um and what was that supposed to install? 
Using VLC there is no sound. Is that normal?

---

### Post by ORBiTrus on 2007-09-08
Hit tab to select the "OK" and hit enter.

restricted-codecs will install some stuff that's either illegal in the states, or non-free.  One of those things is a WMA codec for gstreamer, which, as I said, is what those programs use.

Of course, if this WMA file is DRMed, you won't be able to play it {at all, without a lot of work}.

VLC without sound can be normal.  VLC is a powerfull little app that sometimes needs a little setup.  It's possible, again, that VLC isn't playing sound because the file is DRMed.  If VLC plays another file, that *might* be it, if VLC doesn't, well...

Remember: if a file ends in WMA, that's just the manufacturer trying to tell you that he only wants you to be able to play it on Windows.  Unfortunately, many people seem to think that because there are many of these files Linux should play them, but that's not the case; often if the manufacturer wants to force people to use Windows because it saves them 0.01 cents on the dollar, they do.

P.S. Your terminology in the subject line is unsound.  While if you did break something, I would congratulate you on taking responsibility, in this case something broke.  It doesn't mean you did anything.  So, if you have a personality that takes responsibility for things like this, you don't have to - that type of personality is not good to have anyways; people with it are easy to walk over.

---

### Post by T4K3Z0U on 2007-09-08
> **ORBiTrus said:**
> Hit tab to select the "OK" and hit enter.

restricted-codecs will install some stuff that's either illegal in the states, or non-free.  One of those things is a WMA codec for gstreamer, which, as I said, is what those programs use.

Of course, if this WMA file is DRMed, you won't be able to play it {at all, without a lot of work}.

VLC without sound can be normal.  VLC is a powerfull little app that sometimes needs a little setup.  It's possible, again, that VLC isn't playing sound because the file is DRMed.  If VLC plays another file, that *might* be it, if VLC doesn't, well...

Remember: if a file ends in WMA, that's just the manufacturer trying to tell you that he only wants you to be able to play it on Windows.  Unfortunately, many people seem to think that because there are many of these files Linux should play them, but that's not the case; often if the manufacturer wants to force people to use Windows because it saves them 0.01 cents on the dollar, they do.

P.S. Your terminology in the subject line is unsound.  While if you did break something, I would congratulate you on taking responsibility, in this case something broke.  It doesn't mean you did anything.  So, if you have a personality that takes responsibility for things like this, you don't have to - that type of personality is not good to have anyways; people with it are easy to walk over.

Ok VLC worked fine after I rebooted. Is there a way I could import all my music into it rather than having to open each song individually?

---

### Post by ORBiTrus on 2007-09-08
View -> Playlists

That's the best you'll get with VLC.  It's a media player, not a media organizer... in other words, don't give up on Exaile et al.  They really are a much better user experience once they have all the codecs they need.

But if you want to use VLC because "it works" that's fine too.

---

### Post by T4K3Z0U on 2007-09-08
> **ORBiTrus said:**
> View -> Playlists

That's the best you'll get with VLC.  It's a media player, not a media organizer... in other words, don't give up on Exaile et al.  They really are a much better user experience once they have all the codecs they need.

But if you want to use VLC because "it works" that's fine too.

Is there a software for ubuntu that will change wma files into a supported format?

---

### Post by runemaste644 on 2007-09-08
Go to Synaptic (System>>Administration>>Synaptic Package Manager) or run```
sudo synaptic
```
You must have your password. Click on "Broken" and see if you have any broken packages. It happened to me before so im sure this will work.

---

### Post by T4K3Z0U on 2007-09-08
> **runemaste644 said:**
> Go to Synaptic (System>>Administration>>Synaptic Package Manager) or run```
sudo synaptic
```
You must have your password. Click on "Broken" and see if you have any broken packages. It happened to me before so im sure this will work.

I just got this message when trying to run synaptics.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried the manual run but nothing happened. the screen just disappeared once I hit run.

---

### Post by runemaste644 on 2007-09-08
What do you mean the screen disappeared?

Remember, dpkg-reconfigure is dangerous. It could have permanetly messed up my internet on Ubuntu.

Were you really trying to run Synaptic when you got the message or was it Add/remove?

Try Synaptic again.

---

### Post by T4K3Z0U on 2007-09-08
> **runemaste644 said:**
> What do you mean the screen disappeared?

Remember, dpkg-reconfigure is dangerous. It could have permanetly messed up my internet on Ubuntu.

Were you really trying to run Synaptic when you got the message or was it Add/remove?

Try Synaptic again.

i mean nothing happened. The run screen disappeared. 
I was opening synaptic.
It is fixed now.

---

### Post by runemaste644 on 2007-09-08
Ok. I was actually thinking of using a Terminal window, but Alt+F2 works too. Its just i can see any errors if i run it in Terminal

---

