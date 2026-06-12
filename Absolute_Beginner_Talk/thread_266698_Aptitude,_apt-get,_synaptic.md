---
title: "Aptitude, apt-get, synaptic"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by ReaderRat on 2006-09-27
I am trying to sort out how these relate to one another. I believe that aptitude is a frontend for apt-get, and synaptic is a GUI for aptitude. Is this correct?

Two questions: After I run *apt-get update* , do I need to install all the security updates then? How do I do that?

---

### Post by xpod on 2006-09-27
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

?

---

### Post by ReaderRat on 2006-09-27
Thank you for the link. It's got some good reading (now that I know where to go).
I still don't know what to do about the updates.

---

### Post by aysiu on 2006-09-27
*update* just sees what's out there available to install.

*upgrade* upgrades your existing packages

*dist-upgrade* makes changes that Ubuntu decides are for the best (usually this involves upgrading your existing packages, but they may remove certain packages and add certain ones, too). You have to have the appropriate *-desktop* metapackage installed for this to work properly. For example, if you have Gnome, you would need *ubuntu-desktop* installed.

---

### Post by xpod on 2006-09-27
Sorry it was but a link i gave but i had an angry baby who took over my attention..
And besides.....aysiu`s sites are probably some of the most easy to follow i
know of.Of course i dont know much myself but i asked the same questions two months ago and those were where i started.....and still am of course:D

---

### Post by bodhi.zazen on 2006-09-27
apt-get vs aptitude is getting out of hand. Almost as bad as gnome vs KDE or Microsoft vs Linux..... 8-[

synaptic is a gui (front-end) for apt-get (backend).

both have advantages, I advise aptitude (from the CLI) because:

[[color=blue]Aptitude[/color]](http://ubuntuforums.org/showthread.php?t=37736)

:-\"

---

### Post by aysiu on 2006-09-27
Is it really getting out of hand? There's an obscure thing to do with building dependencies that *apt-get* can do and *aptitude* can't, and every now and then *aptitude* thinks it's smarter than it really is and "holds back" packages you don't want held back.

Other than that, there's not much *apt-get* has over *aptitude*, and there's a lot *aptitude* has over *apt-get*, especially when it comes to uninstalling programs.

---

### Post by xpod on 2006-09-27
Your to late ma pal as me thinks the big mans sites would have done the job..

Funnily enough though i got that one bookmarked as well:D 
Never too late anyway;)

---

### Post by bodhi.zazen on 2006-09-27
> **aysiu said:**
> Is it really getting out of hand? There's an obscure thing to do with building dependencies that *apt-get* can do and *aptitude* can't, and every now and then *aptitude* thinks it's smarter than it really is and "holds back" packages you don't want held back.

Other than that, there's not much *apt-get* has over *aptitude*, and there's a lot *aptitude* has over *apt-get*, especially when it comes to uninstalling programs.

Thanks Aysiu. Perhaps I was not as clear as I should have been. Unlike your post, it seems to me some posts on this issue are taking a more hostile turn in promoting apt-get or aptitude rather then providing useful information.

If you see them perhaps you can continue to inject the voice of reason.

---

### Post by snakyjake on 2006-09-29
> **bodhi.zazen said:**
> Thanks Aysiu. Perhaps I was not as clear as I should have been. Unlike your post, it seems to me some posts on this issue are taking a more hostile turn in promoting apt-get or aptitude rather then providing useful information.

If you see them perhaps you can continue to inject the voice of reason.

I agree, and I have to admit the Linux community has contributed to this.  I'm a big proponent of wikis so our Linux community can have something official and comprehensive.  And I'm noticing the Ubuntu wiki specifically talks about apt-get.  Also noticing that the community has help wikis strung out in too many places.

Here's a good example:
[https://help.ubuntu.com/ubuntu/desktopguide/C/apt-get.html](https://help.ubuntu.com/ubuntu/desktopguide/C/apt-get.html)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[https://wiki.ubuntu.com/AdeptHowto](https://wiki.ubuntu.com/AdeptHowto)

I don't want to take this thread off topic, but I'm going to post these concerns to another thread (PM if you feel like chatting about it).

---

