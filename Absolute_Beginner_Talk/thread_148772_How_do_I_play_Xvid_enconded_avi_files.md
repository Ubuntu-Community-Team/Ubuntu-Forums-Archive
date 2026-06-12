---
title: "How do I play Xvid enconded avi files?"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by jimjames on 2006-03-22
Hello there

Ok firstly, I have no idea how to use command lines and Ive only just started using the 'Synaptic Packet Manager' to no great effect

I tried using totem but when I started it up it displayed a message saying

"Totem could not startup"

"Failed to create a Gstreamer play object. Please check your gstreamer installation"

I did a bit of reading about the 'Synaptic Packet Manager' and Restricted Formats'

(read some of this page [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats))

And despite downloading a gstreamer-totem thing not much has happened.

Im rather confused and some explanations and a few pointers to some truely new born baby documents would help alot.

Were any of you made to play sports at school in the biting cold? And when you got back to the changing rooms you couldnt tie your shoes up despite being perfectly capable? Thats a tiny bit how i feel right now.

Thanks for any help!

Jim

Update -

I've read this page;

[https://wiki.ubuntu.com/MultimediaApplications](https://wiki.ubuntu.com/MultimediaApplications) 

installed totem-xine and I can now play my video! hoorah. But no sound. Boo.

How might I go about fixing the missing sound? I know sound is working generally because ubuntu is making its bird noise's and dungs at me.

---

### Post by taurus on 2006-03-22
Try using Automatix and install the codecs, w32codecs!!!  Then, use either mplayer or xine to play your avi movie...

---

### Post by jimjames on 2006-03-22
Hi

Will Automatix do the same job as the Synaptic Package Manager?

Or can I only get the w32codec from Automatix? I tried searching for w32codec in the synaptic package manager and found nothing...

Thanks for your help

---

### Post by taurus on 2006-03-22
Automatix contains some add-ons that you can't find with either synaptic or apt-get.  So, if you can't find something with synaptic, look for it in Automaix and I am sure you can find almost anything, including a kitchen sink!  :mrgreen:

---

### Post by OffHand on 2006-03-22
sudo apt-get install w32codecs

To enable restricted formats go to synaptic>settings>repositories. click settings again and enable 'show disabled software resources'

---

### Post by jimjames on 2006-03-22
Ok so

totem-xine installed

w32codecs installed (definatelly - ive checked with a friend)

But still no sound!

Maybe i should try mplayer?

Or is there some other codec i may need? I know in windows its sometimes neccesairy to have the ac3 filter for sound.

---

### Post by OffHand on 2006-03-22
Install these codecs: [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

---

### Post by gabruo on 2006-03-22
Try Mplayer it supports AC3 too, but make sure you check you repositories if it doesn't show up on the search in synaptic it is unsupported I believe.

---

### Post by YuHoo on 2006-03-22
I'm not insulting your intelligence, but I had a similar problem with gxine and found that the auto detection of audio channels is sometimes hit-or-miss. The specific correction to your problem I am not sure of, however this could perhaps be the issue.

---

