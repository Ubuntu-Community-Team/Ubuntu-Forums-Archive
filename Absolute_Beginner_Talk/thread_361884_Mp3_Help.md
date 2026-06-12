---
title: "Mp3 Help"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by jtrimble on 2007-02-14
Greetings,

I have been using Ubuntu for a matter of hours, and this is my first time using any sort of Linux system. 

With that in mind, I have having trouble getting music to play back on Ubuntu.

I installed Ubuntu 6.06 LTS - the Dapper Drake - released in June 2006.

I get sound when I log into my system, so Im pretty sure my sound card is working. At first I thought it might me a support problem, but when I tried to play a (burned) CD in my CDrom drive, it would load it up but had no sound. I checked all the volume levels, obviously.

I just want to rock out on Ubuntu :guitar: 

Can anyone help me? I have been to a few of the websites offered to me, but either I did not install them correct or they did not work. 

Thanks!

-Josh

---

### Post by Maestro23 on 2007-02-14
Check this link on restricted formats: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by taurus on 2007-02-14
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by highneko on 2007-02-14
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by jtrimble on 2007-02-14
thank you for the help; however, it seems the problem is worse then I thought.

I downloaded an ogg vorbis song just to make sure I was getting sound, but it seems that Im not. So far, here is what makes noise:

The loggin screen

these attempts have failed in making any kind of noise:

mp3
CD
ogg

How would I begin to make sure my sound card is working correctly in Ubuntu? Thanks again, and sorry for being such a noob here! :(

---

### Post by sda5150 on 2007-02-15
Try adding the gstreamer codecs:

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base
sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad
sudo apt-get install gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly 
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse 
sudo apt-get install w32codecs

This will install the codecs for all the different formats.
you will need to have all the repositories enabled.

Try using xmms for playing sound, you can install it by doing this:

sudo apt-get install xmms

Check under <System><preferences><sound>
Make sure the default sound card is the correct card.

Let us know if your still having problems.

Sam.

---

### Post by gary_emms on 2007-02-15
If your a bit confused you could try Automatix or Easyubuntu. Try searching for each on the forum, or in google. You'll have to download them from the sites but the instructions are good and each will set up your sound and video.
Cheers

---

### Post by kinson on 2007-02-15
I'm curious because he said he has the login sound when he logs in, doesn't that mean that the sound card is working?

I understand that he probably doesn't have the mp3 codec, but he should be able to play ogg format by default right?

But just in case, I do agree with trying to install xmms to see if it can play anything.

```
sudo apt-get install xmms
```

Cheers,
Kinson

---

### Post by jtrimble on 2007-02-15
Ok, so since my last post, my sound has completly stopped working. Not even for the login. 

So... how would I go about starting to fix this? I am completly new to this whole linux scene, and I really want to use it--but I got to have sound.

I assume all the codec fixes will not work until I have sound working.

Thanks!

---

### Post by SysTech on 2007-02-15
Have you installed Amarok? 

First, I think that it installs all of the codecs. 

Second, it is by far the best app out (windows included) for playing music, hooking up your ipod, organizing play lists, ect. 

check it out: [http://amarok.kde.org/]("http://amarok.kde.org/")

To install go to your terminal and type: 
```
sudo apt-get install amarok
```

---

### Post by jtrimble on 2007-02-15
I have amarok. I had it from the start (my friend suggested it to me). 

I think the problem isn't with the codecs, but rather the soundcard itself. I am looking for fellow Linux users on campus right now, but if anyone on here might be able to point me in the right direction as to how to repair/install/get a sound card to work, that would be great.

:confused: 

I enjoy the headache that Ubuntu (or Linux really) is giving me, and I am learning alot, but I still have no sound. I cannot completely let go of windows until my sound works, as I use that more then anything else on my machine! :(

---

### Post by headphase on 2007-02-15
How do you get Amarok to play mp3s?  All I can get is ogg.

---

### Post by halitech on 2007-02-15
ok, I'm gonna ask a dumb question here. Have you double checked to make sure the speakers are plugged in and plugged in correctly? I've done it myself when moving things around so might not have anything to do with codecs or anything else. 

also, open a terminal and type
```

lspci

``` 
and then post the output here. it will tell us if ubuntu is even seeing the card

---

### Post by 3rdalbum on 2007-02-15
When you turn the volume up, make sure that you are also turning the "PCM" channel up in the full Volume Control program. On some computers, for an unknown reason, Gnome turns off the PCM channel shortly after login.

Also, check the Users And Groups panel under System > Administration > Users And Groups. Select your user account, then click Properties and "User Privileges" tab. Make sure that everything is ticked.

---

### Post by headphase on 2007-02-15
Ok, I got it.

---

