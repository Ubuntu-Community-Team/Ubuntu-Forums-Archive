---
title: "Suggestion: Scroll bar visibility in Unity"
date: 2013-02-11
forum: Assistive Technology &amp; Accessibility
---

### Post by sunnybubblegum on 2013-02-11
I didn't know whether to voice this suggestion directly to Canonical, or whether this qualified under the Art & Design topic. But I thought I'd try here.

This is a suggestion that relates to accessibility -- chiefly visibility -- and Unity's main themes.

I am slightly visually impaired (keratoconus, an eye disease), in a way that makes bright things appear more blown out, blurry and hazy than they are (the 'bloom' effect).

 With Unity's Ambiance theme (the default), I often have difficulty distinguishing between a window's scroll bar, and the scroll background (the strip upon which the bar slides). Especially when the window's contents are overall very dark or very light, and the eyes have adjusted accordingly. (Shapes 'blend into' their more dominant surroundings.)

The thing is, I really enjoy the Ambiance theme (I use it), and Radiance is great too. They are beautiful. I don't find the High Contrast themes appealing, or even very helpful with regards to visibility.

Despite this condition, I'm able to see things largely as others do. It's not a drastic impairment; I 'get by' with the current setup.

I suppose my tentative desires are:
For Unity's main themes to have a slightly darker scroll bar background, or
to have either the option for this, or an additional theme altogether.

I wish not to reduce the current solution from elegant and unified to ugly and incohesive. It would just make using the desktop appreciably less laborious for me.

Thank you!

---

### Post by vasa1 on 2013-02-11
Please name the programs for which scrollbar visibility is an issue. I'm asking because Unity has one type of scrollbar, the overlay type; others, such as most, not all, browsers, use the older, conventional type.

If it is the former that is bothering you, there are, or were, ways to disable it so that you'd see only conventional scrollbars everywhere. In any case, it's not too difficult to increase "contrast" for **either** type by editing certain text files that form part of most themes. 

So, once again, do clarify and also mention which version of Ubuntu you're using: 12.04 or 12.10 or something else.

---

### Post by sunnybubblegum on 2013-02-12
It's definitely the older, conventional type of scroll bar you speak of that I have difficulty with. The newer one I actually like; it's very easy to see. Thanks for pointing out this distinction. I'm using Ubuntu 12.04.

Programs I use that employ the undesired scroll bar are Firefox (18.0.2), Gimp (2.8.4), the LibreOffice Suite (3.5.4.2), FileZilla (3.5.3), Synaptic Package Manager (0.79.5), Chromium (24.0.1312.56) and perhaps a few others. And who knows what future programs.

I just have a few questions.

Because you say that this type of scroll bar is 'older' yet more conventional, is this an indication that Canonical are slowly phasing out the use of it in favor of the new one?

Who chooses which scroll bar will be used where, Canonical or the program itself?

If the 'conventional' scroll bar will remain indefinitely, wouldn't there be legitimate philosophical grounds to propose a more visible default scroll bar to Canonical, given their commitment to the "ubuntu" ethos and accessibility? (i.e. instead of users having to use a workaround themselves by altering text files)

Thank you for your reply.

---

### Post by vasa1 on 2013-02-12
> **sunnybubblegum said:**
> It's definitely the older, conventional type of scroll bar you speak of that I have difficulty with. The newer one I actually like; it's very easy to see. Thanks for pointing out this distinction. I'm using Ubuntu 12.04.

Programs I use that employ the undesired scroll bar are Firefox (18.0.2), Gimp (2.8.4), the LibreOffice Suite (3.5.4.2), FileZilla (3.5.3), Synaptic Package Manager (0.79.5), Chromium (24.0.1312.56) and perhaps a few others. And who knows what future programs.
**My understanding** is that gtk3 apps will work with the new scrollbars which are being called "overlay scrollbars". gtk2 (and other non-gtk3) apps still use the older ones.
> **sunnybubblegum said:**
> ]I just have a few questions.
Here are some references dealing with overlay scrollbars:
[Ubuntu Unveils New Overlay Scrollbars for Natty]("http://www.omgubuntu.co.uk/2011/03/ubuntus-new-overlay-scrollbars-for-natty")
[Overlay Scrollbars – Update]("http://design.canonical.com/2011/07/overlay-scrollbars-update/")
[http://askubuntu.com/questions/192130/how-to-change-color-and-width-of-non-overlay-scrollbars-in-ubuntu-12-04]("http://askubuntu.com/a/192138/25656")
> **sunnybubblegum said:**
> Because you say that this type of scroll bar is 'older' yet more conventional, is this an indication that Canonical are slowly phasing out the use of it in favor of the new one?
I think Canonical's thinking can be gauged from the second link.
> **sunnybubblegum said:**
> Who chooses which scroll bar will be used where, Canonical or the program itself?
My understanding is that a gtk3 app will automatically use the overlay scrollbars if available.
> **sunnybubblegum said:**
> If the 'conventional' scroll bar will remain indefinitely, wouldn't there be legitimate philosophical grounds to propose a more visible default scroll bar to Canonical, given their commitment to the "ubuntu" ethos and accessibility? (i.e. instead of users having to use a workaround themselves by altering text files)
I have views on accessibility in general but they aren't fit for this forum.

---

### Post by sunnybubblegum on 2013-02-21
Thank you for your responses, vasa1. While it's not clear to me whether all applications will eventually make use of the newer scroll bar, it seems like it's a possibility.

---

