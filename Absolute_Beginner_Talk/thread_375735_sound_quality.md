---
title: "sound quality"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2007-03-04
Hello.
I am having a problem with the sound quality of .mov files.
In windows, they hear sweet, without any noise.
But in Ubuntu the level of noise is intolerable. ](*,) 
A file which I played in windows very fine but in ubuntu very noisily is available [here]("http://pmoutal.free.fr/aak_zilakafi.mov").

Can anyone help me?

---

### Post by pveith on 2007-03-04
Have you muted your mic-line? In some cases the an active mic-line (even if no mic is connected) can cause the static...

To check just righ click the speaker symbol in your upper panel and select "volume settings" (using a german translation here, so the actual option name might vary). You will see an array of slider with speaker symbols below, just deactivate all line-in and mic settings by clicking the corresponding speaker.  Also check settings in this application if mic is not available directly...

---

### Post by sauravbhaumik on 2007-03-04
I have muted microphone, line-in and phone. No improvement.
Is in your Ubuntu any difference between mp3 sound and mov sound (quality)?
Please try the link I gave. That is the kind of mov I am having problem with.

---

### Post by pveith on 2007-03-04
Yes i tried your link with totem and it sounded okay to me. There was some background static, which -IMHO- is due to the recording. By the way the video uses the quicktime sound system and a such it might be of lower quality than a "normal" mp3 as it compresses the movie for internet-video&audio-streaming. Does the static appear in other mp3s or movies, too? For Quicktime videos try out apples movie trailers for instance.

---

### Post by sauravbhaumik on 2007-03-04
> **pveith said:**
> Yes i tried your link with totem and it sounded okay to me. There was some background static, which -IMHO- is due to the recording. By the way the video uses the quicktime sound system and a such it might be of lower quality than a "normal" mp3 as it compresses the movie for internet-video&audio-streaming. Does the static appear in other mp3s or movies, too? For Quicktime videos try out apples movie trailers for instance.

But in windows, when I play this file in realplayer it is very smooth. In Ubuntu, mp3's and dvd movies work well but .mov files make problems.

I didn't understand what you meant by "apples movie trailers".

One thing more. My totem doesn't play mov files. What plugin is required? I plpay mov files in xine movie player and in VLC.

---

### Post by pveith on 2007-03-04
Right now i am using feisty (the still-in-development version of ubuntu). It could be that feisty fixed this issue, but ONLY use feisty if it is okay for you that it breaks from time to time. It will be released in april 2007, though... That said, it could be that i just can't reproduce your problems on my maschine...

Have you tried the linux realplayer? It is in the ubuntu-repositories. 

As for apples movie trailers. Quicktime is developed by apple and they have moviestrailers on their website. Have a look at [http://www.apple.com/trailers/](http://www.apple.com/trailers/) there are lots of mov files in different resolutions...

---

### Post by sauravbhaumik on 2007-03-04
in linux real-player, mov files do not seem to be playable.
So you are one of the person who use feisty. Would you tell me something about the new feature feisty has than edgy?

What plugin do you have so that your totem can play mov files?

---

### Post by pveith on 2007-03-04
I am using plain gstreamer totem and it just works (so i don't have a reference version. I don't have windows installed). Feisty will include updates of every major program in ubuntu, most prominently the new gnome. It will be the first ubuntu to "star" compiz and 3d-desktop effects. It includes KVM and the kernel modules to run it and as such supports virtualization much better. Have a look at the feisty specs under: [https://blueprints.launchpad.net/ubuntu/feisty](https://blueprints.launchpad.net/ubuntu/feisty) there is a more readable version somewhere, but i can't remeber where...

---

### Post by pveith on 2007-03-04
Arg, just wanted to ask if the apple trailes also produce the static described. If not this might be a problem with the specific quicktime-version the mov file is using or realplayer might turn on noise reduction... If the sound-quality is poor with the apple-trailers too, you should try mplayer or xine.

---

