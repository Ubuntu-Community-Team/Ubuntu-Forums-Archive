---
title: "Why is Inkscape so slow?"
date: 2007-08-15
forum: Art &amp; Design
---

### Post by Jiawen on 2007-08-15
When I try to do almost anything moderately complex in Inkscape, it becomes as slow as frozen molasses on downers. I just had a document that consisted of three circles and fourteen lines, and when I tried to put a gradient on one of the circles, it took me five minutes just to get a screen redraw. This is ridiculous.

Is there something I can do to speed up Inkscape? Other than its painfully slow speed, I love it, so I don't want to switch to anything else (and XaraLX, its closest competition, has tons of other problems that I don't want to go into). 

Any help is appreciated.

---

### Post by Paul820 on 2007-08-15
Working perfectly fine here, no slowdown at all. How much ram have you got installed on your computer? If you have loads of ram then i don't know what the problem is.

---

### Post by shad0w_walker on 2007-08-15
System details are always helpful for this sort of thing. As far as I'm aware inkscape is is a vector drawing tool so that doesn't lend itself greatly to lower end hardware.

Also, has this just started doing this recently or has it always been? Run on a different distro and its run fine?

---

### Post by graigsmith on 2007-08-17
editing vectors with full graphic rendering is cpu intensive.  one thing you can do find ways to simplify the amount of information you are working with. instead of creating 100's of points on a circle and having slight curves between each one, have 1-2 points and use the points to create the proper curve.  it will cause it to render faster, and save files wont be as huge.  are you using any kind of tracing feature? usually those add far too many extra points.  if you draw all that by hand, it will be faster, and look way better too.

or get a faster processor.

---

### Post by mrgnash on 2007-08-19
I can confirm that this thing runs like a dog on my E6600, whereas XaraLX runs fine on that, and my little Turion ML-30. It's just bad coding on their part. The next revision is meant to be faster though.

---

### Post by Half-Left on 2007-08-19
> **mrgnash said:**
> I can confirm that this thing runs like a dog on my E6600, whereas XaraLX runs fine on that, and my little Turion ML-30. It's just bad coding on their part. The next revision is meant to be faster though.

Inkscape runs fine here, if you use blur with loads of objects it gets slow, but to say it's bad coding is total nonsense.

---

### Post by mrgnash on 2007-08-20
> **Half-Left said:**
> Inkscape runs fine here, if you use blur with loads of objects it gets slow, but to say it's bad coding is total nonsense.

Well it's certainly not up to Xara's standards -- you can have tonnes nodes, transparencies, etc. and it remains blazingly fast.

---

### Post by Jiawen on 2007-08-20
I'm using a 1.8GHz machine with 1 gig RAM. 

It's certainly quite slow with any kind of blurring, but it's also pretty slow even without. And, like mrgnash noted, it's nowhere near XaraLX in terms of speed. (As I mentioned, I don't feel like going into why I don't want to use XaraLX.)

---

### Post by Half-Left on 2007-08-20
> **mrgnash said:**
> Well it's certainly not up to Xara's standards -- you can have tonnes nodes, transparencies, etc. and it remains blazingly fast.

Xara is the fastest vectory app by a long shot(beats the hell out of illustrator as well), what do you expect and it's been developed way longer then inkscape and parts of it are still proprietary . Blur is a new feature in Inkscape, I should imagine it will get faster.

Please, before you compare proprietary applications that have been developed over many, many years, give a thought that opensource ones dont have half the man power or skills. Companies can afford to employ the best and Xara, Corel and Adobe do and have been around for decades developing applications like this.

---

### Post by mrgnash on 2007-08-20
> **Half-Left said:**
> Xara is the fastest vectory app by a long shot(beats the hell out of illustrator as well), what do you expect and it's been developed way longer then inkscape and parts of it are still proprietary . Blur is a new feature in Inkscape, I should imagine it will get faster.

Please, before you compare proprietary applications that have been developed over many, many years, give a thought that opensource ones dont have half the man power or skills. Companies can afford to employ the best and Xara, Corel and Adobe do and have been around for decades developing applications like this.

You're right. I should not have put it in those terms; I just find it frustrating that Inkscape seems to be on the verge of greatness, and yet, is almost unusable due to speed issues (at least for me). The frustration I feel in this regard is further compounded by the fact that the only viable alternative on my platform of choice, is XaraLX, the development of which, seems to have almost stalled.

---

### Post by Half-Left on 2007-08-20
If it's that slow for you just turn the Filters option lower so it renders faster. File>Inkscape Preferences>Filters

Also having compiz enabled does tend to slow inkscape's rendering speed down.

---

