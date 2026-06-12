---
title: "Cube Background"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by AcademyKP03 on 2007-11-06
How do I put a background picture while using the cube function?

I have the cube effect working - and it's great ... but getting a picture put in the background is my problem ....

Any idea would be helpful

thanks

---

### Post by Phristen on 2007-11-06
Go to appearance tab, then scroll down, you will see a "skydome"section. Enable skydome and enter "skydome image" :)

It's funny, I almost had the same question, so I'll post it in this thread.
The skydome works fine with pictures up to 2048 px, but when I put large pictures like 4096 px wide, then the pictures don't show... Just the solid color background. Any ideas how to fix it?

---

### Post by AcademyKP03 on 2007-11-06
Yup; that did it

Although, here's a question - - bonus

I notice while looking at pictures of other people's cube effect ... that the windows while in cube effect - seem like they're jumping off the page .... ie like they have a spaces between each other, on each "face" of the cube .....

hmmm, not sure that was very clear ....

Here's a picture of what I mean:

[http://news.softpedia.com/images/reviews/large/beryl-img4-large.jpg](http://news.softpedia.com/images/reviews/large/beryl-img4-large.jpg)

Notice how one one face of the cube ..... that the windows aren't sitting within the face, they're like coming off the side -- 

Make sense?

I'm sure there is some setting to change it .... but hoping someone already knows how ....

---

### Post by jordanmthomas on 2007-11-06
That's the 3D windows plugin.

---

### Post by AcademyKP03 on 2007-11-06
How do I get that?

Is that within Compiz Config setting?

Thanks

---

### Post by jordanmthomas on 2007-11-06
I'm not sure of what packages Ubuntu splits compiz into, but do you have ccsm and any sort of compiz package labeled 'extra' installed?
(try running ccsm from a terminal or the Alt + F2 box)

It should be in there under extras.  If not, install the extra plugins and try again.

---

### Post by AcademyKP03 on 2007-11-06
> **jordanmthomas said:**
> I'm not sure of what packages Ubuntu splits compiz into, but do you have ccsm and any sort of compiz package labeled 'extra' installed?
(try running ccsm from a terminal or the Alt + F2 box)

It should be in there under extras.  If not, install the extra plugins and try again.




Yes, I have it installed, m only choices under Extras are:

1) Annotate
2) Benchmark
3) Screenshot
4)Splash
5) Windows preview

--

How do I install extra plugins?

---

### Post by jordanmthomas on 2007-11-06
```
sudo apt-get install compiz-fusion-plugins-extra
```
Or install it from synaptic, pick your poison.

---

### Post by jordanmthomas on 2007-11-06
Note I changed the post in case you've already read it.  Sorry about that.

---

### Post by AcademyKP03 on 2007-11-06
I already have that installed ...

What choice, under "extras" is the 3d Effects found?

---

### Post by jordanmthomas on 2007-11-06
3D Windows
(You have the extra plugins installed, not just the main?)
I screwed up the post and I think I edited it after you read it.

---

### Post by AcademyKP03 on 2007-11-06
I went to terminal - copy and pasted your last sudo and got this:

john@john-desktop:~$ sudo apt-get install compiz-fusion-plugins-extra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-fusion-plugins-extra is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
john@john-desktop:~$ 



So I think i have the most up to date ....

I go to System>Preferences>Advanced Desktop Effects and Settings> and Look under the "Extras" and I don't see 3D effects ....

am I doing something wrong?

---

### Post by jordanmthomas on 2007-11-06
No, you're not doing anything wrong.  It seems the Ubuntu compiz doesn't ship with the 3d plugin, so you'll need to find a 3rd party repository (like trevino's) or compile yourself. 
It's very strange, really....
Sorry about that (wasting your time there), in my distro it's in the unsupported-plugins, which Ubuntu doesn't have.

---

### Post by AcademyKP03 on 2007-11-06
No problem, thanks for trying .....

---

### Post by jordanmthomas on 2007-11-06
Man, I am dumb today..
For what it's worth, I was also wrong about where you find it.
It's in the Effects section of ccsm.  (you still don't have it installed I don't think)

---

### Post by ramjet_1953 on 2007-11-06
I have read elsewhere that the 3D plug-in was removed from this edition of Compiz Fusion, as it was buggy and causing problems.

I'm fairly sure that if you persist and search around for it, there will be an un-suppoted package somewhere.

Regards,
Roger :cool:

---

### Post by mc4man on 2007-11-07
3d windows
[http://ubuntuforums.org/showthread.php?t=585491](http://ubuntuforums.org/showthread.php?t=585491)

---

### Post by Phristen on 2007-11-07
So does anyone know, why is the skydome background only working with pictures up to 2048 pixels in width?

---

### Post by jordanmthomas on 2007-11-07
It's a limit of your graphics card.  Odds are, it can only handle textures up to 2048x2048.

---

