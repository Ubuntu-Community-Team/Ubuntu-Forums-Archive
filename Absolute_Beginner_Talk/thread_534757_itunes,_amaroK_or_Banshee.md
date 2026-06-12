---
title: "itunes, amaroK or Banshee?"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-08-25
I read through this thread just now...
[http://ubuntuforums.org/showthread.php?t=211883](http://ubuntuforums.org/showthread.php?t=211883)


Since I don't have an iPod and I was using iTunes on Windows to purchase and play complete CDs, my question is this:  Does amaroK or Banshee have a store where I can purchase new CDs for about $10 like iTunes does?  That is really the only thing I used iTunes for.  I had a Napster account for a short while, but on top of the $10 CD purchase price, they charged a $14/month membership fee.  So I started using the iTunes store and really liked it.  I never had a problem with the interface so I played music with it as well and it always worked good.

What does Ubuntu offer that is comparable?

---

### Post by GMachine_24 on 2007-08-25
Hi:

I don't think amarok of banshee offer download music stores. However, I'm pretty sure you can buy music from emusic.com which is the best source for downloadable music anyway unless you like excessive restrictions and other corporate bull****.

Check them out if you want. They offer a free trial program and then songs are like 30-35 cents each depending on how many you sign up for. The music is YOURS and you can burn it to a CD, copy it to your MP3 player, whatever.

It's not perfect; but it's not classic rock crap, either.

I just read where Rhapsody is teaming with some other music download source and will come out with 'Rhapsody America' soon - whether this is compatible with Linux I do not know. You can listen to Rhapsody via Firefox on Linux but you cannot buy / download music.

gm

---

### Post by aysiu on 2007-08-25
AmaroK and Rhythmbox have integration with Magnatune and Jamendo, respectively. Magnatune is a store with independent music. Jamendo is cost-free (but legal... and mostly French) music.

If you want the iTunes music store, dual boot or just use Windows or Mac.

---

### Post by kc5hwb on 2007-08-25
I tried emusic.com already and stopped using them because their selection sucked.  They had almost none of the music that I was looking for at the time.  I listen to some diverse music, but all of it is available on iTunes.

I installed both Banshee and Songbird just now and neither of them will play the mp3s that I have on my harddrive.  Songbird just says "error" and Banshee says "error, no codec"  I've never   installed a codec before because I just played them with VLC and of course it doesn't need codecs.  So where can I get codecs for these?

BTW... Songbird does have some store entries to buy music.  I might check those out.

I have XP installed through Virtualbox, and iTunes running in that.  It seems to work fine, except that Vbox doesn't see my cd burner... not sure why.  It sees it as just a regular cdrom, but I can't burn anything in XP at all.

Last thing... I almost installed amaroK, but it wanted to install a TON of other packages along with it, including "kde desktop"  This won't hose up my GNOME install, will it?

---

### Post by nosrednaekim on 2007-08-25
nope, amarok won't mess up GNOME. When you are install amarok, make sure you also install "libxine-extracodecs" which provides mp3 and other codecs for the xine engine which amarok uses.

---

### Post by GMachine_24 on 2007-08-25
If you downloaded your music from Apple I believe you can only play/copy those files using Apple-approved software/hardware blah blah blah. You're probably not going to find a Linux program that works with any restricted file formats including Apple and Microsoft's DRM (digital rights management, as I'm sure you know) music protocol (used by Rhapsody, Yahoo, etc.)

gm

---

### Post by isaacj87 on 2007-08-25
If you're using GNOME, I'd use Banshee.

I have both Amarok and Banshee, and while I like Amarok a slight bit better, Banshee doesn't seem as resource hungry for Gnome users.

---

### Post by nonewmsgs on 2007-08-25
> **kc5hwb said:**
> I tried emusic.com already and stopped using them because their selection sucked.  They had almost none of the music that I was looking for at the time.  I listen to some diverse music, but all of it is available on iTunes.

I installed both Banshee and Songbird just now and neither of them will play the mp3s that I have on my harddrive.  Songbird just says "error" and Banshee says "error, no codec"  I've never   installed a codec before because I just played them with VLC and of course it doesn't need codecs.  So where can I get codecs for these?

BTW... Songbird does have some store entries to buy music.  I might check those out.

I have XP installed through Virtualbox, and iTunes running in that.  It seems to work fine, except that Vbox doesn't see my cd burner... not sure why.  It sees it as just a regular cdrom, but I can't burn anything in XP at all.

Last thing... I almost installed amaroK, but it wanted to install a TON of other packages along with it, including "kde desktop"  This won't hose up my GNOME install, will it?

for a large music collection i find my favorite is quod libet but i have heard many good things about banshee and amorak.  for the virtualbox, does your burning software give you a no cd burners found?

---

### Post by Dark Star on 2007-08-25
Amarok or Exaile ftw :D

---

### Post by akba0012 on 2007-08-26
what would be the best IPOD management program to Rip music from the IPOD itself?

I have it working with Rythmebox, but I can't figure out how to rip the files from the IPOD itself.

---

### Post by isaacj87 on 2007-08-26
Definitely Banshee....
For me, all I did was right click my iPod within Banshee and it made a Music folder in my Home folder as well as create artist and album folders too! Plus, it was all in my library waiting for me. One click did it all!

---

### Post by Dark Star on 2007-08-26
> **akba0012 said:**
> what would be the best IPOD management program to Rip music from the IPOD itself?

I have it working with Rythmebox, but I can't figure out how to rip the files from the IPOD itself.
My ipod shuffel is being managed by Exaile I just love theway it do .. So easy :)

---

### Post by akba0012 on 2007-08-26
> **isaacj87 said:**
> Definitely Banshee....
For me, all I did was right click my iPod within Banshee and it made a Music folder in my Home folder as well as create artist and album folders too! Plus, it was all in my library waiting for me. One click did it all!

What did you click? Synchronize?

---

### Post by nonewmsgs on 2007-08-26
abba - i love my gtkpod.  but you can actually just copy and paste it into the folder.

---

### Post by kc5hwb on 2007-08-26
I have Banshee and Songbird both installed, but they won't play my MP3s that I already have on my HDD.  I guess my main question is... is there a codec needed to play regular, non-DRM, MP3s?  VLC plays them fine, but Songbird and Banshee don't seem to want to.



> **nosrednaekim said:**
> nope, amarok won't mess up GNOME. When you are install amarok, make sure you also install "libxine-extracodecs" which provides mp3 and other codecs for the xine engine which amarok uses.

Audio Adreneline rocks.  Their final CD was quite good.

> **GMachine_24 said:**
> If you downloaded your music from Apple I believe you can only play/copy those files using Apple-approved software/hardware blah blah blah. You're probably not going to find a Linux program that works with any restricted file formats including Apple and Microsoft's DRM (digital rights management, as I'm sure you know) music protocol (used by Rhapsody, Yahoo, etc.)

gm

True... but iTunes will also let you burn a MP3 cd from their software, which will work on other players once it is in that format.  However, since my vbox software isn't seeing my cd burner for some reason, I am unable to do this at present.

Plus, I wouldn't mind moving away from iTunes if I can find something similar in Ubuntu.

---

### Post by S15_88 on 2007-08-26
Exaile!

---

### Post by kc5hwb on 2007-08-26
> **S15_88 said:**
> Exaile!

WTGAC is that?

---

### Post by S15_88 on 2007-08-26
[http://www.exaile.org/]("http://www.exaile.org/")

---

### Post by Dark Star on 2007-08-27
> **S15_88 said:**
> [http://www.exaile.org/]("http://www.exaile.org/")
```
sudo apt-get install exaile
``` Its a media played based on Amarok for more info check this out :) [Exaile:The best Media player![Gnome]]("http://ubuntuforums.org/showthread.php?t=525360")

---

### Post by GMachine_24 on 2007-08-27
> 

True... but iTunes will also let you burn a MP3 cd from their software, which will work on other players once it is in that format.  However, since my vbox software isn't seeing my cd burner for some reason, I am unable to do this at present.

Plus, I wouldn't mind moving away from iTunes if I can find something similar in Ubuntu.

I understand you can burn CDs from itunes songs . . . but I believe you are limited to something like making 8 copies - which, granted, is a lot - but still it's not as if you went to Amazon and bought the CD and then could pretty much do whatever you want with it. Apple's interest is in keeping a proprietary computer/software/applications/media business growing - otherwise your downloaded itunes could be freely copied, stored or whatever.

Unfortunately, there is no equivalent - at least not one I have found - the rivals the iTunes online music store. I'm sure it will come one day - perhaps from Real media because they seem more receptive to open source than other media companies. We shall see.

--gm

---

### Post by isaacj87 on 2007-08-27
> **akba0012 said:**
> What did you click? Synchronize?

No right click on the ipod in the left panel and choose import ipod

---

### Post by cookies on 2007-08-27
> **kc5hwb said:**
> I have Banshee and Songbird both installed, but they won't play my MP3s that I already have on my HDD.  I guess my main question is... is there a codec needed to play regular, non-DRM, MP3s?  VLC plays them fine, but Songbird and Banshee don't seem to want to.
...

See:
[http://www.psychocats.net/ubuntu/mp3](http://www.psychocats.net/ubuntu/mp3)

---

### Post by akba0012 on 2007-08-28
> **isaacj87 said:**
> No right click on the ipod in the left panel and choose import ipod

Shoot, everytime i try to do that it says, "Cannot import track from Ipod" "Could not find file /media/ipod/ipod_control/Music/F20/11-yesterday.mp3"

annoying! Think it has to do with the file hierarchy in the settings?

---

