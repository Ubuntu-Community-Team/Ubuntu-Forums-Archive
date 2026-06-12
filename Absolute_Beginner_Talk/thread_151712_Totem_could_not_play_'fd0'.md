---
title: "Totem could not play 'fd://0'"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by jlhughes on 2006-03-28
I'm attempting to configure a new installation to play XM Radio's web feed.

When I launched the player the first time, the web page reported that Macromedia Flash was needed.  I also received a system error message "Totem could not play 'fd://0'. There were no decoders found to handle the stream, you might need to install the corresponding plugins."

I installed the "free" multiverse Flash player. I rebooted the computer.

I no longer get the warning that I need Macromedia Flash player, but I am STILL getting the Totem error message.

---

### Post by Pragmatist on 2006-03-28
Isn't XM Radio a commercial service?  Do they support Linux?

---

### Post by taurus on 2006-03-28
Perhaps you need totem-xine!!!
```

sudo apt-get install totem-xine

```

---

### Post by jlhughes on 2006-03-29
[QUOTE=Pragmatist]Isn't XM Radio a commercial service?  Do they support Linux?[/QUOTE]

Yes, XM Radio is a subscription satellite radio service. However, when you buy a subscription (for instance, for a car satellite radio), you also get to use their web service for no extra fee. (listen.xmradio.com)

To make a long story shorter, I was able to get the Web feed to work by  removing and reinstalling ALL of the Totem packages. I have no idea which specific package was needed, but it works and I'm happy. (Stupid newbie luck on my part :mrgreen: )

---

