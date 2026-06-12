---
title: "How do I use TV as secondary monitor?"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Pirate King on 2008-02-19
Hello everyone,

I have a Radeon 9800Pro graphics card, and I am running Ubuntu 7.10 Gutsy Gibbon. My 9800Pro has Video-Out, but I don't know how to use the TV as a Secondary Monitor. It's a Conia (Cheapo TV), and it's not displayed in the screen list. I know it can be used as a secondary monitor as I used to use it when I had Windows. Is there a way to use my TV as a secondary monitor? If so, how? If I have to use it as a Primary Monitor I don't mind, as long as I can easily switch between them. 

I did search on the forums, but there were no replies in the threads I found. 

Thank-you everyone in advance! =)

---

### Post by DrMega on 2008-02-19
Have you installed the proprietary ATI drivers? If so then go to Synaptic, and get ati-config.

Once you've done that, go to terminal (Applications->Accessories->Terminal and run the following commands:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

The above command backs up your config file, which you will soon change. I can't remember the parameters you need to send to ati-config, but if you run it with no parameters it will list the options out for you:

```

ati-config

```

If you look at the output from that, it will give you some examples for initial setup (covering the most common scenarios). Once you've worked out which options suit you best, run:

```

sudo ati-config *your options*

```

Then press CTRL+ALT+Delete to restart X.

Make sure your TV is connected and switched on when you do all this, or your graphics card won't detect it and it won't work.

I'm afraid the ati tools are a bit flakey, so good luck.

---

### Post by Pirate King on 2008-02-23
everytime I enable Propietry drivers Ubuntu goes into Low Graphics mode. I'm not sure why or how to stop this. Is it normal?

---

