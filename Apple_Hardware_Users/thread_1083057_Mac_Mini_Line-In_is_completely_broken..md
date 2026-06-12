---
title: "Mac Mini Line-In is completely broken."
date: 2009-02-28
forum: Apple Hardware Users
---

### Post by film42 on 2009-02-28
So here's the deal. I set my MacBooks (running leopard) headphone jack to input into my Mac Mini's Line-In (running ubuntu 8.10), it then 'should' output to the speakers that our plugged in to the Mac Mini. And yes I enabled the Line-In to Output swap. The whole point is to run sound from my MacBook into my Mac Mini, so they both can share the speakers.

When I run a capture test with "HDA Intel (Alsa mixer)" it gives the error:

```
Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'
```

and here's a [Screenshot]("http://codingrockets.com/stuff/screenshot/1235850550.png")

I tried using Sound Recorder (Playing music on my MacBook in full volume), but that too blows up.

I've been researching all day and have yet to find a solution. If someone has had this problem, or knows of a possible solution PLEASE empty your brain here.

Thanks again,

film42

---

