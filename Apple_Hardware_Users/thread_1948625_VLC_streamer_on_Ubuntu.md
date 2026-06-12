---
title: "VLC streamer on Ubuntu"
date: 2012-03-28
forum: Apple Hardware Users
---

### Post by susja on 2012-03-28
Hello folks,
I am completely new to this VLC world. I have iPad3 and I just bought 2 days ago VLC from App store because it stated that it has beta version for Linux . I am using Ububtu 11.10 32 bit. 
Does anyone have luck to run VLC on Ubuntu ? Could you share your experience?
Next could someone point me where is download bits I should install and any step-by-step instruction how to do it?
I am familiar with Linux but again got confused with the stead related to VLC on Linux . Officially they say: betta version and not supported but it looks that some have some successes .
Appreciate any help.
Thanks in advance

---

### Post by Sylos on 2012-03-28
Hello. 

I have been using VLC media player on Ubuntu for a few years. It works fine for me. You can download it through the repos with

sudo apt-get install vlc

I hope thats what you are wanting (forgive me if I misunderstood)

Cheers

---

### Post by linuxd1 on 2012-03-28
VLC is available from Ubuntu software center.:p

---

### Post by susja on 2012-03-28
> **Sylos said:**
> Hello. 

I have been using VLC media player on Ubuntu for a few years. It works fine for me. You can download it through the repos with

sudo apt-get install vlc

I hope thats what you are wanting (forgive me if I misunderstood)

Cheers

Thanks for reply but I suggest that VLC player will play on my player but  need VLC streamer on Ubuntu. I assume that it'll stream my video and player on iPad will play it.

---

### Post by Sylos on 2012-03-28
I think from having a quick look at the VLC site that the standard player should be able to do it.

Have a look and see what you can figure out:

[http://www.videolan.org/streaming-features.html](http://www.videolan.org/streaming-features.html)

Not sure how you set it up though...

EDIT: this might help [http://www.youtube.com/watch?v=UPMr0bpxOyE](http://www.youtube.com/watch?v=UPMr0bpxOyE)

EDIT2: Been looking at the readme for the linux helper. Seems you need the latest version of VLC from another ppa along with a host of other stuff. It appears the helper sets it up for you. Best advice - try it and see what happens BUT read the forum posts related to it - some people found issues with it failing and making vlc in general fail. Good luck.

---

### Post by susja on 2012-03-30
> **Sylos said:**
> I think from having a quick look at the VLC site that the standard player should be able to do it.

Have a look and see what you can figure out:

[http://www.videolan.org/streaming-features.html](http://www.videolan.org/streaming-features.html)

Not sure how you set it up though...

EDIT: this might help [http://www.youtube.com/watch?v=UPMr0bpxOyE](http://www.youtube.com/watch?v=UPMr0bpxOyE)

EDIT2: Been looking at the readme for the linux helper. Seems you need the latest version of VLC from another ppa along with a host of other stuff. It appears the helper sets it up for you. Best advice - try it and see what happens BUT read the forum posts related to it - some people found issues with it failing and making vlc in general fail. Good luck.

Folks,
Eventually I was able to setup Helper on my Ubuntu 11.10 and now I could stream movie to iPad. I have perfect picture but I don't have sound :) . Well it's not good obviously and I asked for help from VLC dev but it looks that every time I start my PC I have to start manually Helper file. My question: where should I put this file and which system setting should I modify in order this file be executed in the background every time I start my PC?
Thanks

---

### Post by susja on 2012-03-30
Well I realized that I could just add VLCStreamerClient to 'Startup Applications ...' and it'll start when I reboot the system.
Well it looks that this program is not a service ( at least I think so ) and when it starts it's a GUI application so I can't put it to run in a background.
Well ... not very convenient ... but it looks it's the best I could do. My expectation was to run it somewhere in background but it looks I was wrong :)
the bottomline is that I have two options: either start this Streamer only when I want to stream from my PC or live with that running window ...

---

### Post by Sylos on 2012-03-31
Hello again.

Great to hear you got it running.

Below is a link that might help you with having the gui app running from boot. Im wondering if using devilspie to get the app started as a minimised window might make it a little better for you.

[http://askubuntu.com/questions/20989/how-do-i-tell-a-start-up-program-to-start-minimized](http://askubuntu.com/questions/20989/how-do-i-tell-a-start-up-program-to-start-minimized)

Cheers

---

