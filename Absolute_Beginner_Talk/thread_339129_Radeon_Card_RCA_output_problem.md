---
title: "Radeon Card RCA output problem"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by tordan on 2007-01-15
I have a ATI Radeon video card with a RCA/S-video converter. I have watched movies and video from my computer on my television w/ windows for a while. Windows automatically sensed the video card and enabled the RCA/S-video outputs.
How do I set up Ubuntu Edgy Eft to work with the video card's extra outputs?

I know Ubuntu knows the card exists because I am using the VGA output on it for the monitor and it works fine.

---

### Post by crispy_420 on 2007-01-15
You'll need to configure your xorg.conf for ATI TV-out. Just look around the forums. But your first goal would be to setup fglrx drivers for best performance.

Look [HERE]("http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/").

Cool program for gui configuration of ati cards. It is called fglrxkonf.

---

### Post by tordan on 2007-01-16
Thanks for the reply.

I don't even know what I'm looking at on that page.
What am I looking for?
What is this package going to accomplish?

---

### Post by crispy_420 on 2007-01-18
look at fglrxkonf

You can even add this source as a repo for apt or just install from download. It will setup ATI video to meet your needs.

---

### Post by tordan on 2007-01-19
Thanks!
I got the program downloaded. (I don't know why I couldn't figure out what to do after the first message)(420)

Now, would you mind helping me with the next step. I tried to access Kommander's help program, but it was inaccessible. Whats next? What is the overall function of this program?

---

