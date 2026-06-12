---
title: "audacity - recording from speakers output"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by MolotovHearts on 2007-10-27
I've seen this in a few threads but still can't work it out. 

What I'm trying to do is record the output of my speakers in audacity so I can then cut it up and use it for samples as well as, record drum beats I made in hydrogen as they are played through my speakers so i can use them as samples as well.

I use audacity on windows as well and it has worked well for that, but on the version I have on linux, the dropdown menu at the top-right isn't there so I can't choose between the input devices.

Another thing, I can't play audacity and have another program playing at the same time. Can I change that too?

Any help would be great.

If there are any other programs anyone could suggest would be better for what I'm trying to do, that would be great as well.

---

### Post by 5-HT on 2007-10-28
Ardour and JACK will make make your life so much easier. :)
You're really trying to record from your speaker output?? Ouch: just route the transport in JACK and you'll notice a world of difference.
cheers,

---

### Post by MolotovHearts on 2007-10-28
Thanks.

I installed ardour-gtk from Synaptic but when I open it I get a window saying that JACK isn't working.

So I open JACK and press start, but I end up with: 

Could not connect to JACK server as client.


I've posted about this in a thread a few hours ago:
[http://ubuntuforums.org/showthread.php?t=574348]("http://ubuntuforums.org/showthread.php?t=574348")

---

### Post by argie on 2007-10-28
I wanted to give this a try some time ago. I forgot which I set to input, but I think I had something like Line Out. Setting that to record, and increasing the volume allowed me to record what was playing. However, quality tends to degrade. Just make sure both volume sliders aren't zero, I didn't notice that and kept worrying about how to get it to work.

Also, you need to have a duplex sound card or something. I forget, but I saw it on the wiki pages I searched then.

---

### Post by MolotovHearts on 2007-10-29
Thanks.

I somehow got it to work, through OSS. Problem is that it records with way too much feedback and is a bit too loud.

---

### Post by philinux on 2007-10-31
[http://ubuntuforums.org/showthread.php?p=3678931#post3678931](http://ubuntuforums.org/showthread.php?p=3678931#post3678931)

---

